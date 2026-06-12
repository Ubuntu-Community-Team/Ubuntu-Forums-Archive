---
title: "[SOLVED] rip copy-protected dvd for personal use"
date: 2008-05-05
forum: General Help
---

### Post by moore.bryan on 2008-05-05
i've attempted to use a number of different methods, but nothing seems to work... any suggestions for ripping a copy-protected dvd? i am **not** trying rip this to post anywhere on the internet; it is for educational showing in my classroom.

---

### Post by gwpritch on 2008-05-05
I've had a lot of success backing up my dvd's with a little script called XVIDENC which automates the usage of mencoder which comes with mplayer. You can google it. Works great to encode to .avi or other formats with excellent quality.

---

### Post by tamoneya on 2008-05-05
```
sudo apt-get install dvdrip
```Then look in applications -> sound and video -> dvd::rip

---

### Post by dashnak on 2008-05-05
I alway use [lemonrip]("http://jaromes.projects.googlepages.com/lemonrip.html").
It works great.

---

### Post by anaconda on 2008-05-05
I like k9copy

But also mencoder from the commandline is quite handy.

```
mencoder dvd://1 -vf scale=640:360 -o friends_season2.avi -alang en -slang en -vobsubout friends_season2 -oac copy -ovc lavc -lavcopts vcodec=mpeg4
```
(this would rip track 1 from dvd and take the english language (if many choises) and english subtitles to a separate file. (subtitles would work automagigally eg. in VLC videoplayer))

And if copy protection is your problem, then here is a link for instructions on how to install libdvdcss2
[https://help.ubuntu.com/community/RestrictedFormats?highlight=(restricted)#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats?highlight=(restricted)#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)
Copy protection is a problem only if you are unable to watch your DVD from ubuntu

---

### Post by retrow on 2008-05-05
IN addition to what others have suggested, a reason why you may not be able to unlock DVDs would be because of some missing codecs.

To cover all bases in terms of required codecs, add medibuntu repositories for your version of Ubuntu.
[Medibuntu Repositories](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

Once you add the repositories and the keys, run:
```
sudo apt-get update
sudo apt-get install libdvdcss2 libdvdread3-dev w32codecs ubuntu-restricted-extras msttcorefonts build-essential
```
This will allow you to use dvdrip, lemonrip etc. to their full potential.

---

### Post by moore.bryan on 2008-05-05
excellent suggestions from everyone...
> **gwpritch said:**
> XVIDENC
this is exactly what i was looking for... i'm in the process of ripping now; i'll let you know how it turns-out.
> **tamoneya said:**
> dvd::rip
this was the first one i tried and for my level of "ripping knowledge" and my needs, way too complicated and unnecessary. i mean, if i were some sort of professional pirate perhaps, but i'm just looking to back-up a single dvd...
> **dashnak said:**
> [lemonrip]("http://jaromes.projects.googlepages.com/lemonrip.html").
this is definitely something i'll have to look into... looks clean and easy.
> **anaconda said:**
> k9copy... mencoder from the commandline... libdvdcss2
tried k9copy, but kept getting errors... fooled around with mencoder straight, but couldn't get it to do exactly as i wanted. already installed libdvdcss2...
> **retrow said:**
> [Medibuntu Repositories]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
already made sure i hit these up... i'll report back if i run into any problems with the xvidenc script. i know it's just a front-end script for mencoder, but it seems to be working and my mencoder cli input was apparently sub-par.
thanks for all the great suggestions!

---

