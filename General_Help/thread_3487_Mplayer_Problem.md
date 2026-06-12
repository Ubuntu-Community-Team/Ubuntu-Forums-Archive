---
title: "Mplayer Problem"
date: 2004-11-06
forum: General Help
---

### Post by andy_sp1ke on 2004-11-06
Hi

I am having a few issues with media players on Ubuntu, which is a shame because otherwise its my favourite OS! 

Totem was useless because they had removed the ability to play anything, why?!?  I have unistalled that and am going to have a look at installing a new version. 

MPlayer i got working as command line only, no GUI. When it comes to configuring the gui (./configure --enable-gui) it runs through and throughs up an error on PNG. I have tried installing PNG as suggested but its conflicting :s 

Checking for PNG support ... no (mismatch of library and  header versions)

How do I unistall all versions and install a fresh one? Can i do it all through synaptic? 


cheers for any help.

andy

---

### Post by FLeiXiuS on 2004-11-06
[QUOTE=andy_sp1ke]Hi

I am having a few issues with media players on Ubuntu, which is a shame because otherwise its my favourite OS! 

Totem was useless because they had removed the ability to play anything, why?!?  I have unistalled that and am going to have a look at installing a new version. 

MPlayer i got working as command line only, no GUI. When it comes to configuring the gui (./configure --enable-gui) it runs through and throughs up an error on PNG. I have tried installing PNG as suggested but its conflicting :s 

Checking for PNG support ... no (mismatch of library and  header versions)

How do I unistall all versions and install a fresh one? Can i do it all through synaptic? 


cheers for any help.

andy[/QUOTE]

Take a look at this thread in the HOWTO section...
[http://ubuntuforums.org/showthread.php?t=94](http://ubuntuforums.org/showthread.php?t=94)

---

### Post by andy_sp1ke on 2004-11-06
Thanks, I think I have followed that before and it couldnt get the LibPNG download. I'm having another go and if it doesnt work i'll post what it is saying to me.

andy

---

### Post by andy_sp1ke on 2004-11-06
Ok here it is!

root@andysp1ke:/home/andy # sudo apt-get install libpng-dev
Reading Package Lists... Done
Building Dependency Tree... Done
Package libpng-dev is a virtual package provided by:
  libpng12-dev 1.2.5.0-7ubuntu1
You should explicitly select one to install.
E: Package libpng-dev has no installation candidate


Now i figure this means i need to install libpng12-dev and 1.2.5.0-7ubuntu1? I know one is a seperate package but i know nothing about the other one. I tried getting libpng using the below.

root@andysp1ke:/home/andy # sudo apt-get install libpng12-dev
Reading Package Lists... Done
Building Dependency Tree... Done
libpng12-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So that should be ok? Must be the other one? But that doesnt exist.

root@andysp1ke:/home/andy # sudo apt-get install 1.2.5.0-7ubuntu1
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package 1.2.5.0-7ubuntu1


So I dont know where to go now!

---

### Post by Julius on 2004-11-06
[QUOTE=andy_sp1ke]Ok here it is!

root@andysp1ke:/home/andy # sudo apt-get install libpng12-dev
Reading Package Lists... Done
Building Dependency Tree... Done
libpng12-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[/QUOTE]

That should work.

---

### Post by andy_sp1ke on 2004-11-06
Thanks for the help, got it all going now!

---

### Post by sun on 2004-11-14
I have the same issue.  What did you do to resolve this?

---

### Post by adbak on 2004-11-14
Everything should work if you follow the HOWTO in the appropriate section.

---

### Post by mattyh on 2004-11-14
I don't remember if this is in the HOWTO or not, but installing totem-xine is useful, because then you get preview pics of all the video's and what not.  I like that as an alternative to the quite inferior (imo) totem-gstreamer.

---

### Post by iminj on 2004-11-14
After 2 weeks with linux and Ubuntu, I've overcome numerous learning curve issues thanks to the tremendous community here. Now it's time to tackle one of the elusive issues - mplayer, which hasn't worked on my system since Day 1.

I followed the multimedia HOWTO step-by-step, and presumably I have mplayer and it's GUI installed .. (but obviously not working correctly).

Here's what happens when I put a DVD movie in my DVD drive:

(1) The movie's folder mounts on my desktop, however, mplayer doesn't automatically open. 
(2) Right clicking the mounted folder, and examining "Properties" reveals that the folder's Location is: /media
(3) I manually set the "open with" tab property to gmplayer
(4) When I open mplayer, and go thru the menu to Open/Play DVD, I get the following error message: "Couldn't open DVD device: /dev/dvd"

Anyone able to assist ? Is there a conflict between the folder location - /media and the location that mplayer is looking for ... /dev/dvd? If so, how do I correct it?


iminj

---

### Post by adbak on 2004-11-14
Have you apt-gotten (pardon my pun ;)  ) ```
libdvdcss2
``` yet?

If not, that may be what's missing.  Make sure to enable the Universe repositories.

---

### Post by iminj on 2004-11-15
[QUOTE=adbak]Have you apt-gotten (pardon my pun ;)  ) ```
libdvdcss2
``` yet?

If not, that may be what's missing.  Make sure to enable the Universe repositories.[/QUOTE]

Yes. I have libdvdcss2 installed -  version 1.2.8-0.0

---

### Post by mahalram on 2004-11-17
[QUOTE=iminj]After 2 weeks with linux and Ubuntu, I've overcome numerous learning curve issues thanks to the tremendous community here. Now it's time to tackle one of the elusive issues - mplayer, which hasn't worked on my system since Day 1.

I followed the multimedia HOWTO step-by-step, and presumably I have mplayer and it's GUI installed .. (but obviously not working correctly).

Here's what happens when I put a DVD movie in my DVD drive:

(1) The movie's folder mounts on my desktop, however, mplayer doesn't automatically open. 
(2) Right clicking the mounted folder, and examining "Properties" reveals that the folder's Location is: /media
(3) I manually set the "open with" tab property to gmplayer
(4) When I open mplayer, and go thru the menu to Open/Play DVD, I get the following error message: "Couldn't open DVD device: /dev/dvd"

Anyone able to assist ? Is there a conflict between the folder location - /media and the location that mplayer is looking for ... /dev/dvd? If so, how do I correct it?


iminj[/QUOTE]

Mplayer looks for /dev/dvd. Even though the multimedia howto says that you have to link  /dev/dvd,  to say /dev/cdrom0 in my machine I found that it was already there and linked the /dev/hdc . (Mine is a sony vaio TR2AP3 laptop) You may have the same issue. Check with 

ls -l /dev/dvd

So this is what I use for playing DVDs with mplayer in ubuntu

Command line 
mplayer dvd:// /dev/hdc

GUI
open gui and click on the file chooser. At the bottom choose "all files" then navigate to /dev/hdc 
(or whatever you /dev/dvd points to) That does it for me 
Hope this helps

---

### Post by adbak on 2004-11-17
A much easier way of getting MPlayer working is to add
```
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```
to your /etc/apt/sources.list.  Notice I said "testing" and not "stable", like I'm sure you've seen countless times before.

apt-get update, then apt-get install mplayer.

Works like a charm, and much more responsive than when I installed from the HOWTO.

---

### Post by iminj on 2004-11-17
[QUOTE=mahalram]Mplayer looks for /dev/dvd. Even though the multimedia howto says that you have to link  /dev/dvd,  to say /dev/cdrom0 in my machine I found that it was already there and linked the /dev/hdc . (Mine is a sony vaio TR2AP3 laptop) You may have the same issue. Check with 

ls -l /dev/dvd

So this is what I use for playing DVDs with mplayer in ubuntu

Command line 
mplayer dvd:// /dev/hdc

GUI
open gui and click on the file chooser. At the bottom choose "all files" then navigate to /dev/hdc 
(or whatever you /dev/dvd points to) That does it for me 
Hope this helps[/QUOTE]

mahalram:

Thanks for this .. although you are few steps ahead of me.

In my case, **ls -l /dev/dvd** returned the following: 
"No such file or directory"

So, mplayer seeks a directory that apparently doesn't exist. In an earlier post I reported that when i loaded a DVD into the drive, it mounted to the desktop and the properties said it was located at /media.

How to do get mplayer to look in /media OR how do I define /media as /dev/dvd?

iminj

---

### Post by Julius on 2004-11-17
/media is not where the dvd/cd rom is mounted. They are mounted on folders that are INSIDE /media.
I just dont know why I can't play a DVD in mplayer now without changing any options.

However:

1- You can use Totem-xine to play DVDs. IMO it's better because it has menu support. Just do a File > Play disc and that should work 
2- Start gmplayer (from a console). Do a right click in the video window and go to preferences. GO to the misc tab. In the bottom of that page you'll find where the links to the dvd and cd drives are. If you are not sure how's ur DVD drive linked-as. Do a "nano /etc/fstab" (without sudo, just in case :P) and check there. The right /dev/hdx thing in the gmplayer config should work when you do "DVD > Play disc"
3- Let's say your dvd-rom is /dev/hdc. I guess that if you copy that file, change its name /dev/dvd and paste it again in /dev, you will have mplayer working correctly. Not sure, though.

---

### Post by iminj on 2004-11-18
[QUOTE=Julius]
1- You can use Totem-xine to play DVDs. IMO it's better because it has menu support. Just do a File > Play disc and that should work[/QUOTE]

That's what I did ! .. and the combination of Totem-xine and mozplugger works. Totem-xine opens DVD's and with mozplugger, the codecs, (and realplayer), Firefox can stream video ( wmv / asf / real / qt) and audio (m3u / asx / wma / ra)

Oddly, installing mozplugger broke my earlier .pls (shoutcast) and .ogg streaming to xmms .. but that will be addressed in another thread.

I gave mplayer 2 weeks, but never got it working satisfactorily. It wouldn't open DVD's; and the mplayer plugin for Firefox never worked on my system. Certainly, the core issue is my lack of experience in linux ( 2 weeks), but I'm walking away from mplayer convinced that it's complexity and unintuitive configuration is not ready for a typical NOOB like me. Hopefully, the folks at ubuntu will find a creative way to address this issue down the road - as painful multimedia implementation will not attract new users to this otherwise terrific distro.

**Final question:** I installed mplayer using the HOWTO in this forum. mplayer is on my system, but it doesn't show up in Synaptic. How do I remove it?

thanks to all 
iminj

---

### Post by mainlylinux on 2004-11-18
You need to created a symbolic link - that's why you are getting the error about /dev/dvd.

Go to a root terminal, and type ln -s /media/cdrom(x) /dev/dvd


where x is the appropriate number of your dvd device.

try mplayer again.

Dan

---

