---
title: "Skydome/cube issue in Compiz Fusion"
date: 2008-07-05
forum: General Help
---

### Post by cptasker on 2008-07-05
Hi everyone,

I've had Ubuntu for just a few days and I'm still finding my way about so forgive me if I don't give the correct information..

I recently installed compiz fusion, the issues I am having trouble with are:

Skydome displays gradient (blue and white) but if I load an image it comes up plain white or black and shows no image. I've tried jpg and png I have also tried scaling images to a square. Any ideas what could be up?

My cube is only 4 sides with no top or bottom. I am aware you have to set your desktop to 4 in the initial basic settings but no matter what I set any of it to I can't get a 3d cube. I have reset everything to default and tried again but no joy. 

Any suggestions would be welcome, thanks in advance!

Claire xx

---

### Post by sayakb on 2008-07-05
1. Check the largest image size supported by your card (i dont exactly remember the command for that). Scale the skydome image down and try again.
2. Have you enabled cube caps?

---

### Post by cptasker on 2008-07-06
Hi, Thanks for your quick answer! 

1. No luck, just the same problem I'm afraid!

2. Cube caps is on, I think I've followed every single tutorial on these forums and still the same problem! :-s

Is it time to re-install?

Thanks!

Claire xx

---

### Post by sayakb on 2008-07-06
1. Im sure its the size. Scale it down to 1024x768 size. 
2. Have you set any cube cap images?

Also, if nothing works, in ccsm, press **Preferences** and Click **Reset to Defaults** button. Then again enable **Desktop Cube**, **Rotate Cube**, **Cube Caps** and **Cube Reflection** (If you need this, ie.)

Try upgrading to Compiz 0.7.6 otherwise. In System->Administration->Software Sources->Third Party Softwares, add this repo:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

And reload the database. You will be notified of Compiz update. Do the update and reboot. See if cube/distorted cube plugins work.

---

### Post by thetechguyz on 2009-02-25
[http://www.artpoker.net/WallpapersImages/1024x768_PartyPoker03.jpg](http://www.artpoker.net/WallpapersImages/1024x768_PartyPoker03.jpg)

I used this image to test the Cube Cap but it cuts off her mouth up and her half of her lower arm on the left side of the image. The left side just as bad... This image is in 1024x768. All things are on and selected.

The scale down image for cub cap and bottom do no function properly. I tried this with 3D Cube and Deformation. I have also tried a range of various resolutions but still nothing works. Compiz Version 0.7.8

I'm about to try resetting to defaults. I fear this will not fix the cause though...

---

