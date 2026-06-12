---
title: "Backing up files from Windows through Ubuntu - HDD disappears?"
date: 2019-05-14
forum: General Help
---

### Post by werewolfrising on 2019-05-14
I am new to this so please bear with me. To preface, my old desktop computer isn't loading Windows (Vista, yes it's old) properly. The computer starts up fine and Windows starts. Once anything is clicked, whether it be a file, program or even the start menu, Windows freezes (almost like it's loading something) and a couple minutes later, it shuts down with the blue screen. It will not boot in safe mode, I have tried recovery, etc. Nothing seems to work.


I want to transfer my photos, music, text files, etc. to an external hard drive. I don't care about the "Windows" files that are there, if that makes sense. After transferring the files I want, I am okay with wiping the system.


So I decided to use Ubuntu to recover my files. I have a separate new laptop that I was able to download Ubuntu on, put it on a USB and boot my old computer from that (Escape to boot menu, select USB). Ubuntu opens/works fine on it. Everything on the desktop looks and works as it should without freezing.


I open "FILES" and my internal Hard Drive (HP - /dev/sda1) is there as shown:
[IMG]https://i.imgur.com/g5XBOAf.jpg[/IMG]


When opening that, my files are all still there. They don't seem to be corrupt since I am able to open and view them through Ubuntu.


The problem is that after 60 seconds or so, the internal Hard Drive (HP) disappears and I can't seem to access (or find) it anymore:
[IMG]https://i.imgur.com/7WA3cNz.jpg[/IMG]


All I want to do is plug in my External Hard Drive and transfer my files to that. Is there a way to prevent it from disappearing? Note: I am able to successfully transfer very small files like a text document before it disappears so I know the files themselves are okay.


I know little to nothing about this stuff so any help would be appreciated.


I am using Ubuntu 18.04.2 - If there is any more information I could provide, I will.


Thank you!!

---

### Post by HermanAB on 2019-05-14
It sounds like you have a HDD problem on the old machine.

You may be able to repair it by buying a 2nd hand disk drive of the exact same model on Ebay and then swapping the controller cards.

---

### Post by oldfred on 2019-05-15
The swap of controller cards worked on old drives. Most new drives are electronically tuned for alignment and without lots of equipment, it may not work.

If drive not spinning.
Some of the other old fixes were using oven  to either loosen old lube or freezer to shrink metal parts so drive would start. Those types of fixes would only start drive once, or you must immediately copy data.Sometimes light tap with rubber mallet to get it to start spinning would loosen it just enough. But these types of "fixes" also often totally destroy drive. So only use as last resort.

Drives do fail, sometimes totally. This is why backups are so important. Ok, I know horse is out of barn, so a little late to close barn door. :)
Hope you already have backups of new system.

From Disks and icon in upper right corner is Smart Status. It will show details on drive, but all I know is good/bad. It can run tests, but if drive is auto shutting down due to an issue then you may not have time to run tests.

---

### Post by HermanAB on 2019-05-15
BTW, another crazy thing you can try, is to turn the drive sideways - vertical.  With a notebook, flip the machine on its side and see whether the drive keeps going.  It changes the load on the bearings of the motors and actuators.

You can also try to put the machine inside your fridge for an hour, then boot it up in the fridge and keep it in there to see if it keeps going.  If that works, find a powerful A/C and work in front of it - or in a chest freezer with the lid open...

---

