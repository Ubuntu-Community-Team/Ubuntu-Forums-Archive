---
title: "Mate 16.04 - right click open command prompt terminal ..."
date: 2016-04-23
forum: General Help
---

### Post by cwmoser on 2016-04-23
Just installed Ubuntu Mate 16.04.  
Two features I had setup in 15.10 was that I could:
- right click in a folder and select the command prompt terminal
- right click on a graphic image and select Resize

I can't get these configured in 16.04.  My notes are that the right click to open terminal
was built into 15.10, and for resize I issued:  **sudo apt-get install nautilus-image-converter**
but that now does not work.

Any help is appreciated.


Carl

---

### Post by Dennis N on 2016-04-24
I just installed Ubuntu MATE 16.04 as well, and the right-click "open in terminal" feature is still present. See the screenshot attached. You may have done something wrong. I clicked on the white space and the currently open folder is opened in the terminal. Also, if I click on a folder icon in that window, and choose "open in terminal", that folder is opened.  

I've never used the image resize plugin, but since it is for nautilus and not caja, it could be it just no longer works.

---

### Post by cwmoser on 2016-04-24
duplicate

---

### Post by cwmoser on 2016-04-24
Thanks Dennis.  My problem was that I was coming from 14.04 to 15.10 and now 16.04.
I was using Nautilus as my File Browser.  In the Mate community forum it was made clear
to me that I should be using caja.  Now I have my custom folder icons changed from using
nautilus to caja and I can now right click and select Terminal.

Also learned that there is a caja-image-resize too:
sudo apt-get install caja-image-resize
Need to log out and back in for it to be enabled as a right click feature.

---

### Post by wagb278 on 2016-04-24
I also have problems with image resize via Caja in Ubuntu-MATE 16.04.  I installed the caja-image-converter package via Ubuntu Software Center and any attempt to resize an image file results in the Error message "filename cannot be resized. Check whether you have permission to write to this folder"  I tested resizing an image using Fotoxx application and it works just fine and saved the resized image file in the same folder.  File and folder permissions are correct.

I am running software versions: 

Caja 1.12.7
caja-image-converter 1.12.0-1
MATE 1.12.1

I suspect a bug or configuration problem with the caja-image-converter software.  I could not find any configuration settings that might cause this.

Any ideas on how to get this working?

---

