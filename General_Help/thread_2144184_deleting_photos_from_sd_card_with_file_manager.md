---
title: "deleting photos from sd card with file manager"
date: 2013-05-11
forum: General Help
---

### Post by Buntu Bunny on 2013-05-11
Awhile back I tried to delete some jpg photos from the camera's memory card while the camera (Panasonic DMC-ZS6) was mounted to the computer. It deleted them, but for some reason made that part of the card inaccessible. I eventually had to reformat the card in Gparted. The card was usable, but I always got an error message from the camera. I still took my shots and transferred them to my computer, but had to delete from the camera itself.

I have a different camera now (Kodak Easyshare m583) and I'm using a card reader to copy my photos to my photo folder. It would be so much easier to simply delete them from the card in file manager when the card is mounted. ***But***, I've already had problems with this camera and am hesitant. Can anyone give me any tips or warnings about doing this?

---

### Post by 2F4U on 2013-05-11
Are you sure that the card is not the source of the problem? Did you try a different card? What else I could think of is that the camera uses its own filesystem format, which Ubuntu can't handle. If this is the case and you have ongoing problems, one way to deal with the issue would be to copy the files from the card as usual, but then either delete the files from within the camera or format the card from the camera. This would hopefully make sure the filesystem on the card won't get corrupted.

---

### Post by ranger1021994 on 2013-05-11
You connected camera in MTP mode or Storage mode ?

---

### Post by Buntu Bunny on 2013-05-11
> **2F4U said:**
> Are you sure that the card is not the source of the problem? Did you try a different card? What else I could think of is that the camera uses its own filesystem format, which Ubuntu can't handle. If this is the case and you have ongoing problems, one way to deal with the issue would be to copy the files from the card as usual, but then either delete the files from within the camera or format the card from the camera. This would hopefully make sure the filesystem on the card won't get corrupted.

2F4U, thank you for such a quick response! I'm not sure of the source of the problem either way. I wasn't have any problems with the files being read by Shotwell, nor copied. I only had a problem when I deleted the images from file manager. The card doesn't really need formatting, it was a necessity under the circumstances. I certainly can continue as I'm doing now. 

> **ranger1021994 said:**
> You connected camera in MTP mode or Storage mode ?

Ranger1021994, I cannot seem to find this information in the camera settings. The only modes offered are capture modes and safety modes. :confused:

---

### Post by ranger1021994 on 2013-05-11
You get those options when you connect camera to pc?

---

### Post by Buntu Bunny on 2013-05-11
> **ranger1021994 said:**
> You get those options when you connect camera to pc?

Those are the options from the camera menus. I don't seem to get any options when I connect the camera to the pc, but then I have problems with this camera mounting (all of that in this thread, "[Camera Mounting Twice?]("http://ubuntuforums.org/showthread.php?t=2140600")"). That doesn't help, does it?

---

