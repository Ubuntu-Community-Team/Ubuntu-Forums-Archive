---
title: "AVI to MP4 or H.264 for the iphone"
date: 2008-05-07
forum: General Help
---

### Post by Nick w on 2008-05-07
Im tired of looking with no luck at all for a ubuntu converter which will convert my AVI file to a MP4 or H.264 so i can watch it on my iphone.

can any one help?

im lost, i need help, HELP ME UBUNTU FORUMS!

---

### Post by HermanAB on 2008-05-07
Avidemux can do it.

---

### Post by starfry on 2008-05-07
I use "mencoder" to transcode the BBC iplayer files into avi files for playing on my Zen.

---

### Post by Nick w on 2008-05-07
> **HermanAB said:**
> Avidemux can do it.

how did you install it?

im having endless problems!

---

### Post by Creative2 on 2008-05-10
install ffmpeg after you have actived medibuntu repository then try with this 

ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 128k -s 480x320 -aspect 4:3 OUTPUT

---

### Post by Nepherte on 2008-05-10
A thread that helped me out a lot is: [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)

It converts dvds to mp4 format in a mkv container. You could change some commands to get the desired result.

---

### Post by Emmanuel BOCQUET on 2008-12-30
You can try this, it works for me on my ipod Touch (after searching 3 hours)

mencoder -ovc lavc -oac lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=800:threads=4:acodec=libfaac -af lavcresample=24000 -vf scale=480:320,harddup -lavfopts format=psp -ofps 30000/1001 SOURCE.avi -o /samba/DEST.mp4 -sub SUB.srt -subfont-text-scale 3

---

### Post by SetsunaFSei on 2008-12-31
The easiest way is by installing MediaCoder on Ubuntu using Wine, it works like a charm.  

Step 1)
---------

You need to install wine. First things first go into your menu under Applications->Accessories->Terminal

In the terminal command use these commands 1 at a time

Code:
sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list


This will install the wine sources for you
next in the command line prompt you need to use these commands

Code:
sudo aptitude install wine


for those who use apt-get use

Quote:
Sudo apt-get install wine -> Both produce the same results



---------
Step 2)
---------

Next we need to download mediacoder. Pretty sure all you know the location of MediaCoder but for those that don't it's [http://mediacoder.sourceforge.net/dlfull.htm](http://mediacoder.sourceforge.net/dlfull.htm)

once downloaded you need to be sure exe files are associated with wine so right click on the installer and go to the properties section of the menu.
After thats done you need to Goto the Open With tab and make sure it's associated with wine. if it is then your all set.
Now just double click on the installer and it will run just fine. It is recommend that you leave all settings as they are because this way you can be sure you will be able to find MediaCode.
After you are done you can find MeidaCoder either in Applications -> Wine -> MediaCoder (Ubuntu) or in your userfolder in the .wine directory
(you might have to select "show hidden files).
It might take some time for MediaCoder to start (on my machine approximately 20 seconds because the usual firefox popup is missing).


---------
Step 3)
---------

Download Firefox as it is a requirement for MediaCoder. It doesn't matter if you already installed it unless it is the Windows version which is installed through wine. You can download it here: [http://www.getfirefox.com](http://www.getfirefox.com) Be sure you choose to download the version for Windows. To install it just do the same you did in the step above.


--------
Step 4)
--------

If you still can't start MediaCoder (R6034 error), download the modified manifest file
[http://www.4shared.com/file/19830555/a8edfda4/MicrosoftVC80CRT.html](http://www.4shared.com/file/19830555/a8edfda4/MicrosoftVC80CRT.html)
(you have to extract this into the MediaCoder folder).




This guide was brought to you by thibeaz and expanded by SirAuron (using the workarounds in the thread "MediaCoder on Linux/WINE"
[http://mediacoder.sourceforge.net/forum/viewtopic.php?t=1072](http://mediacoder.sourceforge.net/forum/viewtopic.php?t=1072)
It was tested on Ubuntu 7.04 by several users but it should also work on other linux distributions if wine can run on them. 



Visit the following site for more details:

[http://forum.mediacoderhq.com/viewtopic.php?t=2275](http://forum.mediacoderhq.com/viewtopic.php?t=2275)

---

### Post by pmooney78 on 2008-12-31
I just use the mp4ize script. It runs in a terminal while I'm doing other things and produces iPod-suitable output. So if I have a video file "TheCrucible.avi", I just navigate to the folder containing it and type "mp4ize TheCrucible.avi". Works like a charm for me.

Look here:
[http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html](http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html)

---

### Post by hyperdude111 on 2009-01-01
I use handbrake, it has options for all apple ipods, the iphone, apple tv, ps3, psp and dvd iso. It is available in a .deb and is fast.

---

