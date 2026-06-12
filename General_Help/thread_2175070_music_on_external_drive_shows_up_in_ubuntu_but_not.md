---
title: "music on external drive shows up in ubuntu but not in windows"
date: 2013-09-17
forum: General Help
---

### Post by pancakefacecake on 2013-09-17
Hi, been using an WD 500GB to keep my music for a while now. the problem is much of the music I put onto the external HDD doesnt show up on windows [on the explorer or any music players] even though i can clearly see the music on ubuntu. 

Is this a problem others have been having. any tips? i tried showing hidden folders but didnt help.

thanks

---

### Post by oldos2er on 2013-09-17
What file system is on the WD drive?

---

### Post by CeejRab on 2013-09-17
Hello Pancakefacecake,

If you formatted your WD HD on a linux system, it may have formatted as and EXT filesystem and claimed the rights to it, thus your files may be encrypted and hidden to other operating systems. 

To see what file system is as oldos2er asked above, open disk utility and click on your external drive (assuming you have it plugged into your machine of course). Tell us what it says the filesystem format is, please.

When viewing this drive in windows, when you right click on the device and select "properties", does it show that any of the storage is used? If so, then your files are there but hidden. If thats the case, open the device and in the menu bar (under edit or view tab i believe) click folder options. Scroll through and find "show hidden files and folders" and click the radio button to select it. This will unhide hidden folders and you will be able to see if they are there.

Let us know what you find :)

all the best

---

