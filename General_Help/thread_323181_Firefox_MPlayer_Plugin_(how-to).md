---
title: "Firefox MPlayer Plugin (how-to)"
date: 2006-12-21
forum: General Help
---

### Post by fbolduc on 2006-12-21
I wanted to play QuickTime, RealPlayer and WMV movies in Firefox, so I started looking around a bit for alternatives. I found that MPlayer could do anything I wanted, so I gave it a shot. I successfuly installed MPlayer and it's Firefox plugin and I tought that I should share my experience with others.

I tested this on default installation of Ubuntu Dapper and Ubuntu Edgy, both with X86 processors.

For AMD64 and PowerPC processors, you'll need to replace the CODEC archive (essential-20061022.tar.bz2) with the one appropriate to your processor (and change some of the commands since it's not the same file name). See [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/) for more informations.

Here's the script (same as attachement):
```

#!/bin/bash
if [ `id -u` != "0" ]; then
	echo "You should be root to run this script."
	exit 1
fi
apt-get install build-essential libpng12-dev libpng3-dev libgtk1.2-dev libgtkgl2.0-dev libgtkmm2.0-dev libgtk2.0-dev libwxgtk2.4-dev libx11-dev libxpm-dev libxt-dev firefox-dev
cd
mkdir mplayer-temp
cd mplayer-temp
wget http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc1.tar.bz2
wget http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2
wget http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.8.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.31.tar.gz
tar -xf MPlayer-1.0rc1.tar.bz2
tar -xf essential-20061022.tar.bz2
tar -xf clearplayer-0.8.tar.bz2
tar -xf mplayerplug-in-3.31.tar.gz
mkdir /usr/local/share/mplayer/
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf /usr/local/share/mplayer/subfont.ttf
mkdir /usr/local/share/mplayer/skins/
cp --recursive clearplayer/ /usr/local/share/mplayer/skins/
ln -s /usr/local/share/mplayer/skins/clearplayer/ /usr/local/share/mplayer/skins/default
mkdir /usr/local/lib/codecs/
cp essential-20061022/* /usr/local/lib/codecs/
cd MPlayer-1.0rc1
./configure --enable-gui
make -s
make install
cd ../mplayerplug-in
./configure
make -s
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
cd
rm -rf mplayer-temp

```

After that, just restart Firefox. To see if it worked, go to URL: about:plugins . If installed successfuly, you should see lots of references to mplayerplug-in 3.31 on that page.

Here's a list of file extensions that are supported:

asf,asx,au,avi,divx,flc,fli,m3u,mod
mov,mp2,mp2ve,mp3,mp4,mp4
mpeg,mpg,mpv2,nsv,ogg
ra,ram,rm,rv,sdp,smil,snd
viv,vivo,wav,wax
wm,wma,wmp,wmv,wvx

Uninstallation instructions:
[http://ubuntuforums.org/showthread.php?t=338168](http://ubuntuforums.org/showthread.php?t=338168)

---

### Post by yopnono on 2006-12-21
You have mplayer in the repo

---

### Post by fbolduc on 2006-12-21
Yes, but not the version with with all the proprietary codecs (QuickTime, RealPlayer, WMV, etc.) as far as I know.

Oh, and I forgot to mention that using those codecs might be illegal in your country.

---

### Post by Azakus on 2006-12-21
Mine came from the repos and had all the proprietary codecs.

---

### Post by NeoChaosX on 2006-12-21
I'd suggest going the route suggestedi n this thread, especially if you have Edgy. The stock mozilla-mplayer/mplayerplug-in in the Edgy repos doesn't seem to play nice with some Windows Media streams.

---

### Post by lilolpete on 2006-12-23
Someone should sticky this guide! :KS I could not get my video working for the longest time, and as a newbie this helped me out tremendousely! THANK YOU!!!:D

---

### Post by lilolpete on 2006-12-23
One more thing. When I try viewing video streams I can't really scale it. Theres not zoom function. Also when I hit full screen it keeps the same size but has huge black borders around it. What can i do to fix this? Thanks!

---

### Post by agx on 2006-12-23
How do you make the plugin replay the videos automatically?

---

### Post by CodyZ on 2006-12-23
This may be obvious to you, but not to me.  Is that script for X86 processors or powerPC processors? I have an X86, do I just copy/paste that into the terminal and then blammo windows media and quicktime streams for me?  Will it mess with the flash I already have set up?  I have linux mint barbara default set up now.

---

### Post by PriceChild on 2006-12-23
totem-xine or totem-gstreamer work perfectly on my system with plugins for firefox.

Guide here: [uwiki]RestrictedFormats[/uwiki]

---

### Post by fca_neo on 2006-12-23
Sorry, I'm a total newbie, but, how do you run this scrip?

---

### Post by hanzomon4 on 2006-12-23
> **PriceChild said:**
> totem-xine or totem-gstreamer work perfectly on my system with plugins for firefox.

Guide here: [uwiki]RestrictedFormats[/uwiki]

Totem plugin has never worked for me. I just installed it and removed mplayer-plugin, but I'm still just getting a white box where  the video should be.  Here's a link to the video I tried [:LINK:]("http://www.gamespot.com/xbox360/sports/nba2k7/index.html"), just scroll down and pick one......

---

### Post by mrphd on 2006-12-26
I have used the script but there seem to be some issues with audio. ALSA doesn't work for all content. And while I can use OSS where this fails, the sound cuts when the window loses focus. I get this with the bbc news viewer and some others.

Does anyone else experience this? And does anyone know how I can solve this problem?

---

### Post by lilolpete on 2006-12-26
> **fca_neo said:**
> Sorry, I'm a total newbie, but, how do you run this scrip?

How I ran the script was just doing it line by line. Make sure you dont have any other plugins that might get in the way of this one! Otherwise it wont work. I had VLC plugin and I had to remove this before it worked. 

Now this thing plays everything. Now inorder to get zoom to work just go to the configuration file for MPLAYER and type in zoom=yes. And all will be well!

---

### Post by st14n on 2006-12-28
> **lilolpete said:**
> One more thing. When I try viewing video streams I can't really scale it. Theres not zoom function. Also when I hit full screen it keeps the same size but has huge black borders around it. What can i do to fix this? Thanks!

For me, this happens when I start mplayer with the -vo X11 option. This may be default for you. Try to add the parameter -zoom. Or better, check if the video works with -vo xv instead; it is faster. You may change the default behavior for your mplayer to something that works for you by looking into the ~./mplayer directory.

---

### Post by Michaelt74 on 2006-12-28
Like Cody and fca, I'm just starting to use Ubuntu; with mixed results so far. These guides are all fine - provided you have some linux know how; I don't. So to ask the question again, how do you run the script?

Click on applications>accessories>terminal> What next? 

Could anyone tell me what to do step by step, please.

Thanks

---

### Post by mrphd on 2006-12-28
> **Michaelt74 said:**
> Could anyone tell me what to do step by step, please.
Thanks

1. Save the script to your desktop. Let's say it is called mplayer.sh
2. Open a terminal
3. Type "cd ~/Desktop"
3. Type "sudo sh mplayer.sh" and enter your password as prompted.
4. Wait! 

Finished!

---

### Post by Michaelt74 on 2006-12-28
Thanks, but I don't understand what you mean "save the script to the desktop" - how?

---

### Post by nix4me on 2006-12-28
I recommend using the cvs code for both mplayer and mplayer plugin if you are going to compile your own.

The release versions of mplayer and mplayer plugin are old and they are both available in the repositories.  Both are very slow to release updated versions and the cvs is much more up to date.

The cvs versions have many bugfixes and work much better.  

nix4me

---

### Post by mrphd on 2006-12-29
> **Michaelt74 said:**
> Thanks, but I don't understand what you mean "save the script to the desktop" - how?

For this go to the menu item Applications->Accessories->Text Editor. Now copy the code from the original post by fbolduc into the clipboard. Now just past this into the text editor you just opened. Go to File->Save as and call the file mplayer.sh. Choose desktop as the folder you want to save into.

---

### Post by Michaelt74 on 2006-12-29
Thanks for the help, will let you know if I get it working.

---

### Post by Michaelt74 on 2006-12-29
I ran the script, but as soon as I tried to open a video from Yahoo, the player opened, black screen with small 'play diagram in the centre. Next, I clicked it, the following message appeared:

Error opening/initializing the selected video_out (-vo) device

I checked out the FAQ's for the error, the Mplayer site said the following:

Q:	

I've just installed MPlayer. When I want to open a video file it causes a fatal error:

Error opening/initializing the selected video_out (-vo) device.

How can I solve my problem?
A:	

Just change your video output device. Issue the following command to get a list of available video output drivers:

mplayer -vo help

After you've chosen the correct video output driver, add it to your configuration file. Add

vo = selected_vo

to ~/.mplayer/config and/or

vo_driver = selected_vo

to ~/.mplayer/gui.conf. 

How do I know what output device to choose and how do I change it?

---

### Post by mrphd on 2006-12-30
First, can you try viewing some other video online, say from [www.apple.com/trailers/?](www.apple.com/trailers/?) Does this work? 

Does yahoo use flash? Do you get the same problem if you go to youtube (which also uses flash)? I'm just trying to establish if the problem you have is with flash or with mplayer...

Let me know...

---

### Post by Michaelt74 on 2006-12-30
I managed to make the VLC player run the wmv files, Totem works fine for everything Quicktime. I'll leave mplayer alone at this stage until I have some sort of idea about how linux works. Thanks again.

---

### Post by komaroveli on 2006-12-31
hi
could you help me with my problem?
script worked just fine. i can view trailers (CNN, BBC etc) with no problems (video and sound are fine). but when i play avi films i get no sound, or to be exact - very high pitch noise! video is fine.

---

### Post by CheeseQueen452 on 2006-12-31
I just want to say thankyou for posting this script!! I was a little afraid to install it at first, but I decided to try it. Now I can watch Yahoo news clips & ET/Insider videos :) YEY!! They don't play perfectly(a little choppy), but then again they never did.... For a while I was using the Mplayer-connectivity extension which I didn't really like. At least I can now watch the videos in Firefox the way it was intended :) Thankyou again!!

---

### Post by psycho78 on 2007-01-01
unfortunately the script did not help me... I deinstalled every plugin i had (vlc, totem, xine, mplayer), afterwards I ran the script.
mplayer tries to start but stops immediately.... I don't know what else I can try...:(
about:plugin tells me that every media file will be played with mplayer 3.31 ....

---

### Post by lilmienboy on 2007-01-02
has anybody try watching video at NBA.com because when i watch it , its really choppy.

---

### Post by andshoesandsocks on 2007-01-05
Hi, I am completely new to ubuntu. I tried to use that code exactly as the directions stated. Here is what I got back:


Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... not found

*** Please downgrade/upgrade C compiler to version gcc-2.95, 3.x or 4.x! ***



can anyone help me with this problem please...

---

### Post by dmizer on 2007-01-07
> **PriceChild said:**
> totem-xine or totem-gstreamer work perfectly on my system with plugins for firefox.

Guide here: [uwiki]RestrictedFormats[/uwiki]

okay ... please stop in here: [http://www.ubuntuforums.org/showthread.php?p=1975107#post1975107](http://www.ubuntuforums.org/showthread.php?p=1975107#post1975107) and let me know how it's suppose to be done? because the restricted formats wiki is the EXACT same thing i followed to make mine not work.

btw ... this script did not resolve this issue: [http://www.ubuntuforums.com/showthread.php?t=322085](http://www.ubuntuforums.com/showthread.php?t=322085) mplayer still insists on attempting to play the video without caching.

---

### Post by dmizer on 2007-01-07
> **andshoesandsocks said:**
> Hi, I am completely new to ubuntu. I tried to use that code exactly as the directions stated. Here is what I got back:


Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... not found

*** Please downgrade/upgrade C compiler to version gcc-2.95, 3.x or 4.x! ***



can anyone help me with this problem please...

i think you'll need to do the following:
```
sudo aptitude install build-essential
```
you should be able to make the script work then.

---

### Post by Michaelt74 on 2007-01-08
Dmizer, I'm a newbie too, forget about the restricted format links or anything related to them, I tried what they suggested but it didn't help me.

---

### Post by darweth on 2007-01-10
This script was pretty amazing EXCEPT it did not set up an ALSA audio driver for me and now I can no longer watch movies and stuff offline due to no audio.  There is no ALSA option under audio in prefs.  Is there anyway to fix this?  I need my MPlayer!!!!  Ahhhh!

**edit** actually, it is not so amazing.  Other than the sound problem, the video runs really poorly too (offline with avis).  Either slow and choppy or really sped up and messy.  Ahhhh.  This never happened with the old MPlayer that DIDN"T work well in Firefox.  It seems I have traded perfect playback of xvid/divx etc offline for good playback of wmv, rm, quicktime, etc. online. :/

---

### Post by darweth on 2007-01-10
I noticed one other person mentioned troubles with mplayer and avis offline.  Ahhh!  Seriously... can people comment on this script and NON-firefox vids in mplayer?  It is impossible to watch them with the player the way it is.

---

### Post by steampunk on 2007-01-13
I'm seriously getting tired of not being able to hear online videos. Apple.com/trailers and youtube.com will allow me to watch them, but not to hear them. I've tried every single thing in this thread to no avail. I can download the videos and hear them fine. I can play ordinary videos of any single format and hear them fine. However, anything that I'm watching in Firefox does NOT have audio. I'm so frustrated! :mad:

---

### Post by darweth on 2007-01-14
Can someone give this newb a terminal rundown of how to uninstall everything installed by the script in the first post?  I have decided to attempt a switch to Totem for streaming video.  Thanks!

---

### Post by clemslacker on 2007-01-16
here's a rundown of how to run this script

1) copy and paste the text of the script in a text editor (save it as filename.sh)
2) change directory to the location of filename.sh in a terminal (e.g. $ cd /home/username/filename.sh)
3) change permissions of the file (e.g. $ chmod 777 filename.sh)
4) run the file as superuser (e.g. $ sudo ./filename.sh)

you should then see output within the terminal and all the commands in the script should execute, such as making the directory for mplayer (e.g. mkdir /usr/bin/mplayer).

---

### Post by steampunk on 2007-01-18
> **clemslacker said:**
> here's a rundown of how to run this script

1) copy and paste the text of the script in a text editor (save it as filename.sh)
2) change directory to the location of filename.sh in a terminal (e.g. $ cd /home/username/filename.sh)
3) change permissions of the file (e.g. $ chmod 777 filename.sh)
4) run the file as superuser (e.g. $ sudo ./filename.sh)

you should then see output within the terminal and all the commands in the script should execute, such as making the directory for mplayer (e.g. mkdir /usr/bin/mplayer).

"how to ***uninstall*** everything installed by the script"

---

### Post by davekenny on 2007-01-19
after trying the suggestion in other posts. I tried this one. and it worked:):):p 

Thanks

-dave

---

### Post by CheeseQueen452 on 2007-01-23
I need help!! I installed this script a while back & it was working fine, but there were updates this morning that included mozilla-totem, & now streaming videos won't work! I tried to install this script again, but when I entered the code in a terminal, I heard a system beep & the terminal window closed. How do I install the script? HELP!!!

---

### Post by CheeseQueen452 on 2007-01-23
Anyone?

---

### Post by CheeseQueen452 on 2007-01-23
Ok, I uninstalled totem-mozilla & the streaming videos work again :) Phew!!

---

### Post by dmizer on 2007-02-21
to make mplayerplug-in work perfectly for streaming media in firefox, see this thread: [http://www.ubuntuforums.org/showthread.php?t=322085](http://www.ubuntuforums.org/showthread.php?t=322085)

the above thread works with mplayer/mplayerplug-in in both dapper and edgy, and it works with the mplayer/mplayerplug-in out of the repositories.

this script does not compile with alsa, so sound will be a huge problem.  if you DO run the script, i suggest removing the last line, so that you can easily uninstall it later.

---

### Post by CheeseQueen452 on 2007-02-21
I have the script in this thread(not the one you mentioned) installed & working fine for the most part, but I'm curious... if I install the mplayerplug-in-0.4.xpi add-on, will I have any problems or conflicts with the script? The website to download the add-on says "This Extension converts OBJECT tags to EMBED tags for sites that only support IE." So, I'm wondering if this will help me with certain websites that I've been unable to play streaming media because of OS/browser compatibility. This is primarily a window$ world, after all.....

> **dmizer said:**
> to make mplayerplug-in work perfectly for streaming media in firefox, see this thread: [http://www.ubuntuforums.org/showthread.php?t=322085](http://www.ubuntuforums.org/showthread.php?t=322085)

the above thread works with mplayer/mplayerplug-in in both dapper and edgy, and it works with the mplayer/mplayerplug-in out of the repositories.

this script does not compile with alsa, so sound will be a huge problem.  if you DO run the script, i suggest removing the last line, so that you can easily uninstall it later.

---

### Post by dmizer on 2007-02-21
yes, installing the extension will help.  but that won't fix the lack of alsa sound support.

of course, if it's working for you ... power to ya.

---

### Post by latanerp on 2007-02-22
Wow, nothing else had worked to get mplayer working in Firefox and I really didn't think this was going to work because I got so many errors; but sure enough, I restarted Firefox, and it did.  Amazing.  Thanks a lot.

---

### Post by CheeseQueen452 on 2007-02-22
I noticed something interesting.... The extension worked *almost* flawlessly, although it didn't help with a couple of sites that are IE specific. But here's the interesting thing.... At etonline.com, the videos there use the real player plugin, but with the script in this thread, the mplayer plugin takes over. After installing the extension, the videos used real player. I have now uninstalled the extension, but the videos STILL use real player. How can this be? Not that I'm complaining, at least the videos work.... but shouldn't the mplayer plugin take over again?

> **CheeseQueen452 said:**
> I have the script in this thread(not the one you mentioned) installed & working fine for the most part, but I'm curious... if I install the mplayerplug-in-0.4.xpi add-on, will I have any problems or conflicts with the script? The website to download the add-on says "This Extension converts OBJECT tags to EMBED tags for sites that only support IE." So, I'm wondering if this will help me with certain websites that I've been unable to play streaming media because of OS/browser compatibility. This is primarily a window$ world, after all.....

---

### Post by dmizer on 2007-02-22
your problem is/was not the mplayerplug-in extension.

your problem is that you have two media plugins to handle the same media stream, and firefox doesn't know which to use.  if you want to use only mplayer to play all streaming media, then you will need to remove the references to real player in your plugins folder (usually /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins/)

---

### Post by CheeseQueen452 on 2007-02-23
I can't manually delete them since I'm not logged in as root. What's the psudo command?

> **dmizer said:**
> your problem is/was not the mplayerplug-in extension.

your problem is that you have two media plugins to handle the same media stream, and firefox doesn't know which to use.  if you want to use only mplayer to play all streaming media, then you will need to remove the references to real player in your plugins folder (usually /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins/)

---

### Post by dmizer on 2007-02-23
> **CheeseQueen452 said:**
> What's the psudo command?

sudo command-here.

or in this case: sudo rm filename

---

### Post by CheeseQueen452 on 2007-02-24
It didn't work. Strange..... I'm sure I typed the command correctly, & it said no such file or directory. But the file is there. Oh well, guess I'll just leave it. The streaming videos work, so it's not really a problem.

> **dmizer said:**
> sudo command-here.

or in this case: sudo rm filename

---

### Post by H.E. Pennypacker on 2007-04-06
After running this script, whenever I'd try to play a zshare video, Firefox, Epiphany, and Galeon would crash.  

Note: Zshare.com never worked for me, but it never crashed on me either.

---

### Post by ampted on 2007-06-30
why not???```
apt-get install mplayer
```?????????????????????????????????? works fine for me!!!!

---

### Post by cchevy on 2007-11-05
This might not be the place but I could not locate where to write my question, which i think involves ff plugins.

When audio is played in firefox and opera i cant play anything as it says: the device is busy.

how can i play audio files simultaneosly in a browser and on totem?

when i played 2 files with different aplications there was no problem.. i think that it might be the audio from the flash perhaps(youtube)

---

### Post by IwasAnex on 2008-03-14
OK, So I'm new to Ubuntu, but a not as new to Linux. I noticed this script is getting a little dated but it worked fine for me. it just needs some tweaks to get it to run. I am running 7.10 Gutsy on a AMD64. Here is what i did after downloading the script.

Removed libpng3-dev from the list of apts to install. The apt-get was spitting back an error that would make the script crash at the end. 

edited the line

wget [http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20061022.tar.bz2)

to

wget [http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2)

plus clearplayer has been updated to 0.9 so you need to edit it's line accordingly

wget [http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.9.tar.bz2](http://www.mplayerhq.hu/MPlayer/skins/clearplayer-0.9.tar.bz2)

and then update the rest of the script where it called the codecs and skin.

tar -xf essential-amd64-20071007.tar.bz2
tar -xf clearplayer-0.9.tar.bz2

cp essential-amd64-20071007/* /usr/local/lib/codecs/


I haven't put the player through all its paces yet, but I'm streaming windows media, which never worked for me before.

Have fun, play safe.

---

