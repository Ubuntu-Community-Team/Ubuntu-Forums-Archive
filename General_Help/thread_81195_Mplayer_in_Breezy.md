---
title: "Mplayer in Breezy?"
date: 2005-10-23
forum: General Help
---

### Post by Luggy on 2005-10-23
From what dirt I have been able to dig up mplayer is availible via synaptic with Breezy, however when I search for it I can't find it.

Is there any repositories that I need to have inorder to get it? What repositories do I need now that I'm in Breezy to get myself the w32codecs?

---

### Post by Emerzen on 2005-10-23
Do you have the multiverse repositories available?  I believe that's where Mplayer is.  Here is a website that has Ubuntu deb's (as well as other packages) for win32codecs.  Just add the lines to Synaptic.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

Here's the Multiverse line you need:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted

---

### Post by Xian on 2005-10-24
[QUOTE=Luggy]What repositories do I need now that I'm in Breezy to get myself the w32codecs?[/QUOTE]
Add these lines to your /etc/apt/sources.list:

```
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
```

---

### Post by ikd69 on 2005-10-24
I have also found that the Ubuntu Guide (which is still at 5.04, but is working fine for 5.10 if you change the word hoary to breezy) has detailed instructions for setting up mplayer and w32 codecs.  You can find the guide at this [http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/") address.

Cheers,

IKD :smile:

---

### Post by 23meg on 2005-10-24
if i were you i'd get seethru's gtk2 build of mplayer mentioned in [this thread]("http://www.ubuntuforums.org/showthread.php?t=78037"); it looks a lot more handsome than the gtk original. see the last page of the thread for a .deb file.

---

### Post by Luggy on 2005-10-24
[QUOTE=23meg]if i were you i'd get seethru's gtk2 build of mplayer mentioned in [this thread]("http://www.ubuntuforums.org/showthread.php?t=78037"); it looks a lot more handsome than the gtk original. see the last page of the thread for a .deb file.[/QUOTE]

Actually I perfer the non-graphical version of mplayer. But thanks for the input.

I tried switching 'hoary' to 'breezy' when adding the extra repositories from the ubuntu guide but that didn't work. I believe that the repositiroes Xian suggested fixed the problem though.

---

### Post by andlinux21 on 2005-10-26
I got most of the add ons to install but the codecs are giving me the hardest times 

vegeta@dragonball:~$ sudo apt-get install libdivx4linux
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libdivx4linux
:confused:

---

