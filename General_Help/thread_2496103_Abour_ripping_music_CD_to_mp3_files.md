---
title: "Abour ripping music CD to mp3 files"
date: 2024-03-14
forum: General Help
---

### Post by satimis on 2024-03-14
Hi all.

Ubuntu 22.04 desktop

Please advise an ease and reliable way ripping music CD to mp3 files?

Thanks

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Just found;
How to Rip CDs From the Linux Command Line
[https://linuxconfig.org/how-to-rip-cds-from-the-linux-command-line](https://linuxconfig.org/how-to-rip-cds-from-the-linux-command-line)

Can I use it to rip all music tracks on music CD to .mp3 files

$ apt policy abcde```

abcde:
  Installed: (none)
  Candidate: 2.9.3-1
  Version table:
     2.9.3-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```
The package "abcde" is on repo

---

### Post by ajgreeny on 2024-03-14
Yes, abcde is the package to use.
Once set up with the configuration to suit the output you want, it is simply a case of putting a CD in the drive and then using terminal command **abcde**.
 It will then create your mp3, flac, or whatever else you chose, and do several filetype outputs simultaneously if you need more than just mp3.

---

### Post by satimis on 2024-03-14
> **ajgreeny said:**
> Yes, abcde is the package to use.
Once set up with the configuration to suit the output you want, it is simply a case of putting a CD in the drive and then using terminal command **abcde**.
 It will then create your mp3, flac, or whatever else you chose, and do several filetype outputs simultaneously if you need more than just mp3.
Hi@ajgreeny,

Thanks for your advice.

Is it possible to rip the whole music CD with one click?

Regards

---

### Post by satimis on 2024-03-14
Hi all,

The story behind my intention ripping music CD is below;

I have more than 500 music CDs and >90% are classical music, including Opera, from famous composers such as Beethoven, Mozart, Schubert, Tschaikowsky, Paganini, Rossini, Brahms etc.  The CDs can play in my home HiFi system without problem and with excellant sound quality.

The CDs are already not on the market.  If damaged they are not easy to replace even with money therefore I must make some precaution.  I can clone (burn) another 500 CD copies but storage may be my headache.

Another thought comes to my head is ripping all 500 CDs to computer.  Then I can burn them again on a new CD if any old CD damaged.

Comment and suggestion would be appreciated.


[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Just found following article which is quite interesting;

How to Rip CDs From the Linux Command Line
[https://linuxconfig.org/how-to-rip-cds-from-the-linux-command-line](https://linuxconfig.org/how-to-rip-cds-from-the-linux-command-line)

---

### Post by Dennis N on 2024-03-14
> Comment and suggestion would be appreciated.

Definitely you want to back them up to computer files. I did it maybe 20 years ago for my large CD collection. 

I would use a GUI application. I think it's much easier to set up the encoding parameters. No need to spend time consulting a man page.  All distros have one or more applications of the GUI type that handle the ripping and encoding. The underlying ripping and encoding libraries are the same. 

Ubuntu has several GUI applications in the Software Store that handle the ripping and encoding. I only have used Brasero. No problems with it.

My go-to application in the past was **grip**, but there no longer is a .deb for it - only .rpm packages (Fedora, Red Hat, OpenSuse). So if you have Fedora installed, you can get that as well.

if you are an audiophile and/or want best quality, use flac when encoding instead of mp3 or ogg. But the file sizes for flac will be larger. Many (me included) find mp3 or ogg with high-enough quality settings to be quite acceptable. For recording speech, lower quality settings in mp3 and ogg are good enough and save space.

---

### Post by TheFu on 2024-03-15
I use this:

```
#!/bin/bash

abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
      -j 4  -o flac,vorbis:"-q 6" -V -x
```

YMMV.

---

### Post by satimis on 2024-03-16
> **TheFu said:**
> I use this:

```
#!/bin/bash

abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
      -j 4  -o flac,vorbis:"-q 6" -V -x
```

Hi@TheFu,

1)
Is it the command line will rip the whole music CD to .mp3 files?

2)
If I create following folders for ripping my music CD;

~/MP3_ripped_on_CDs
~/MP3_ripped_on_CDs/CD-1
~/MP3_ripped_on_CDs/CD-2
~/MP3_ripped_on_CDs/CD-3
etc.

Then on Terminal, how to run your code?  Thanks

Regards

---

### Post by TheFu on 2024-03-16
1) Try it. What does it do?

2) explainshell.com - check it out. It will help greatly.

YMMV.  That means it works for my needs, but may not work for yours.  I think it is close to what you want, but only you can decide BY TRYING IT.

---

### Post by satimis on 2024-03-16
> **TheFu said:**
> 1) Try it. What does it do?

2) explainshell.com - check it out. It will help greatly.

YMMV.  That means it works for my needs, but may not work for yours.  I think it is close to what you want, but only you can decide BY TRYING IT.
HI@TheFu
Performed following steps;

1) create following folders
~/Music/MP3_ripped_on_CDs/CD-1

2) on Terminal run
$ cd ~/MP3_ripped_on_CDs/CD-1/

3)
$ abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
> -j 4  -o flac,vorbis:"-q 6" -V -x```

[ERROR] abcde: flac is not in your path.
[INFO] Define the full path to the executable if it exists on your system.
[INFO] Hint: sudo apt-get install flac

```

4)
$ sudo apt install flac

5)
Ran the command lines again

This time it worked, converting all tracks on the CD to .flac and .ogg files
```

01.Track_1-Track_1.flac
01.Track_1-Track_1.ogg
02.Track_1-Track_1.flac
02.Track_1-Track_1.ogg
03.Track_1-Track_1.flac
03.Track_1-Track_1.ogg
.....
......

```

There are 99 tracks on the CD.  After finished the CD was ejected automatically.

01.Track_1-Track_1.flac
and
01.Track_1-Track_1.ogg
are same files

**[COLOR="#FF0000"]Is there any way to convert all tracks to .mp3 files only.[/COLOR]**

Thanks

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Following command line can convert all .ogg files to .mp3 files
```

for i in *.ogg; do ffmpeg -i "$i" -acodec libmp3lame "${i%.*}.mp3"; done

```

Following solution is NOT an ideal one

```

for i in *.ogg; do ffmpeg -i "$i" -acodec libmp3lame "${i%.*}.mp3"; done
| rm *.ogg | rm *.flac

```

---

### Post by ajgreeny on 2024-03-16
You need to either add mp3 to the listed output in that command or if you don't need the flac or ogg files, just replace **flac ,vorbis** with mp3.
There will be a different quality reference needed for the mp3 files as a think that **-q 6** does not work for mp3s but I can't recall how it is done. A search should find that easily enough!

---

### Post by satimis on 2024-03-16
> **ajgreeny said:**
> You need to either add mp3 to the listed output in that command or if you don't need the flac or ogg files, just replace **flac ,vorbis** with mp3.
There will be a different quality reference needed for the mp3 files as a think that **-q 6** does not work for mp3s but I can't recall how it is done. A search should find that easily enough!
Thanks for your advice.

Performed following steps

$ abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
>  -j 4 -o mp3:"-q 6" -V -x```

[ERROR] abcde: eyeD3 is not in your path.
[INFO] Define the full path to the executable if it exists on your system.
[INFO] Hint: sudo apt-get install

```

To install python-eyed3
Ran;

$ sudo apt install dnf

$ sudo dnf install python-eyed3```

/usr/lib/python3/dist-packages/dnf/const.py:22: DeprecationWarning: The distutils package is deprecated and slated for removal in Python 3.12. Use setuptools or check PEP 632 for potential alternatives
  import distutils.sysconfig
/usr/lib/python3/dist-packages/dnf/const.py:22: DeprecationWarning: The distutils.sysconfig module is deprecated, use sysconfig instead
  import distutils.sysconfig
Unable to detect release version (use '--releasever' to specify release version)
Error: There are no enabled repositories in "/etc/yum.repos.d", "/etc/yum/repos.d", "/etc/distro.repos.d".

```

I suppose "abcde" not work for mp3 ?

Regards

---

### Post by Tadaen_Sylvermane on 2024-03-16
I know the cli is the way people want to go. I just rip them with Asunder and call it a day. No screwing around for the perfect combination of flags to pass. CLI is nearly always faster. But sometimes it isn't worth the effort imo. If you want mp3 don't forget to install the lame package as well.

Lack of lame might be why you can't encode mp3 btw.

---

### Post by satimis on 2024-03-16
> **Tadaen_Sylvermane said:**
> I know the cli is the way people want to go. I just rip them with Asunder and call it a day. No screwing around for the perfect combination of flags to pass. CLI is nearly always faster. But sometimes it isn't worth the effort imo. If you want mp3 don't forget to install the lame package as well.

Lack of lame might be why you can't encode mp3 btw.
Hi@Tadaen_Sylvermane

cli ?

Is it awscli ?

Regards

---

### Post by Tadaen_Sylvermane on 2024-03-16
command line. terminal based tools. most linux users in my experience try to do this for everything but sometimes it just isn't worth it. the gui can be quicker and save headaches in some cases. Not always, but quite often.

---

### Post by satimis on 2024-03-16
Hi all,

About storage of ripped mp3 files

1)
Hardware
I'll purchase a new WD SATA6 4TB megnetic drive.  Format: ext4 without OS installed. solely for storage.

Would SSD drive works better for this job?

2)
Data file of mp3 files.
I'll use LibreOffice Writer

Content detail:
CD Number : CD-001, CD-002, CD-003 etc 
Name of CD:
Name of music:
Name of composer:
Name of Orchestra/Band :
Player: name of violinist, pianist etc.
etc.

Comment and suggestion would be appreciated.

Regards

---

### Post by TheFu on 2024-03-16
> **ajgreeny said:**
> You need to either add mp3 to the listed output in that command or if you don't need the flac or ogg files, just replace **flac ,vorbis** with mp3.
There will be a different quality reference needed for the mp3 files as a think that **-q 6** does not work for mp3s but I can't recall how it is done. A search should find that easily enough!

Yep. I don't use mp3 files. 

They are inferior in quality to vorbis and I prefer patent-free codecs.  q=6 is 192 kbps in the vorbis world. My ears cannot tell the difference between that and lossless (flac) files.  For mp3, 256kbps is required, making for larger files.  AAC at 128-256kbps is nearly as good as vorbis audio. If you use apple stuff, you'll want that.  A few years ago, I found myself wanting better quality rips from my 1000+ music CDs.  Since I never wanted to go through that again, I decided that FLAC was required. It is lossless and can be converted to whatever the "next" great audio format that becomes available is.  Right now, for my needs, that's vorbis.  

I did some reading of audiophile tests for the different codecs.  My summary of what they decided is that these three are roughly equivalent in sound quality.
FLAC ~ 256kbps MP3 ~ 192kbps AAC ~ 192kbps Vorbis
That's ordered by file size. FLAC is huge even with the built-in compression.  Vorbis is the smallest for the quality.  AAC has the Apple problem that I never want to encourage.

Vorbis is included in nearly all hardware and all audio-capable browsers these days (and has been for years). It is also in every Android device and supports as many channels as you like.  ogg is the container. The older audio that was placed into ogg containers has been replaced by vorbis.

I find that great music is vastly diminished if 128kbps mp3 is used. It just loses so many details.  Perhaps if you only listen on a motorcycle going 90 kph, it wouldn't matter?

If you look at youtube streams, the highest quality are using VP9 for video and vorbis for audio.  Oddly, most of my playback devices don't like VP9 video, so I transcode to HEVC/h.265.  A year ago, I was using h.264 video because my playback devices weren't powerful enough to deal with decoding h.265.  A few raspberry pi4 media players and that's all solved .... though my 1 yr old Toshiba tablet can struggle with h.265 1080p video. 

I'd recommend keeping the FLAC files, so you don't need to touch audio CDs unless massive data loss happens.  These days with multi-TB HDDs, isn't like it was in the mid-1990s when 80MB HDDs were huge.

Oh and for audiobooks, I use q=2. That's about 64Kbps.  Those are basically the only 2 quality settings I use with Vorbis, 2 and 6.

The script I posted is just for abcde. I have another that creates directories and moves the resulting files around - for my needs. It also loops over discs and pulls CDDB data.  I do remember having to setup the CDDB access, somewhere, but don't have that information anymore.  I spent 5 minutes searching and didn't find it. Sorry.

BTW, ExplainShell would have answered the questions posted.

---

### Post by TheFu on 2024-03-16
> **satimis said:**
> Hi all,

About storage of ripped mp3 files

1)
Hardware
I'll purchase a new WD SATA6 4TB megnetic drive.  Format: ext4 without OS installed. solely for storage.

Would SSD drive works better for this job?

2)
Data file of mp3 files.
I'll use LibreOffice Writer

Content detail:
CD Number : CD-001, CD-002, CD-003 etc 
Name of CD:
Name of music:
Name of composer:
Name of Orchestra/Band :
Player: name of violinist, pianist etc.
etc.

Comment and suggestion would be appreciated.

Regards

ssds are faster when reading and writing files.  Whether that matters or not is a judgement.  I avoid using my SSDs for data processing like this to keep the temporary writes to a minimum, extending the life of the SSD.  If I'm ripping and transcoding, it happens in batch, so I don't mind batch processing overnight.  Last night my system was transcoding about 4 1080 recordings.  I don't care that it took 8 hrs. I was asleep.

For tagging, **abcde** should handle it, assuming you have the CDDB setup correctly.
Keep all information in the ID3 tags which are part of the audio file - mp3, aac, vorbis all support tags.  **EasyTag** is the GUI took for this, if you don't have it automatically entered using abcde.  There must be 20 fields for the stuff you want included. EasyTag. Definitely.  Don't forget to "save" after you make changes. Multi-select to set fields with data shared by hundreds of files at the same time is great.

---

### Post by satimis on 2024-03-16
Hi all,

How to run "abcde" gui ?

Regards

---

### Post by monkeybrain20122 on 2024-03-16
> **satimis said:**
> Hi all,

How to run "abcde" gui ?

Regards

I don't know about abcde, it sounds complicated (i didn't really read the thread, just scanned it). When I had a cd rom I used to use k3b, intuitive gui, choose your output format from menu,  and one click, look at the progress bar, finish, you are done. It is in the repo.

---

### Post by #&amp;thj^% on 2024-03-16
abcde has no GUI, it is all cli or scripting.

TheFu and i use the same script I can See. ;)
```
tac /home/me/ripcd 
      -j 4  -o flac,vorbis:"-q 6" -V -x
abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \

#!/bin/bash

```

---

### Post by ajgreeny on 2024-03-16
> **monkeybrain20122 said:**
> I don't know about abcde, it sounds complicated (i didn't really read the thread, just scanned it). When I had a cd rom I used to use k3b, intuitive gui, choose your output format from menu,  and one click, look at the progress bar, finish, you are done. It is in the repo.
It may sound complicated but once you have the configuration file setup as you want depending on where you want the ripped files to be placed,and the filetype you need, it is simply command ***abcde*** and it all works in the background.
Couldn't be easier!

There is a very long but excellent thread [https://ubuntuforums.org/showthread.php?t=2257705](https://ubuntuforums.org/showthread.php?t=2257705) which is possibly worth plodding through, especially the more recent posts, though the early one taught me a lot about setting it up in the first place.

---

### Post by TheFu on 2024-03-16
> **1fallen said:**
>  
TheFu and i use the same script I can See. ;)
```
tac /home/me/ripcd 
      -j 4  -o flac,vorbis:"-q 6" -V -x
abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \


```

Taking what someone else has mastered is the sign of wisdom.  I don't remember if I created it or you did, but either way - -thank you or you're welcome! ;)  I steal lots of other smart people's scripts ... or at least the core parts if the whole thing doesn't work for me.

I can't imagine someone using Linux more than 5 yrs, not being comfortable with 20 line scripts and knowing where to find all the options for every command. Boggles my mind.  I suppose, lots of people don't change their car oil either.  I know how, but since the oil and the service are only $10 difference, I can't see why I'd waste my time doing it and having to clean up and find a legal place to dispose of the used oil.  We all trade money for effort, so there's nothing wrong with paying someone else to do things we don't know or don't choose to do ourselves, assuming we have the cash.

---

### Post by #&amp;thj^% on 2024-03-16
That has been so long ago that I can't even remember who helped with that.
mc4man and andrew.46 got my curiosity to peak so long ago, But i will here and now **Thank You** for other Scripts I've Gleamed from you over the years .

---

### Post by TheFu on 2024-03-16
BTW, your **tac** abuse is pretty high.  Aiming to confuse me?

---

### Post by #&amp;thj^% on 2024-03-16
Now that would be a feat to confuse you?

It's a habit I picked up a short while ago, and just for you I'll correct that to "cat" :)

---

### Post by monkeybrain20122 on 2024-03-16
> **ajgreeny said:**
> It may sound complicated but once you have the configuration file setup as you want depending on where you want the ripped files to be placed,and the filetype you need, it is simply command ***abcde*** and it all works in the background.
Couldn't be easier!

There is a very long but excellent thread [https://ubuntuforums.org/showthread.php?t=2257705](https://ubuntuforums.org/showthread.php?t=2257705) which is possibly worth plodding through, especially the more recent posts, though the early one taught me a lot about setting it up in the first place.

I no longer have a CD rom or listen to CD (or watch DVD). I have enough music between spotify and live performance. So it doesn't concern me.

I have made a dozen of scripts for various purposes and compile some programs from source if I need certain extra features or can't find pre-compiled, up to date version somewhere. I am a programmer and data analyst. So I am sure I could figure our how to use a command line tool to rip CD if I so desire. 

But to me it is just unnecessarily arcane when you have nice gui tools around. I and probably OP would have better things to do than learning/memorizing a bunch of cryptic commands and options and/or cut and paste to make a script from somewhere that I would have to further RTFM to figure what those options and all the -x -y --oktp --LOL means. Thank you very much but I don't need to write or use command line to watch a video or rip a CD, it is 2024, not 1994 . If I were one of those people who think only command line wizards should use Linux I wouldn't be using Ubuntu (I am not saying you)

Also as a rule if a new user asks about how to do certain things, I would always tell them the gui way if possible. No need to intimidate new people with a wall of cryptic commands that looks like some magic incantation. I have seen some experienced users delight in doing that  and without ever even explaining what those commands do or mean 

(I am not talking about you, be rest assured, You are always very helpful to new and old user alike, sorry if I sound harsh)

So my recommendation to OP is still k3b. Use the easiest way to get the job done. Use your time and intelligence for something more interesting and important.

---

### Post by TheFu on 2024-03-16
> **1fallen said:**
>  It's a habit I picked up a short while ago, and just for you I'll correct that to "cat" :)

I get confused all the time, like at the bottom of the stairs, trying to remember why I walked down them.

**cat**?  How about **less**? Something useful.  *cat* is pretty useless 99% of the time.  Wish the Unix books would stop showing it.

---

### Post by oldfred on 2024-03-16
I like following threads like this, I find a new script to add to my script folder.
I cannot remember most commands unless I use them daily. I either have a script file or details in my Zim notes files.

But years ago I ripped my Music CD/DVDs to FLAC. Back then I only had an MP3 player but wanted files in the better quality on system for future use.

I used GUI tools, Sound Juicer to rip CDs and Sound converter to convert FLAC to MP3. Both Gnome based, but I use Kubuntu now.
And for whatever reason back then, converting directly to MP3 player from Sound Converter wrote files much faster than converting on HDD and then writing to MP3 player.

I do prefer K3B for writing to CD/DVDs.

---

### Post by HermanAB on 2024-03-17
Here is the complete answer to the original question:
[https://askubuntu.com/questions/1881/what-are-some-cd-ripping-programs-you-can-use-on-ubuntu#1887](https://askubuntu.com/questions/1881/what-are-some-cd-ripping-programs-you-can-use-on-ubuntu#1887)

---

### Post by satimis on 2024-03-18
> **HermanAB said:**
> Here is the complete answer to the original question:
[https://askubuntu.com/questions/1881/what-are-some-cd-ripping-programs-you-can-use-on-ubuntu#1887](https://askubuntu.com/questions/1881/what-are-some-cd-ripping-programs-you-can-use-on-ubuntu#1887)
Hi@HermanAB,

Thanks for your link.

I'll test sound-juicer later.  It is on REPO

The amazing feature of "abcde" is ONE command line ripping complete CD.  It is not ripping the tracks, one-by-one

Regards

---

### Post by Dennis N on 2024-03-18
First, a correction about the GUI program **Brasero** that I mentioned. I had forgotten that it's a burner, not a ripper. It burns CDs or DVDs from existing files, both audio/video files or just data. 
 
The GUI programs that do ripping will have check boxes to select which tracks you want to rip and encode and the ripping of selected tracks is automatic. Asunder and Sound Juicer are rippers. The image below is Asunder - 2 tracks have been deselected.

You need to test these programs and decide what you like.

---

### Post by monkeybrain20122 on 2024-03-18
> **satimis said:**
> Hi@HermanAB,

Thanks for your link.

I'll test sound-juicer later.  It is on REPO

The amazing feature of "abcde" is ONE command line ripping complete CD.  It is not ripping the tracks, one-by-one

Regards

That is not a full list. In my experience k3b is the best full feature ripper/burner, it is in repo.
[https://apps.kde.org/k3b/](https://apps.kde.org/k3b/)

---

### Post by Dennis N on 2024-03-18
The thing about **k3b** for GNOME users that might give pause is that it is a KDE application, not GTK so you need a lot of additional packages to support it. A simulation on my Ubuntu 23.10 shows I would need to install **178 new packages**, to wit:

```
dmn@tyana:~$ apt install -s k3b
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
[list of new packages omitted]
0 upgraded, [COLOR="#FF0000"]178 newly installed[/COLOR], 0 to remove and 9 not upgraded. 
```

Installing **Asunder** on my Ubuntu 23.10 requires only 8 new pakages.

So Gnome users should keep this in mind.

---

### Post by TheFu on 2024-03-18
> **Dennis N said:**
> The thing about **k3b** for GNOME users that might give pause is that it is a KDE application, not GTK so you need a lot of additional packages to support it. A simulation on my Ubuntu 23.10 shows I would need to install **178 new packages**, to wit:
 

That is always a key consideration for me. Some Gnome tools also have huge lists of dependencies.  If there's more than about 20, I usually say "no" and seek out some other solution.  For packages with huge numbers of dependencies, I'll look for an AppImage, never a snap nor a flatpak.  I prefer to add my own constraints, not have them dictated at me.  The firefox snap being the default was sufficient for me to switch distros on my desktop away from Ubuntu to a distro that allows snaps, but doesn't effectively mandate them.  

I have an ongoing battle with bloat.  I've been a Linux user long enough to remember running a full OS in a 4MB RAM setup, with X11!  For **online banking**, I still use a minimalist ISO that needs under 80MB to run.

Having too many dependencies in a packaging system adds risks for ending up in "apt-hell".  Of all the issues I have with Ubuntu, that's the one that isn't too hard to avoid through careful consideration of dependencies and by avoiding fringe package installs from outside the core repos and I definitely avoid .deb file direct installations.

There are certainly times with a full bloat desktop is helpful too, just not most of the time, for me.

---

### Post by MAFoElffen on 2024-03-18
While adding more to look at:
[RubyRipper]("https://github.com/bleskodev/rubyripper")
[soundKonverter]("https://github.com/dfaust/soundkonverter/wiki")

---

### Post by satimis on 2024-03-19
Hi all,

Lot of thanks for your suggestions.

My ultimate need is to duplicate/clone all .wav files on all tracks of the CDs to desktop computer in the same format.  Should any CD be damaged, I can burn a new CD, all tracks of the damaged CD.

I'm interested testing all your suggestions but I wouldn't do it on the host of my desktop PC.  I'm running Oracle VirtualBox on Ubuntu 22.04.  But forwarding DVD-writer to the VM may be my problem which I have encountered in the past.  Bare-metal hard drive is the best solution but I need a spare SSD/Megnetic hard-drive to proceed.

Regards

---

### Post by andrew.46 on 2024-03-19
> **ajgreeny said:**
> There is a very long but excellent thread [https://ubuntuforums.org/showthread.php?t=2257705](https://ubuntuforums.org/showthread.php?t=2257705) which is possibly worth plodding through, especially the more recent posts, though the early one taught me a lot about setting it up in the first place.

That was indeed a good guy who started that long thread :)

---

### Post by ajgreeny on 2024-03-19
> **andrew.46 said:**
> That was indeed a good guy who started that long thread :)
Yes indeed it was!
Now, what was his name? I think it was andrew46!  Where have I seen that name recently?
:lolflag:

---

### Post by satimis on 2024-03-19
Hi all,

I found an easy solution to satisfy my need, copying all files of all tracks on CD to computer.

Steps:-
1) Create following folders
$ sudo mkdir ~/Music/CD-Folders
$ sudo mkdir ~/Music/CD-Folders/CD-001
CD-002
CD-003
etc.

2) change owner
$ sudo chown username:username -R ~/Music/CD-Folders/CD-001
etc

3) Insert and mount the music CD

4) Start File-manager for both folders and 'Audio Disc'

5) Copy and paste all tracks on CD-Folder.

That is all.  Very easy, no software is required.

I couldn't find the path of the mounted 'Audio Disc' on Terminal.  Can any folk help?

Thanks

Regardcs

---

### Post by TheFu on 2024-03-19
If you don't use sudo, it will just work without all the chown crap.  

Don't abuse sudo.

You can't just copy tracks from a music CD to a computer directory. They are stored in different formats.  A tool is required ... er ... like a CD ripper ... abcde.

---

### Post by Dennis N on 2024-03-19
> My ultimate need is to duplicate/clone all .wav files on all tracks of the CDs to desktop computer in the same format.
If your CD has .wav files that you can access with Files, then it is a data CD not an audio CD. Data CDs have a file system structure (like a disk drive) which can be mounted, read and copied by the file manager. Audio CDs can't be read by the file manager. 

So a CD with music (which you called a "music CD") can be a data CD or an audio CD. Everyone assumed yours were audio CDs. 

Still, even a data CD requires a burner program to store information on it. You can't do it with Files. And you can't rip a data CD.

CDs of music that you buy in a store are audio CDs.

---

### Post by satimis on 2024-03-19
> **TheFu said:**
>  - snip -

You can't just copy tracks from a music CD to a computer directory. They are stored in different formats.  A tool is required ... er ... like a CD ripper ... abcde.
Yes, the exact format .wav as on CD.

I can play all of them on computer without problem.  This way of operation makes my work much easier.  Wonderful.

---

### Post by satimis on 2024-03-19
> **Dennis N said:**
> If your CD has .wav files that you can access with Files, then it is a data CD not an audio CD. Data CDs have a file system structure (like a disk drive) which can be mounted, read and copied by the file manager. Audio CDs can't be read by the file manager. 

So a CD with music (which you called a "music CD") can be a data CD or an audio CD. Everyone assumed yours were audio CDs. 

Still, even a data CD requires a burner program to store information on it. You can't do it with Files. And you can't rip a data CD.

CDs of music that you buy in a store are audio CDs.
I can convert the .wav file to .mp3 file running
```

$ ffmpeg -i Track-1.wav -vn -ar 44100 -ac 2 -b:a 192k Track-1.mp3

```

the size of file reduced from 55.1MB to 7.5MB

Both .wav file (download) and .mp3 file (converted) can be played on VLC media player

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
my late discovery, downloading audio files to computer on the stock of my music CD will help me in building photo-slideshow to search background music on Internet.

My next adventure is how to create a database for easy searching on the stock of the download audio files?

---

### Post by TheFu on 2024-03-19
FLAC [https://en.wikipedia.org/wiki/FLAC](https://en.wikipedia.org/wiki/FLAC) is a lossless audio format and should be playable by many audio players. FLAC is a compressed WAV.
Apple has their own lossless audio file format too.

I'll leave it to you to decide if the compression from WAV --> FLAC is worth using it.  FLAC **is** the lossless standard and has been over 20 yrs.

---

### Post by satimis on 2024-03-19
> **TheFu said:**
>  - snip -

I'll leave it to you to decide if the compression from WAV --> FLAC is worth using it.  FLAC **is** the lossless standard and has been over 20 yrs.
Thanks for your advice.

If I need the copied music CD  files in .flac format, I just run your command on your previous posting with "abcde", not nessary downloading .wav files and then converting them to .flac format.

Actually time is my most concerned.  Copying >500 music CDs it would take me lengthy time to finish.  Storage is not my concern.  I have old WD magnetic hard-drives standing idle

WD STAT3 magnetic drives available:
2 x 2TB SATA3 drives
1 x 1.5TB SATA3 drive

Not sufficient?  I still have a 4TB SATA6  WD magnetic drive which was used for transfering data between my PCs.  It is now standing idly on its dock.  I'm now running an USB 2TB external SSD for data transferring between PCs.

I won't install those WD magnetic drives inside PC.  I just connet them outside PC with long cables.  If space full then I change another drive.  It is very convenient.

I'm now on my daily working PC.  I'll come back later when running my spare PC.  I need to find out if mounting the DVD-Writer GUI I couldn't find its mount point on Terminal.  WHY!!!

Regard

---

### Post by TheFu on 2024-03-20
> **satimis said:**
> Thanks for your advice.

If I need the copied music CD  files in .flac format, I just run your command on your previous posting with "abcde", not nessary downloading .wav files and then converting them to .flac format.

Actually time is my most concerned.  Copying >500 music CDs it would take me lengthy time to finish.  Storage is not my concern.  I have old WD magnetic hard-drives standing idle

WD STAT3 magnetic drives available:
2 x 2TB SATA3 drives
1 x 1.5TB SATA3 drive

Not sufficient?  I still have a 4TB SATA6  WD magnetic drive which was used for transfering data between my PCs.  It is now standing idly on its dock.  I'm now running an USB 2TB external SSD for data transferring between PCs.

I won't install those WD magnetic drives inside PC.  I just connet them outside PC with long cables.  If space full then I change another drive.  It is very convenient.

I'm now on my daily working PC.  I'll come back later when running my spare PC.  I need to find out if mounting the DVD-Writer GUI I couldn't find its mount point on Terminal.  WHY!!!

Regard

Think my ensite 1000+ disc music collection is under 500GB with FLAC and Vorbis versions.
```
$ sudo du -shc .
502G    .
502G    total
```
You can waste storage with WAV, if you like.  FLAC is all about storage efficiency for lossless audio and compatibility.  From FLAC, it is easy to conver to whatever format, at whatever quality, we might need.  FLAC is like having the ISO, but without risking the scratches.

Working on 500 discs is like eating an elephant.  Just need to do it 1 bite at a time and be consistent.  I think you have a fast Ryzen, so the slowest part will be ripping the discs.  In the 1990s, that was 45 minutes. I think now it is just 5 minutes since disc speeds are 32x.  Last time I did it, I setup a batch script to eject the disk when it was finished. I'd be working on other things, the disc would be ejected, I'd swap in the next one, hit <enter> and get back to working.  Doing that a few hours a day gets through 40+ discs/day .... 400 in 2 weeks.  900 in a month.  A little at a time, until completed.  

At the same time, I reorganized the collection in the disc holders so the same genres were together and the same artist albums were all together, in release order too.  Most of us don't have a single disc holder for all our discs.  I have 3+ and each is a little different.  Plus massive collections like Clapton's Crossroads don't fit into any disc holder I've seen.

Well, I've imparted all I think I know about this at this point. Good luck.

---

### Post by satimis on 2024-03-20
Hi@TheFu.

Just made following test on my spare desktop PC

**[COLOR="#FF0000"]Configuration:[/COLOR]**
AMD Ryzen5 8-core CPU
RAM 32G  DDR3
Hard disk - 2TB SATA3 SSD

Time copying all tracks .wav files on CD to hard disk with drag-n-drop is 1 min and 12 seconds.  It is very fast.

Total file sizes of 7 tracks = 429.9 MB

I won't play the .wav files on computer.  They are ONLY the backup of my CDs.

I only play music CDs on my HiFi system with floor-stand loudspeakers and subwoofer

Regards

---

### Post by dragonfly41 on 2024-03-20
This discussion (on audio) and related discussion (on photos) triggered  thoughts on how to process hundreds of files scattered throughout my desktop and various separate media (SSD, HDD and other). Perhaps not audio, and certainly images but the broad principles apply to all file types.
In a word .. automation.
That is, how to run through file types and process them automatically (addressing the point raised in this thread about the time taken).
What I have now mocked up is a workflow using Recoll as the indexing engine.
After a full indexing in Recoll (which will take time for first pass) we can use the Query Language form to identify extensions. Example ext:mp3 but compound queries can be crafted.
Right clicking on any selected file we can open it in selected application such as Shotcut. So far, so good.
But the interesting challenge is to automate the processes applied to selected files. My interest is other mime types but the same approach applies to audio, video, images, docs, scripts.
I build a custom app (desktop file) placed in /usr/share/applications/
```
sudo -H ls  /usr/share/applications/
```
Then custom scripts can be applied through xdg-open protocol to each selected Recoll indexed file.
I offer this "work in progress idea" to address the elephant in the room automation, and the time taken to process hundreds of documents. Of course if we are discussing inserting and removing DVD's the automation has to be suspended for manual DVD change. But otherwise the entire process can be automated perhaps in a server.
One example is trawling through Thunderbird archives.
As part of this thinking, Recoll files will be selected and cycled through a front end script written in Actiona or other GUI. This will "drive" the Recoll UI with different automation rules applied. My current target is trawling through many CherryTree documents (XML format) into which various objects are embedded.  I search ext:cbt. Then a script parses the XML elements (which could contain photos, audio, video, code).
Hover the cursor over the Recoll Query Language field for a few seconds to see a Cheat Sheet popup with query examples.

---

### Post by satimis on 2024-03-21
[COLOR="#FF0000"]**Further to my post #47 above**[/COLOR]

Now I work in following way to duplicate music CD .wav files to computer

1)
Create CD folders on the storage drive

2)
Insert and start a CD

3)
Use drag-n-drop copying music .wav files on corresponding folder

4)
Create a .txt file puting following data on it
4a) CD number
4b) Name of CD (Name of the music title)
4c) Composer

This .txt file is for me to make search.

5)
Put the CDs on CD shelves according to their number
[B][COLOR="#FF0000"][SIZE=4]
Computer is multi-tasking.[/SIZE][/COLOR][/B]  I copy CDs .wav files to folder while I perform other jobs.  I just check the progress periodically. It is very convenient to me.

Alternatively I can check the LED light of DVD-Writer.  If it stops that signifies the copying finished.

Regards

---

### Post by dragonfly41 on 2024-03-21
Then I suggest that you will find Recoll to be useful .. later .. *after* your manual ripfest .. to index your 500 folders containing media objects and metadata. Helper files in Recoll can route to workflows. Just a thought. My task is different from yours. Basically acting as a "breaker's yard" to deconstruct old documents and rebuild in different containers such as Scribus or presentations. But also audio and video clips might be grabbed from the "breaker's yard". All part of the recycling drive. Automation is key.

P.S. I last dabbled with HiFi in the days of Tobey-Dinsdale.  Jack Dinsdale was a work colleague.

---

### Post by satimis on 2024-03-21
Hi all,

Now I have copied the .wav audio files of 32 music CDs on the 1.5TB WD magnetic hard drive.  The storage space used is 23G.

23 divided by 32CDs = 0.71875G

for 500 music CDs
0.71875 x 500 = 359.375G

i.e. about 360G storage space is required.

Actually the duplication with drag-n-drop is quite fast.  Neither I need checking the progress of copying files periodically.  I just occasionally check the LED light of the DVD writer.  If it stops flashing, it indicates the duplication of audio files to computer finished.

Regards

---

