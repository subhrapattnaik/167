# 167

image tracking augmented reality web apps.
-----------------------------------------

we can scan any image and render content over that.

we can also pick any drawing or any picture and use it to show the content over that.

similar to the markers where we were showing the content over the marker.
In this we will be learning how to tell the computer to identify the image
-------------------------------------------

We will be learning how to use an image as an image tracker and play the 3D video content over that image.

-------------------------------------
For 3D video content to be compatible with both Android and iOS devices, we need to add the meta information to enable Apple mobile content.


We can add <div> in the <body> to show the loading descriptor till the time video content is loaded.

  
  Let's add some CSS styling also for the loading descriptor in the <head>
  
 We can now add the basic A-Frame scene and add components to enable arjs and disable vr-mode-ui.
We can also set the renderer component and its property logarithmicDepthBuffer as true to enhance the rendering of the 3D entities in the scene.
In simple terms, a logarithmic depth buffer provides more accuracy for objects near the camera.
  
  <a-scene
  vr-mode-ui=”enabled: false;”
  renderer=”logarithmicDepthBuffer: true;”
  embedded
arjs=”tackingMethod: best; sourceType: webcam; debugUIEnable: false;”>
    
    </a-scene>
  
  -----------------------------------------
  
   to make an image tracking application the first thing that we need is an image.
You should try to pick a good quality image to have better tracking.
This image will be used as the image tracker.
To convert this image into a tracker, we will be using an NFT converter.
  
  https://carnaux.github.io/NFT-Marker-Creator/#/
  
  NFT stands for natural feature tracking. This is a technology which helps to create image trackers.
  
  we can upload the image and generate the NFT marker.
  3 files gets downloaded.
  NFT marker creator will create 3 files with .fset, .fset3 and .iset extension to be used as marker descriptor information.
Allow the permission to download multiple files.
  
  
  Copy and paste these 3 files into the working directory.
  
  
  
Note: Do not use images having very high pixel height and width value to generate the nft marker files.
Resize the image to reduce the time required to generate the nft marker files.
  -----------------------------------
  
  Now we are going to use the video asset to be over the image.
 we will be using <video> to add the video src files and set other properties to play the video.

  For <video> we can set:
● src: the file path to video;
● preload: whether to preload the video content before rendering the scene;
  loop: whether to play the video again and again;
● playsinline and webkit-playsinline: to play the video right where it is and avoid video to play in full screen mode; and
● crossorigin: sets the Cross-Origin Resource Sharing permission to share the information on the web browser. The crossorigin attribute is valid on the <audio>, <img>, <link>, <script>, and <video> elements.
  
  --------------------------------------
  
  Now we will play the video with the nft marker information.
For this we will need the aframe-ar-nft.js library.
  
  
https://raw.githack.com/AR-js-org/AR.js/ master/aframe/build/aframe-ar-nft.js
Then we will use the <a-nft> tag to add the nft marker files.

  For <a-nft> we can set:
● type: nft
● url: file path to nft image descriptor created before.
Note: While adding the nft file descriptor in the src path, the filename (excluding extension) is used only once for all 3 files.

  
  Images are stored as a set of pixel values in the form of rows and columns. This is known as the image matrix.
We can have multiple matrices for better tracking of images.
While using <a-nft> we can also set the tracking properties.

  
  In <a-nft> we can set:
smooth: turns on/off camera smoothing, default: false
  smoothCount:number of matrices for smooth tracking, default: 5
smoothTolerance: distance tolerance for smoothing, if smoothThreshold number of matrices are less than tolerance, tracking will stay still, default: 0.01
smoothThreshold: threshold for smoothing, will keep still unless enough matrices are more than tolerance, default: 2
Now to set the video entity, we will use <a-video> as the child of the <a-nft> and set the src id, height, width, position and rotation to set its orientation.
  
  -------------------------------
  Now let’s add one A-Frame component, “play-on-click”, which can help to play and pause the video on click.
In the schema of the component we can take isPlaying boolean variable with default value as false, as the data for the component.

  
  adds the src file in index.html.
  register “play-on-click” components and adds the schema & .init(), play() and onClick() functions
  ------------------------------------
  we can take the videoEl variable and select the video src to be played using onClick() and .init() methods.
In onClick() function:
● Select the isPlaying attribute.
● Use if/else condition to check the value of the isPlaying variable.
● Set the isPlaying value inside if/else condition and use .play() method to play the video src.
Then call the onClick() function inside .init() method and attach the component to the <a-video> entity.
  ---------------------------------------------------------------
  
  can now test the output using ngrok. To see the output:
● Use ngrok to run the application.
● Open HTTPS URL in your smartphone/laptop and give permission to use the camera.
● Open the original image that was used to create the nft image marker and point the camera towards it.
The window screen can be clicked or the phone screen can be tapped to play and pause the video.
  -------------------------------------
  
Output Reference
Note 1: The output video can be played and paused multiple times on touch.
Note 2: Switch on rotation mode and use the phone in the landscape mode to better cover the video content.
  
  
  

  
  
