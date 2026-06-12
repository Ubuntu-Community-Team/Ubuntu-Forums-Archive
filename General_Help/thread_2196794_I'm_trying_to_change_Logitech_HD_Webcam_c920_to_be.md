---
title: "I'm trying to change Logitech HD Webcam c920 to be my default camera"
date: 2013-12-31
forum: General Help
---

### Post by Mike1977 on 2013-12-31
I'm running Ubuntu 12.04 on Toshiba L755, with Windows 7 as well. 
memory: 3.8 Gib
  processor: Intel® Core™ i5-2410M CPU @ 2.30GHz × 4 
  graphics: Intel® Sandybridge Mobile  
  OS-type 64bit
  disk: 40.2 GB
I have set up a Logitech c920 HD webcam. I'm using GUVCview as well as  V4L. In GUVC , I open up application and it automatically opens up my  laptop's built in camera. I can change the input to HD webcam c920, but I  would like to have HD webcam c920 to be always be default.I have both Gstreamer and Multimedia plug ins iinstalled.  I have gone  into Mutlimedia systems selector with      
     ```
sudo gstreamer-properties 
```
 and changed the default input to HD webcam, yet when I open up G+  Hangouts, or even GUVC view, it still opens up as laptop camera. I've  tried re-running command in terminal and changing default, but it won't  save. When I start up a video chat on G+ it opens laptop camera. IN  Multimedia systems selector, I select external cam as default, and I  press "test". The external web camera lights up (blue light) but I get  no picture. However, it works great in GUVC view. So it's connected, but  how to make it default?
Plug-in: Video for Linux2 (V4L2)
Device: HD pro webcam c920

---

