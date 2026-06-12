---
title: "Software to edit mp4 file"
date: 2022-10-06
forum: General Help
---

### Post by satimis on 2022-10-06
Hi all,

What will be an easy way to trim/cut mp4 files ?

I prefer to do it on screen/graphic, not on command line.  Previously I used FFMPEG trimming/cutting mp4 files according to time base and it worked.

Please advise.  Thanks

Regards

---

### Post by ronsking on 2022-10-06
Take a look at Avidemux.
[https://avidemux.sourceforge.net/]("https://avidemux.sourceforge.net/")

---

### Post by Autodave on 2022-10-06
Audacity works for me.  You can speed up or slow down the file to get to whatever size you need.  I used to have to make a 15 minute music file once a week and I could get that 15 minutes to withing a couple of seconds on the first try.

---

### Post by satimis on 2022-10-06
> **ronsking said:**
> Take a look at Avidemux.
[https://avidemux.sourceforge.net/]("https://avidemux.sourceforge.net/")
Hi,

Thanks for your advice.

Avidemux V2.8 is running here.  I have tried it before posting.  I can import .mp4 file but I have no way to cut the section which I don't need.  I can't find the cutting tool.

Regards

---

### Post by TheFu on 2022-10-06
LosslessCut-linux-x86_64-3.46.2.AppImage   is what I use today. There may be a new version. I check every month or so.   Took about a decade to find it.  

No transcoding. Cuts are only made on key-frame boundaries, so you'll have to learn when and where a cut can be made if you care about the most accurate cutting. No single-frame accuracy with h.264 or h.265 video codecs. Supports any video file format that ffmpeg supports.

mp4 is just a container, not a video codec or audio codec. Best to learn the difference.

---

### Post by Autodave on 2022-10-06
Audacity will let you cut anywhere....I have edited out sneezes, coughs, throat clearings, etc.  You can stretch or compact to the length that you want.  I have use Audacity for many years for many reasons including editing our church's sermons.  Music made to exact time lengths needed.

---

### Post by satimis on 2022-10-06
> **Autodave said:**
> Audacity will let you cut anywhere....I have edited out sneezes, coughs, throat clearings, etc.  You can stretch or compact to the length that you want.  I have use Audacity for many years for many reasons including editing our church's sermons.  Music made to exact time lengths needed.
Hi,

Thanks for your advice.

To my understanding Audacity only edits audio

I'm now looking at Openshot video editor.  I used it before, long time ago, to edit video.  It worked for me seamlessly but unfortunately I already forgot all steps.

Edit
==
Just made a brief search on Audacity Forum and found following link;

Does Audacity edit MP4 (video) files?
[https://forum.audacityteam.org/viewtopic.php?t=37255](https://forum.audacityteam.org/viewtopic.php?t=37255)

Regards

---

### Post by #&amp;thj^% on 2022-10-06
> **TheFu said:**
> LosslessCut-linux-x86_64-3.46.2.AppImage   is what I use today. There may be a new version. I check every month or so.   Took about a decade to find it.  

No transcoding. Cuts are only made on key-frame boundaries, so you'll have to learn when and where a cut can be made if you care about the most accurate cutting. No single-frame accuracy with h.264 or h.265 video codecs. Supports any video file format that ffmpeg supports.

mp4 is just a container, not a video codec or audio codec. Best to learn the difference.

+1 Great Tool, >>>Current release	2022-07-20: [https://www.videohelp.com/software/LosslessCut/old-versions](https://www.videohelp.com/software/LosslessCut/old-versions)
EDIT: FWIW it also comes as a flatpak, just saying.
 "About LosslessCut You are running version 3.45.0"

---

### Post by TheFu on 2022-10-06
The great thing about LosslessCut is that it doesn't transcode, so there is ZERO loss of quality.  Cuts take as long as saving that part of a file.  Due to limitations in how ffmpeg does merges for video files, those are slow. On a local SSD, it probably doesn't matter. Over NFS, which is how I usually edit video, the merge can be painful, so I use LosslessCut to create the different segments, then use mkvmerge to take those segments and put them into a single mkv container.  MKV containers are extremely flexible and can have pretty much any video and/or audio codes, multiple audio/video streams and subtitles, captions, text, chapters, yadda, yadda, yadda.  MKV containers do it all.  A little bash script takes the first segment and automatically places all others in the series into the same mkv. Very handy, but it is custom for my situation and far from bullet proof, so not really something to be shared.

---

### Post by satimis on 2022-10-06
Hi TheFu and 1fallen,

Thanks for your advice.

Just found following link

How to Install LosslessCut in Ubuntu
[https://www.geeksforgeeks.org/how-to-install-losslesscut-in-ubuntu/](https://www.geeksforgeeks.org/how-to-install-losslesscut-in-ubuntu/)

I suppose it is the right document for me to follow to install LosslessCut

The document suggests 2 methods;
Method 1: Installing LosslessCut using the AppImage
Method 2: Installing LosslessCut using the Snap Store

Which method shall I follow?  Thanks

Regards

---

### Post by Autodave on 2022-10-06
To my understanding Audacity only edits audio

You are correct.  And I am old and senile.  Sigh.  Sorry!!

---

### Post by satimis on 2022-10-06
Hi all,

I found an easy solution for cropping video (mp4).  

There are many FREE online services.  Just upload the mp4 file, crop it and download the finished MP4 file.  That is it.  

If you care the water mark, just pay for removing water mark.  To me I don't care the water mark.

Regards

---

### Post by HermanAB on 2022-10-07
I usually end up using kdenlive to edit videos.  It works reasonably well and reasonable easily, without bothering to read the documentation.  However, bear in mind that to edit any video, with any video editor, you need a machine with a large amount if RAM.

---

### Post by mIk3_08 on 2022-10-07
For me, I usually use kdenlive. kdenlive works well to me. Regards and cheers

---

### Post by satimis on 2022-10-07
> **HermanAB said:**
> I usually end up using kdenlive to edit videos.  It works reasonably well and reasonable easily, without bothering to read the documentation.  However, bear in mind that to edit any video, with any video editor, you need a machine with a large amount if RAM.
Hi,

Thanks for your advice.

I'm running Gnome desktop here.  I have 64G RAM onboard

Regards

---

### Post by satimis on 2022-10-07
> **mIk3_08 said:**
> For me, I usually use kdenlive. kdenlive works well to me. Regards and cheers
Thanks for your advice.
$ apt policy kdenlive```

kdenlive:
  Installed: (none)
  Candidate: 4:21.12.3-0ubuntu1
  Version table:
     4:21.12.3-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
kdenlive is on repo


I'll create an Ubuntu22.04 VM testing kdenlive

Regards

---

### Post by raleigh3 on 2022-10-07
I downloaded this and made it executable, but it will not run?

avidemux_2.8.1.appImage

---

### Post by vanadium on 2022-10-07
For me, it does. It is my preferred tool for quick cutting video.

There is a big difference between using a full-fledged non-linear video editor like KDEnlive and using a lossless cutting tool like this and others mentioned in this thread. Using the former requires you to set up a project, import the video, then, after cutting, render the result out, which results in one round of quality loss due to the recompression. For such simple tasks, use a linear video editing tool, or the command line in a way that the video is not reencoded.

---

### Post by TheFu on 2022-10-07
> **satimis said:**
> Hi TheFu and 1fallen,

Thanks for your advice.

Just found following link

How to Install LosslessCut in Ubuntu
[https://www.geeksforgeeks.org/how-to-install-losslesscut-in-ubuntu/](https://www.geeksforgeeks.org/how-to-install-losslesscut-in-ubuntu/)

I suppose it is the right document for me to follow to install LosslessCut

The document suggests 2 methods;
Method 1: Installing LosslessCut using the AppImage
Method 2: Installing LosslessCut using the Snap Store

Which method shall I follow?  Thanks

Regards

Your choice.  I prefer the appimage to avoid unwanted constraints that I'd have to relax.  

The appimage file is like a standalone exe from MS-DOS in 1990.  There is no "install".  Place the file anywhere you like, chmod +x it and run it.  I use a symbolic link from my ~/bin/ to /usr/local/appimages/LosslessCut so I don't need to add /usr/local/appimages/ to the PATH.  Personal preference. You should do it however you like or think is best.  I haven't bothered to add it to any menu, but my WM would make that trivial.   ... just did it. Took about 20 seconds. I had to make up an accel key-chord and had already used 0-9.

Cropping requires transcoding. LosslessCut doesn't transcode, so it wouldn't be the tool for that.  I usually have handbrake do cropping, since I need to transcode anyways, might as well use an excellent, efficient, transcoding tool.

For me, there are 2 types of videos to be edited.  

a) stuff that will be seen once - like recorded TV.  Editing is about commercial removal (comskip) and as much automation in the process as possible. If a 10G file becomes 2.5G instead of 1.5G, it really doesn't matter, since it will be around for only a few days. A few artifacts don't matter. If I could get GPU transcoding working (not a high priority), then that would probably be fine.  As it is, the Ryzen 5600G transcodes at about 3-4x the actual speed.  I batch up the transcoding from the mpeg2.ts files, have a relatively simple "superfast" ffmpeg transcode, then run comskip.  This is all automatic, so none of my time.  Then I use the transcoded video with the comskip EDL files in LossLessCut to validate the cut locations - 90% accurate  - and export/safe the 50% smaller file. For example, last night Grey's Anatomy was recorded.```

4.2G    Greys_Anatomy-Everything_Has_Changed.ts   <-- Original mpeg2 TS recording (?? min TS doesn't know length)
4.0G    Greys_Anatomy-Everything_Has_Changed-huge-mpg.mkv  <-- fix timeline (63min)
2.3G    Greys_Anatomy-Everything_Has_Changed-huge-sf.mkv  <-- Transcoded to h.264, still has commercials (63min)
**1.6G    Greys_Anatomy-Everything_Has_Changed.mkv  <-- commercials removed (44 min)**
```
Most of the processing is automatic. About 30 seconds of my time involved.
After watching the show, it gets deleted. Sometimes it doesn't even make it into a backup. Recorded TV isn't part of the backups here.

b) stuff that will be archived like travel or converted DVDs.  For these, I want to keep all the audio, subtitles, captions, but have no interest in the company leaders or 90% of the credits, so those are removed.  We have the original or can look up the information online for anything removed.  When we all sit down with the popcorn, we don't want to waste 3 minutes with production company junk. And when the film is over, we might want to know the cast, but nobody cares who did the CGI shading and backgrounds in those movies with 10+ minutes of credits.  Anyway, handbrake does the transcoding using the CPU, not the GPU.

If the Grey's Anatomy above was going to be saved forever, I'd have used slower, but higher quality settings and the file would be ~ 1B in size or smaller. My goal for all transcodes is to have ZERO artifacts, size is less important.

---

### Post by Dennis N on 2022-10-07
> I suppose it is the right document for me to follow to install LosslessCut

The document suggests 2 methods;
Method 1: Installing LosslessCut using the AppImage
Method 2: Installing LosslessCut using the Snap Store

Which method shall I follow? Thanks

Don't forget about Flatpak:
```
losslessCut             Save space by quickly and losslessly trimming video and audio files    no.mifi.losslesscut                          3.45.0       stable    flathub
```

Especially attractive if you already have the necessary freedesktop runtime support already installed!

```
       ID: no.mifi.losslesscut
       Ref: app/no.mifi.losslesscut/x86_64/stable
      Arch: x86_64
    Branch: stable
Collection: org.flathub.Stable
  Download: 101.9*MB
 Installed: 274.0*MB
   [COLOR="#FF0000"]Runtime: org.freedesktop.Platform/x86_64/21.08[/COLOR]

```

---

### Post by satimis on 2022-10-08
> **Dennis N said:**
> Don't forget about Flatpak:
```
losslessCut             Save space by quickly and losslessly trimming video and audio files    no.mifi.losslesscut                          3.45.0       stable    flathub
```

Especially attractive if you already have the necessary freedesktop runtime support already installed!

```
       ID: no.mifi.losslesscut
       Ref: app/no.mifi.losslesscut/x86_64/stable
      Arch: x86_64
    Branch: stable
Collection: org.flathub.Stable
  Download: 101.9*MB
 Installed: 274.0*MB
   [COLOR="#FF0000"]Runtime: org.freedesktop.Platform/x86_64/21.08[/COLOR]

```
Hi,

Thanks for your advice.

Testing it on Ubuntu22.04 VM

Installation is very simple just run on Terminal 2 commands;

```

$ sudo flatpak install flathub no.mifi.losslesscut
$ sudo flatpak run no.mifi.losslesscut

```

-> Open -> select a mp4 video

Now I can't figure out how to delete the black section, from starting point to the time-line.  Please see attached screenshot.

Pls help.  Thanks

Regards

---

### Post by satimis on 2022-10-08
Hi Dennis,

I found the solution:-

+/- signs on the right column = add/remove segments
the small figure at the left bottom corner - turn on advanced view

Pls refer to screenshots

Regards

---

### Post by Dennis N on 2022-10-08
First, a comment. In post #21, you show starting loslesscut with sudo. That's probably not a good idea, since I think all your files would then saved with root as owner. Also, you also didn't need sudo to intsall a flatpak. I can't say which of these cutters is better. I tried many at one time or another, and I haven't edited any video for awhile. OpenShot and Avidemux were the two applications I went with, but probably losslesscut is good too.

---

### Post by satimis on 2022-10-08
> **Dennis N said:**
> First, a comment. In post #21, you show starting loslesscut with sudo. That's probably not a good idea, since I think all your files would then saved with root as owner. Also, you also didn't need sudo to intsall a flatpak. I can't say which of these cutters is better. I tried many at one time or another, and I haven't edited any video for awhile. OpenShot and Avidemux were the two applications I went with, but probably losslesscut is good too.
#21
Shall I un-install it and install it again?

losslesscut is simple to use.

I have used OpenShot quite a lot but long time ago.  I already forgot the steps.  Yesterday I tried it but I couldn't do anything on the mp4 file after importing it.  Shall I convert mp4 to another format first before import?

Regards

---

### Post by Dennis N on 2022-10-08
I don't think you need to install it again. Yes, OpenShot is for more "advanced" work like making a single video out of several existing clips, adding transitions, titles, sound, special effects and so on. Tools like losslesscut and avidemux I would say are intended for simpler tasks cutting out things and trimming.

Also, If any of your work files ended up with root owner, of course you could remedy that with a chown command.

---

### Post by TheFu on 2022-10-08
> **Dennis N said:**
>  OpenShot and Avidemux were the two applications I went with, but probably losslesscut is good too.

If you don't want any transcoding, those two fail.  Same for all the big tools.  Every transcode loses quality.  If you have a 4K video and are going to reduce the resolution anyway, that matters less and less.  OTOH, if you intend to keep the same resolution, then it can matter greatly. 

Which is why I choose to transcode once and cut without any transcoding.  But we all have different needs.

Satimis, you should use whatever tool meets your needs. Each has things they do well and things they don't do well. Which is best for you is highly subjective.

---

### Post by satimis on 2022-10-08
> **Dennis N said:**
> I don't think you need to install it again. Yes, OpenShot is for more "advanced" work like making a single video out of several existing clips, adding transitions, titles, sound, special effects and so on. Tools like losslesscut and avidemux I would say are intended for simpler tasks cutting out things and trimming.

Also, If any of your work files ended up with root owner, of course you could remedy that with a chown command.
Hi Dennis,

Why I asked whether needing to reinstall LossLessCut ?

On folder -> right-click a mp4 file -> Other applications -> select LossLessCut

It asks to install LossLessCut

I must start LossLessCut first -> Open mp4 file

Regards

---

### Post by satimis on 2022-10-08
> **TheFu said:**
>  - snip -
Satimis, you should use whatever tool meets your needs. Each has things they do well and things they don't do well. Which is best for you is highly subjective.
Thanks for your advice.

OpenShot is more powerful and versatile.  I have run it long long time ago.  This time I only need to crop a mp4 file. LossLessCut can cater my needy.

I have OpenShot running on this VM.  When I started it

-> import mp4 file -> move the mp4 file to timeline

all worked without problem.  But I couldn't start the mp4 on timeline and then use the scissors to cut the sections which I don't need.

I don't know why? This OpenShot has been installed on this VM long time ago and I haven't run it for long time.

Regards

---

### Post by Dennis N on 2022-10-09
> **satimis said:**
> Why I asked whether needing to reinstall LossLessCut ? On folder -> right-click a mp4 file -> Other applications -> select LossLessCut
It asks to install LossLessCut. I must start LossLessCut first -> Open mp4 file
Regards

That's interesting. I tried right-click > Open with... > Avidemux and it launches Avidemux and opens an mp4 as expected. I noticed losslesscut on one of my other computers here - when I locate it, I will test it for that operation.

**_Update:_**
I checked losslesscut, and I can confirm what you say. It's not anywhere in the "open with" list. I had the same problem with ksnip and fixed ksnip, but the solution for ksnip did not work with losslesscut. It does place it in the "open with" list, but then "open with" just launches the losslesscut application, and does not open the desired file. All these are flatpaks, by the way.

Reinstalling losslesscut won't help. I don't have an answer to the "open with" problem for losslesscut, sorry.

---

### Post by ajgreeny on 2022-10-09
To get LosslessCut in the context menu all I needed to do was use the **right click -> Open With -> Open With Other Application** and then in the full list that appears choose LosslessCut.
From then on it appears in the short list from right click -> Open With.

PS:
I use Xubuntu with thunar file manager; perhaps other file managers work differently.

---

### Post by Dennis N on 2022-10-09
> **ajgreeny said:**
> To get LosslessCut in the context menu all I needed to do was use the **right click -> Open With -> Open With Other Application** and then in the full list that appears choose LosslessCut. From then on it appears in the short list from right click -> Open With.

Is your Losslesscut a Flatpak?
There could be a difference between .deb and flatpak behavior here.

---

### Post by #&amp;thj^% on 2022-10-09
Mine's a Flatpak, and was available in my menu, right after the install.
XFCE and Plasma DE's
```
flatpak install LosslessCut 
Looking for matches…
Found ref ‘app/no.mifi.losslesscut/x86_64/stable’ in remote ‘flathub’ (system).
Use this ref? [Y/n]: 
Required runtime for no.mifi.losslesscut/x86_64/stable (runtime/org.freedesktop.Platform/x86_64/21.08) found in remote flathub
Do you want to install it? [Y/n]: 

no.mifi.losslesscut permissions:
    ipc                   pulseaudio           x11      dri
    file access [1]       dbus access [2]

    [1] xdg-download, xdg-public-share, xdg-videos
    [2] org.freedesktop.Notifications


        ID                                        Branch Op Remote  Download
 1. [&#10003;] no.mifi.losslesscut.Locale                stable i  flathub   1.7*kB / 22.9*kB
 2. [&#10003;] org.freedesktop.Platform.GL.default       21.08  i  flathub 130.6*MB / 129.8*MB
 3. [&#10003;] org.freedesktop.Platform.GL.nvidia-515-76 1.4    i  flathub 366.1*MB / 365.7*MB
 4. [&#10003;] org.freedesktop.Platform.Locale           21.08  i  flathub  17.7*kB / 325.8*MB
 5. [&#10003;] org.freedesktop.Platform.openh264         2.0    i  flathub   1.5*MB / 1.5*MB
 6. [&#10003;] org.freedesktop.Platform                  21.08  i  flathub 206.5*MB / 200.4*MB
 7. [&#10003;] no.mifi.losslesscut                       stable i  flathub 105.2*MB / 101.9*MB

Installation complete.


```

---

### Post by Dennis N on 2022-10-09
> Mine's a Flatpak, and was available in my menu, right after the install.
XFCE and Plasma DE's
Satimis and I are using Gnome. Losslesscut is in the menu, or overview search, and no problem launching it, but the question is using the rt-click on media file and  "open with".

If you would test your Flatpak losslesscut and the "open with" menu, it would be informative. Thanks.

---

### Post by #&amp;thj^% on 2022-10-09
> **Dennis N said:**
> Satimis and I are using Gnome. Losslesscut is in the menu, or overview search, and no problem launching it, but the question is using the rt-click on media file and  "open with".

If you would test your Flatpak losslesscut and the "open with" menu, it would be informative. Thanks.

Sorry no Gnome here, but all i have to do is right click on the video and choose open with Losslesscut.
 @Dennis N can you see/test if this still works using the key combo <Super+Alt> then right click on your video.
FWIW you may need to install>> &#8220;Extension Manager&#8221; from Ubuntu Software. (On Jammy)

---

### Post by Dennis N on 2022-10-09
> i have to do is right click on the video and choose open with Losslesscut
In your image, losslesscut is there in the rt-click menu, but did you then open the selected file in lossless cut? I also have losslesscut as an option in the "Open with" menu, but that only starts the application without the selected file in it.
> test if this still works using the key combo <Super+Alt> then right click on your video.
Super-Alt (and holding) and clicking on lossless cut in "open with" makes no difference in the "open with" behavior. Same result as above.
> FWIW you may need to install>> &#8220;Extension Manager&#8221; from Ubuntu Software. 
It is already installed. What role does it play?

---

### Post by #&amp;thj^% on 2022-10-09
> **Dennis N said:**
> In your image, losslesscut is there in the rt-click menu, but did you then open the selected file in lossless cut? I also have losslesscut as an option in the "Open with" menu, but that only starts the application without the selected file in it.

Honestly, I've not used Gnome since Gnome 3, just play with it a bit.
But that sounds like a bug at first glance, mine on XCFE4 works as expected.
> **Dennis N said:**
> I
It is already installed. What role does it play?
It was touted as extension for preference's for the open with. But that not the problem I plainly see now.
Did ajgreeny's work right? I don't recall seeing that one.

---

### Post by #&amp;thj^% on 2022-10-09
OMG I forgot that the file it self has to be in your Downloads directory or Home, Videos. (For Flatpaks)
I've always set mine to Downloads.

---

### Post by Dennis N on 2022-10-09
I tested with the file in both Downloads and Videos. It makes no difference. 

Well, this problem which Satimis raised in #27 perhaps affects only Gnome (see update below), and at least this one Flatpak, although this is the first time I've seen it with any Flatpak in Gnome. I only pursued this because I was curious why it did not work properly - as I said earlier in this thread, lossless cut is not the simple cutter I have used - that's avidemux - and it's Flatpak works as one would expect.

And, I don't see it as a big issue, because once you right click on the file to be opened, select losslesscut from the "open with" menu, the application opens with a blank window and you just drag the file onto the window from file manager and it opens the file.

@satimis, if you want at least to have losslesscut listed in the "open with" menu, respond to this post and I can post instructions.
[B][U]
Update (1 day later)[/U][/B]
To see if other desktops besides Gnome are affected, I installed the Flatpak of losslesscut (LC) on Xubuntu 20.04 and Ubuntu MATE 20.04. The result was the same as with Gnome. With these flavors, LC was in the "Open With" menu but again only launched LC without the selected media file opening in it. So, based on my observations, I conclude the problem is with the LC Flatpak application and not the desktop environment in use.

---

### Post by ajgreeny on 2022-10-09
Sorry, I should have said in my post #30 that I am using the appimage of LosslessCut.

Whether or not it would make any difference I am not sure, but I have created a .desktop file for it which sits in /home/user/.local/share/applications so LosslessCut does appear in the Multimedia section of my Xubuntu menu system.

EDIT:
When I use the right click Open With my Lossless utility does indeed open with the file loaded ready for action, a d it does not matter where the mp4 file sits in my home, it sèms to open from anywhere in my home.

---

### Post by Dennis N on 2022-10-10
> **ajgreeny said:**
> When I use the right click Open With my Lossless utility does indeed open with the file loaded ready for action, a d it does not matter where the mp4 file sits in my home, it sèms to open from anywhere in my home.

Thanks for this information. It clarifies the extent of the problem. I have updated post #38 with results of my own tests using XFCE and MATE desktops.

---

### Post by TheFu on 2022-10-10
> **1fallen said:**
> OMG I forgot that the file it self has to be in your Downloads directory or Home, Videos. (For Flatpaks)
I've always set mine to Downloads.

Use the appimage and avoid all this crap from snap/flatpaks.  All our systems are a little different.  I routinely edit videos located on NFS storage mounted places that snaps hate.  Effectively, snaps are useless to me for almost anything that uses data.  

I'm fairly certain flatpak locations can be locally setup as needed. Think there's a GUI for that.

Or just use appimages instead.

---

### Post by #&amp;thj^% on 2022-10-10
> **TheFu said:**
> Use the appimage and avoid all this crap from snap/flatpaks.  All our systems are a little different.  I routinely edit videos located on NFS storage mounted places that snaps hate.  Effectively, snaps are useless to me for almost anything that uses data.  

I'm fairly certain flatpak locations can be locally setup as needed. Think there's a GUI for that.

Or just use appimages instead.

As usual I became curious with LosslessCut about the open with dialog.
It's been several months now since my last usage
Took the appimage and it segfaults on both Arch and SuseTumbleweed, Flatpaks all work fine for all I've tested now.
```
LosslessCut-linux-x86_64.AppImage' 

(losslesscut:420764): Gtk-WARNING **: 10:40:43.950: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(losslesscut:420764): Gtk-WARNING **: 10:40:43.956: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(losslesscut:420764): Gtk-WARNING **: 10:40:43.956: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(losslesscut:420764): Gtk-WARNING **: 10:40:43.957: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(losslesscut:420764): Gtk-WARNING **: 10:40:43.957: Theme parsing error: gtk.css:8318:24: negative values are not allowed.
CLI arguments { _: [] }
Current version 3.46.2
Newest version 3.46.2
[420764:1010/104046.895813:FATAL:gpu_data_manager_impl_private.cc(1034)] The display compositor is frequently crashing. Goodbye.
Trace/breakpoint trap (core dumped)


```
**But I need to correct my statement on open with a video.**
Turns out it just open's LosslessCut blank, and confirm you have to drag a drop your desired video for editing.
Apologies for any confusion on this subject. (The developer has limitations due to some OS's like Mac/Apple)
I would agree with the crap statement on Snaps, but I prefer and use Flatpaks...;)

---

### Post by #&amp;thj^% on 2022-10-13
Just for clarity, Electron is the culprit here for some OS's Arch, Suse, Fedora, and yes reports for 22.10 as well
For my appimage I'll run it un-sandboxed IE:
```
LosslessCut-linux-x86_64.AppImage --no-sandbox
```
For convince I made an alias as follows:
```
alias llc="/home/me/LosslessCut-linux-x86_64.AppImage --no-sandbox"
```
and this works for the above mentioned systems.
```
 llc
CLI arguments { _: [], sandbox: false }
Current version 3.46.2
Newest version 3.46.2


```
Hope this helps someone.

---

### Post by TheFu on 2022-10-13
I'm confused.

I've never noticed that any AppImage is running inside a sandbox, unless I do it myself.  [https://appimage.github.io/Isolate/](https://appimage.github.io/Isolate/) seems to imply they have a separate tool for this. They do specifically mention firejail, the tool I use for isolation.

I have noticed some of the same things that others mention about LossLessCut.  About 6 months ago, I started using drag-n-drop to bring media files into the editor.  It was because the File-->Open dialog forgot the directory I was using, which is always some non-standard location, usually on the network.
Because I use both video and EDL files, this meant that twice per video, I had to go through the terrible File/Open GUI. Yuck.  I wasn't really using any file manager before then.  If the CLI interface supported specifying both a video and an EDL file as part of the startup, I wouldn't have changed.  Alas, the programmer seems stick in the point-n-click world.  

I'd also change the i/o keys for start/end cuts to be F3/F4.  Right hand should be for moving in the file. Left hand should be for editing/markers.

Any custom settings are forgotten between program launches.  Recorded TV here is TS mpeg2 with AC3 audio. For some reason, audio isn't support messages are displayed and there's a "make compatible" quick transcode for the audio to be able to hear it during edits.  There's a checkbox to set it, but that checkbox is cleared if the program is shutdown.  

Seems like a noob programming mistake not to have a specific config file somewhere to hold some settings like to always convert incompatible audio for edits, a list of favorite directories, preferred output locations, video containers and video/audio codecs.  All things that ffmpeg can do.  Plus a NEVER, EVER, transcode option, since that's the real killer app for this tool.  

While I'm complaining, I'd like to control the output file mask/name a bit.  The default is just too long for information that doesn't help in my workflow.  Give me retained segments as file-01.ext, file-02.ext, file-03.ext .... file-99.ext.  When I insert a cut, automatically inserting it into the cut list on the right correctly would be handy too.  I can see why creators would prefer the longer names, but that ain't me.  I'm tired of having a merged file that had 5 or 20 cuts only to discover that they were merged out of order.  Keep cuts in order by original video location would be a nice toggle.

A year ago, LossLessCut was just becoming usable and by Feb '22, it was able to replace a commercial tool I'd been using on Windows since 2006.  THAT is impressive. It isn't perfect, but it is better than nearly any other tools, including my custom scripts which can work from EDL files with start/end cut times using mkvmerge to create a merged video without all the junk.  Obviously, my scripts don't have a GUI and that is really handy to validate comskip markers.

---

### Post by #&amp;thj^% on 2022-10-13
> **TheFu said:**
>   

Seems like a noob programming mistake not to have a specific config file somewhere to hold some settings like to always convert incompatible audio for edits, a list of favorite directories, preferred output locations, video containers and video/audio codecs.  All things that ffmpeg can do.  Plus a NEVER, EVER, transcode option, since that's the real killer app for this tool.  



That's my thoughts as well, I was pushing his clam demeanor, So I backed off, and let him point to newer electron packages for being the cause.
And I have a work-around now until/if he/they fix it....
I also have a fan control  AppImage "ExtreneCooling4Linux" that needs root/admin and Sand Boxed. (I love Developers at times LOL)

Behold! AppImages are usually not verified by others. Follow these instructions only if you trust the developer of the software. Use at your own risk!

---

### Post by TheFu on 2022-10-13
> **1fallen said:**
> That's my thoughts as well, I was pushing his clam demeanor, So I backed off, and let him point to newer electron packages for being the cause.
And I have a work-around now until/if he/they fix it....
I also have a fan control  AppImage "ExtreneCooling4Linux" that needs root/admin and Sand Boxed. (I love Developers at times LOL)

Haven't never coded for any container or deployed using any of the all-in-one file methods (besides a self-extracting sh script), I don't know what the limitations of the AppImage tools are. Perhaps access to normal .dotfiles isn't possible?  For all the other great work done on the program, I find it hard to believe there isn't some good technical reason settings aren't saved between runs.

---

### Post by #&amp;thj^% on 2022-10-13
> **TheFu said:**
> Haven't never coded for any container or deployed using any of the all-in-one file methods (besides a self-extracting sh script), I don't know what the limitations of the AppImage tools are. Perhaps access to normal .dotfiles isn't possible? 

I'm just now starting to get a feel for that but..., I can say with certainty my coding skills are not at your level just yet.
> **TheFu said:**
>  For all the other great work done on the program, I find it hard to believe there isn't some good technical reason settings aren't saved between runs.

In a day or so I'll bring that to his attention, and agreed that's a much needed option.

---

### Post by TheFu on 2022-10-13
He added EDL support at my request, so I'm VERY thankful for that.

---

### Post by #&amp;thj^% on 2022-10-13
So am I, and Thanks to you for the request. (It certainly doesn't hurt giving a little verbal love to them from time to time)

---

### Post by satimis on 2022-10-13
Hi all,

Something strange happens here.  I can't remove the selected segment.

When clicking "End current segment at current time" the selected segment turns to red color, instead of black color.
(pls refer to screenshot_1_50.png)

Clicking "Remove segment_1" ("-" sign) the whole bar turns to red.
(pls refer to screenshot_2_50.png)

Pls help.  Thank in advance

Regards

---

### Post by TheFu on 2022-10-14
Colors of segments are random - at least to me.
Select the segment (either in the timeline or the list) and use the backspace to delete it.

---

### Post by satimis on 2022-10-14
> **TheFu said:**
> Colors of segments are random - at least to me.
Select the segment (either in the timeline or the list) and use the backspace to delete it.
Sorry I can't delete it using the backspace.  The whole timeline turns to red, similar to clicking the "-" sign -> "Remove segment 1"

Regards

---

### Post by TheFu on 2022-10-14
I edit using the "keep" toggle, not the "remove" toggle.  The ying-yang symbol toggles that setting.
 v3.46.2 is what I'm using today.

Don't know if any of that helps.  I just find it easier to have the "keep" segments highlighted.  The trash bin icons show what will be retained and what what be cut when the "Export" button gets pressed.

---

### Post by satimis on 2022-10-14
> **TheFu said:**
> I edit using the "keep" toggle, not the "remove" toggle.  The ying-yang symbol toggles that setting.
 v3.46.2 is what I'm using today.

Don't know if any of that helps.  I just find it easier to have the "keep" segments highlighted.  The trash bin icons show what will be retained and what what be cut when the "Export" button gets pressed.
My version 3.45.0

I couldn't find the tool "keep" toggle

Regards

---

