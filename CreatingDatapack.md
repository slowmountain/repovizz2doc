(WIP)
# Creating a datapack

Multimodal data recordings in repovizz2 are represented as *datapacks*, a collection of the data files to-be-uploaded accompanied by a hierarchical structure that describes them.

Each datapack consists of the following:

* a datapack JSON document that adheres to the [repovizz2 datapack JSON schema](#datapack_schema)
* a list of files to be uploaded

In order to upload a repovizz datapack, the user needs to provide all of the above and follow the guide in [Uploading a datapack](https://github.com/chaosct/repovizz2doc/blob/master/Upload.ipynb).

In the rest of this guide, we will walk through the process of creating a datapack JSON document, and preparing the files to be uploaded.

## Creating the datapack JSON

We'll use an example datapack that includes the datapack JSON document along with a list of data files.

### Example datapack

This example datapack contains a multimodal recording carried out using [Thalmic Labs' MYO](https://www.myo.com/), accompanied by audio and video from a handheld video camera. The following data files are present inside the datapack:

<center>

Filename | Description
---------|------------
video.mp4 | video recording from a handheld camera
audio.wav | audio recording from the camera's microphone
emg.json | 8-channel muscle activity (EMG) data 
accelerometer.json | 3-axis accelerometer data
gyroscope.json | 3-axis gyroscope data 
orientation.json | 3-axis orientation data

</center>

The video and audio files are in standard H.264 MP4 and wave format, while the sensor data are stored inside json arrays. We'll talk more about the file formats that repovizz2 uses in a little bit; for the time being let's take a look at the datapack JSON document:

	{
	    "info": {
	        "keywords": [
	            "MYO", "audio", "video", "accelerometer", "gyroscope"
	        ],
	        "description": "Short datapack of MYO data coupled with video and audio.",
	        "name": "MYO_various",
	        "author": "panpap"
	    },
	    "children": [{
	        "class": "data",
	        "type": "e44ab9c4-a1b5-4474-b806-ece64555ef2b",
	        "name": "Video",
	        "text": "Handheld camera",
	        "link": "video.mp4",
	        "meta": {
	            "mime": "video/mp4; charset=binary"
	        }
	    }, {
	        "class": "data",
	        "type": "48e3b5d2-c34c-459c-9a2d-0756c20d80de",
	        "name": "Audio",
	        "text": "Camera microphone",
	        "link": "audio.wav",
	        "meta": {
	            "mime": "audio/x-wav; charset=binary"
	        }
	    }, {
	        "class": "container",
	        "name": "EMG",
	        "text": "",
	        "children": [{
	            "class": "data",
	            "type": "0746bb48-9b92-4cd3-8d9e-3e1de13269eb",
	            "name": "EMG",
	            "text": "8-channel EMG data from the MYO armband",
	            "link": "emg.csv"
	        }]
	    }, {
	        "class": "container",
	        "name": "IMU",
	        "text": "Inertial Measurement Unit (IMU) data from the MYO armband",
	        "children": [{
	            "class": "data",
	            "type": "ae13fb70-fa1e-47d8-9cd6-00cef4fe21cc",
	            "name": "Accelerometer",
	            "text": "3-dimensional (XYZ) acceleration data",
	            "link": "accelerometer.csv"
	        }, {
	            "class": "data",
	            "type": "35524338-dec5-40ca-a099-1fff42fb5460",
	            "name": "Gyroscope",
	            "text": "3-dimensional (XYZ) gyroscope data",
	            "link": "gyroscope.csv"
	        }, {
	            "class": "data",
	            "type": "d4445fc6-0af0-42e0-979e-74a62b70b2ed",
	            "name": "Orientation",
	            "text": "3-dimensional (yaw, pitch, roll) orientation calculated from quaternion data",
	            "link": "orientation.csv"
	        }]
	    }]
	}

As you can see, the document contains two top-level objects:

* An *"info"* object which holds metadata about the datapack (name, author, description, keywords)
* A *"children"* object which holds an array with a hierarchical structure for the contents of the datapack.

Within the *children* array, datapack contents are hierarchically organized using two types of nodes: **data** nodes that hold pointers to data files, and **container** nodes that contain other nodes. This way, the user can construct a tree-like structure the leaves of which point to the data included into the datapack.

The structure from the example datapack can be seen below:
<center><img src="https://dl.dropboxusercontent.com/u/8191579/repovizz2_example_datapack_graph.png" width="300"></center>

### Container nodes
asdasd

### Data nodes
asdasd

### <a name="datapack_schema"></a> The datapack schema

<script src="http://lbovet.github.io/docson/widget.js" data-schema="https://raw.githubusercontent.com/slowmountain/repovizz2doc/master/datapack_schema.json"></script>

If the above doesn't work, check the datapack schema [here](http://lbovet.github.io/docson/index.html#https://raw.githubusercontent.com/slowmountain/repovizz2doc/master/datapack_schema.json)

TODO: Document the schema by adding descriptions for every item

TODO: Fix the datapack schema so that docson renders it correctly

### <a name="datatype_schema"></a>The datatype schema

<script src="http://lbovet.github.io/docson/widget.js" data-schema="https://raw.githubusercontent.com/slowmountain/repovizz2doc/master/datatype_schema.json"></script>

If the above doesn't work, check the datapack schema [here](http://lbovet.github.io/docson/index.html#https://raw.githubusercontent.com/slowmountain/repovizz2doc/master/datatype_schema.json)

