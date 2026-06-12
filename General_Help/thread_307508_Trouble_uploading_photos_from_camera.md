---
title: "Trouble uploading photos from camera"
date: 2006-11-26
forum: General Help
---

### Post by ethaniscool on 2006-11-26
I am having trouble getting photos from my camera to my computer(edgy eft). Every time I try I get this message, 

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

Does anyone have a suggestion as to what I should do?

---

### Post by bettlebrox on 2006-11-26
Some questions:
What type of camera (make & model number)?

What are you using to try and get the pics off the camera? (F-spot, digikam, gtkam ...)

Does it work if you do it as root (or using sudo)?

---

### Post by ethaniscool on 2006-11-27
Ok

Camera = Kodak EasyShare Z650
I am using Fspot for the photos and I do not know what you mean by "do it as root or sudo." What is the command in terminal?

---

### Post by bettlebrox on 2006-11-27
>What is the command in terminal?
sudo f-spot

Might be easier to start with a simplier tool such as gtkam.

Do you need to turn the camera on when you connect it?

After connecting the camera do you see anything in the logs? Look at the outout from dmesg from the command line, probably just need to look at the last few lines.

---

### Post by xopher on 2006-11-27
Make sure your login is in the 'camera' group too.

---

### Post by ethaniscool on 2006-11-27
thanks gtkam and gphoto work great

---

### Post by bettlebrox on 2006-11-28
> **ethaniscool said:**
> thanks gtkam and gphoto work great
As a regular user? Is so there must be a bug in f-spot or some package is missing. U could try purging f-spot and then reinstalling to see if any missing packages get picked up? Or digikam is a pretty neat photo organiser and can access the camera too.

---

### Post by Max Roswell on 2006-12-10
> **xopher said:**
> Make sure your login is in the 'camera' group too.

I'm having the same problem with the same camera.  How do I add my login to the camera group, por favor?

EDIT:  Okay, I've tried f-spot, gtkam, g-thumb, gphoto, and they all give me the same error message:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

Invoking f-spot, gthumb or gphoto as sudo doesn't do anything, but sudo DOES make gtkam and digikam work, though all imported photos belong to root, natch. So it seems like somehow I need to let Ubuntu know that my regular user ID should have permission to access this camera.  I don't know how to do that.

Any ideas?  Most of the time, I can use my SD card and my SD card reader, but it would be convenient to be able to plug in my camera, you know?

SECOND EDIT:  I found the fix for this problem [here.]("http://www.ubuntuforums.org/showthread.php?t=290205")

---

