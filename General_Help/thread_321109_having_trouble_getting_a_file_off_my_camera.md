---
title: "having trouble getting a file off my camera"
date: 2006-12-18
forum: General Help
---

### Post by TeeAhr1 on 2006-12-18
I have three avi files stored on my camera's memory card.  When I plug it in I get the usual camera dialog, the first two files copy fine, but it hangs on the third one and will not respond to anything I do, and I have to force quit.  I can view and edit this file fine on my camera, so I think the avi is uncorrupted.  How would I go about manually transferring files off the camera?

---

### Post by bodhi.zazen on 2006-12-18
If you plug in your camera does it auto mount ? Where ? I presume in /media.

Open a terminal```
cp /media/camera/file_to_copy /home/user_name/pictures_or_other_location
```

---

### Post by iamhugeinjapan on 2006-12-18
Does your camera show up as a usb device on the desktop? 

Are you using nautilus to copy the files off or is the usual camera dialog a photo importing program?

---

### Post by TeeAhr1 on 2006-12-18
It must mount somewhere, because when I plug it in it gives me the "a camera has been detected" box, but I sure can't find it in media, and it doesn't appear on my desktop (I had that option turned off in gconf, but I enabled it just now to check).  If I could figure out where it's mounting to, I'd be in business here...

---

### Post by TeeAhr1 on 2006-12-18
PS: It's not in /mnt either, nor does it show in the Nautilus sidebar.

---

### Post by hanzomon4 on 2006-12-18
Try going to it in nautilus and then click the arrow to go up one folder

---

### Post by bodhi.zazen on 2006-12-18
If you do not know the location of your camera, plug it in, open a terminal and type:```
sudo fdisk -l
```

---

### Post by fragos on 2006-12-18
When you plug your camera in the popup also allows you to ignore which then mounts the camera storage directly as if in a card reader.  An icon for it will pop up on the Desktop.  Click the icon and Nautilus will let you drag and drop any file either way.

---

### Post by TeeAhr1 on 2006-12-20
You guys are great.  Thanks to all who chimed in.

---

