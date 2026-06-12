---
title: "CD emulating software problem"
date: 2007-02-25
forum: General Help
---

### Post by bone2006 on 2007-02-25
I have a cue/bin movie that I'm trying to watch, but the problem is that it's a format that I can't use mplayer to play it.  I tried installing cdemu, but it kept giving me an error.  I thoguht it was kernel related, but I tried a few version and it kept complaining about then I tried kiso and it opened up the cue/bin and it converted just fine.  When I tried to use Kiso to mount it, it crashed each time.

Kind of fustrating using alcohol software and daemon-tools in windows and trying to get something even remotely close in linux.

---

### Post by po0f on 2007-02-25
bone2006,

What problems are you having getting cdemu compiled?

---

### Post by chrome307 on 2007-02-25
Have you tried this ??

[B]
## AcetoneISO ##[/B]

This program from GUI can:

1) Mount and Unmount ISO and MDF(if iso-9660 standard)
2) Convert BIN/CUE, MDF, NRG, CCD/IMG, CDI, XBOX, B5I/BWI, PDI, DAA to ISO
3) Burn Your ISO, CUE, TOC images directly in K3b
4) Blank Your CD/DVD ReWritable
5) Verify md5sum of image files and Generate a Md5sum file from ISO
6) Ability to create ISO from Folder and CD/DVD
7) Service-Menu support
8) Play a DVD-Movie ISO with Kaffeine, Mplayer, VLC, Kmplayer
9) Split ISOs in smaller files and Merge them
10) Quick Turbo Mount an ISO file from your Desktop
11) Compress ISO with p7zip and extract
12) Encrypt and Decrypt an ISO
13) Generate a CUE file from a IMG/BIN image
14) Rip a PSX cd to a bin/toc image


[img]http://kde-apps.org/CONTENT/content-pre1/44805-1.png[/img]

[img]http://kde-apps.org/CONTENT/content-pre2/44805-2.png[/img]

[img]http://kde-apps.org/CONTENT/content-pre3/44805-3.png[/img]


Available here:

```


http://kde-apps.org/content/show.php?content=44805


```

---

### Post by bone2006 on 2007-02-25
At the make, this is what I get:


/cdemu-0.8$ make
/bin/sh: Syntax error: Bad fd number
Makefile:71: /untitled: No such file or directory
Makefile:71: folder/cdemu-0.8/mk/linux-2.6: No such file or directory
make: *** No rule to make target `folder/cdemu-0.8/mk/linux-2.6'.  Stop.

I deleted some of the user specific info above, but all I did was extract the contents, then while in the directroy when I type in maike that is what I'm getting above.  This is extracted on my desktop though

---

### Post by bone2006 on 2007-02-25
chrome307 I posted while you were probably posting, so I didn't see your post until now.

I never heard of that program, but I'll give it a try thanks for posting about it.
going to try it out now

---

### Post by bone2006 on 2007-02-26
I still had problems and this time converting wouldn't work.  I'll assume the image was corrupted.
I have to say that I am impressed with AcetoneISO, especially compared to the other options out there.  Thanks so much

---

### Post by thommo on 2007-03-10
please excuse my linux ignorance (I've only been away from Windows for a week), but does AcetoneISO being a KDE program mean I can't use it on an Ubuntu system?

---

### Post by SkiesOfAzel on 2007-03-23
You can use it in ubuntu, it's just going to load some kde libs in order to work, read [here]("http://www.acetoneteam.org/acetoneiso-gnome.html") for dependencies.

---

### Post by danieldumitru on 2008-04-28
Hy to all.
I have a problem with Acetoneiso2 on Hardy.
When i mount an image throw "Play DVD-Movie ISO" vlc is opening and gives this error "Unable to open '/home/danutz/virtual-drives/dvd'"
Anyone has any ideea?
Before installing codecs from mediubuntu vlc was able to play the image throw acetoneiso2.

---

