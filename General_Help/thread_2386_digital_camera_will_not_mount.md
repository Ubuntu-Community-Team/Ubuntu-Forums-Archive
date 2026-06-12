---
title: "digital camera will not mount"
date: 2004-10-27
forum: General Help
---

### Post by RayG on 2004-10-27
When I installed Ubuntu release candidate. I could use gThumb to access photos stored on it. I could go to File:Import Photos:, click on the camera icon, choose Detect, and the program would detect my camera.  

I have since used apt-get upgrade to update the system using the final release iso. 

Problem: Now when trying to access my camera through gThumb, an error message in the Import Photos: dialog box indicates that the camera is not detected. Even setting the camera type manually does not work. 

The camera is a Kodak CX4200, a PTP type camera, so I cannot just mount it as a file system and access that way. My system is an AMD Duron CPU on a VIA KT266A-based  motherboard. 

Any help is appreciated.
RayG

---

### Post by gregh on 2004-11-24
I have the same problem using a Canon A40. When I plug it in I get the message about importing photos, but when I click yes the resulting gphoto applet cannot detect the camera (even if I set it manually)
This only happened after I did the Hoary upgrade :-)

---

### Post by arctic on 2004-11-24
are you able to access the files through nautilus? or are you having problems there, too?

---

### Post by RayG on 2004-11-24
This particular Kodak camera is not a normal USB device, though it attaches to the USB port. Images are not directly accessible using a file manager. You have to use something like gphoto2 to move stored images to disk.

---

### Post by oooh on 2008-02-28
hallo

I am using canon rebel xt, or 350d

i could download pics using the gthumb nicelly, but dont know how ... now i can not, in fact it takes ages to DL all the previews, and when it comes to dl the complete files:

i download the pics, but they are empty files in my hd !!

i tried to store them in another harddrive, but nothing 

i reinstalled the gphoto2 and nothing

i am currentlz trying to mount the camera using gphotofs, but did not manage still ...

any recommendatio ??

---

