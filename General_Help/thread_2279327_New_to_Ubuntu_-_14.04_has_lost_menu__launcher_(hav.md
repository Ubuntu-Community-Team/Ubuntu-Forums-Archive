---
title: "New to Ubuntu - 14.04 has lost menu / launcher (have tried suggestions on other posts"
date: 2015-05-22
forum: General Help
---

### Post by jon91 on 2015-05-22
Hi,

I am new to Ubuntu, and installed it 2 months ago (14.04),

I update it every day, and whenever prompted to.

Last night, after an update and re-boot - the screen only shows a desktop, and NO menu or launcher.
(If I open a file on the desktop - there is no 'close' button etc).

I have looked around this forum and others - and followed advice given to one or two others in a similar position.
eg
[http://ubuntuforums.org/showthread.php?t=2238678&](http://ubuntuforums.org/showthread.php?t=2238678&)

[http://ubuntuforums.org/showthread.php?t=2278870&highlight=14.04+lost+menu](http://ubuntuforums.org/showthread.php?t=2278870&highlight=14.04+lost+menu)


I have recently run:
sudo apt-get dist-upgrade
from a terminal and re-booted.

No change......

I would be grateful for some help as what to do next.....

Laptop is Medion E7214 w/ 3 GB memory
14.04, 32 bit version
Dual boot - HDD with original windows, and 240Gb SSD with ONLY Ubuntu.
I select the SSD during bootup in the bios manually every time I re-boot (JUST in case friends kids manage to get hold of it!! DEfault is windows boot - so they can't do any harm!!!).
Since the problem started I did run the Software Updater

Many thanks for all your help - as I am now beyond my abilities to solve this - despite loving Ubuntu/

Jon

---

### Post by grahammechanical on 2015-05-22
Well, what can I advise? The advice I gave in that first thread you linked to worked for some. Is it not working for you? Another thing to try is to right click the wallpaper and you will notice that the drop down menu has an option to Change Desktop Background. Select that and you will be at System Settings>Appearance. From there open the first page of System Settings and go to Software & Updates>Additional Drivers tab and try another video driver. Try the open source driver and do a couple of restarts to discipline Ubuntu and then start a proprietary driver if that is your wish.

Regards.

---

### Post by jon91 on 2015-05-25
Hi Graham,

Many thanks for your help):P.

I have had a look at other threads.... and found similar issues......

As per your suggestions - I looked for a generic driver on my machine under:
Software & Updates>Additional Drivers tab
however - none are listed.....

So I looked around - and managed to download the correct .deb file for my laptop's video driver onto a usb stick.
(Sadly - I still haven't worked out how to open it on teh USB stick from the terminal window...... Might need a little help on that one!!!)

In the mean time - tonight I have spent another few hours...

I have run from the terminal:

sudo apt-get update
sudo apt-get dist-upgrade

then I ran:

sudo apt-get install unity-tweak-tool

unity-tweak-tool --reset-unity

now I have gone to the normal scren (gui???) with Cntl + Alt + F7 and then back to the terminal with Cntl + Alt + F1 - I have a load of messages - which may well point to the problem (the first line written many times):

(unity-tweak-tool:3969): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
start: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
Invalid MIT-MAGIC-COOKIE-1 keycompliz (core) - Fatal: Couldn't open display :O
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
Please log out and log back in.

(I typed all of the above by hand - so please forgive any mistakes).


Hmmmm - have re-booted - and it's exactly the same......


2am now - so I will call it a day....

I look forward to any further suggestions.
My knowledge of computers is very basic - so I am learning all the terminal commands as I go along .......

Many thanks in advance for any help and/or suggestions...

Jon

---

