---
title: "ATI TV-out help"
date: 2006-11-03
forum: General Help
---

### Post by bluemerle27 on 2006-11-03
I am trying to set up tv out in ubuntu. I have a ATI 9700 card that supports tv out. I am sure I should edit the xorg.conf file somehow I think but would apreciate any help with this as dont rally know what to edit in the file. btw tryed the atitvout program and did not work

---

### Post by reclusivemonkey on 2006-11-03
> **bluemerle27 said:**
> I am trying to set up tv out in ubuntu. I have a ATI 9700 card that supports tv out. I am sure I should edit the xorg.conf file somehow I think but would apreciate any help with this as dont rally know what to edit in the file. btw tryed the atitvout program and did not work

This may help, although its for NVIDIA;

[http://ubuntuforums.org/showthread.php?t=271344](http://ubuntuforums.org/showthread.php?t=271344)

---

### Post by jocko on 2006-11-03
> **bluemerle27 said:**
> I am trying to set up tv out in ubuntu. I have a ATI 9700 card that supports tv out. I am sure I should edit the xorg.conf file somehow I think but would apreciate any help with this as dont rally know what to edit in the file. btw tryed the atitvout program and did not work

Which drivers are you using? The open source drivers don't support tv out.

---

### Post by bluemerle27 on 2006-11-03
latest ati drivers from the ati website. installed via the instruction in ubuntu ati wiki site. have upgraded to edgy to btw. 8-30-1 or something i thing they were called.

---

### Post by jocko on 2006-11-04
[SIZE=3]try this:
```
sudo aticonfig --tvf=[COLOR=Blue]**PAL-B**[/COLOR] --tvs=[COLOR=Blue]**VIDEO**[/COLOR] --force-monitor=**[COLOR=Blue]tv[/COLOR]**
```[/SIZE][SIZE=3]
The "VIDEO" will output as s-video. Change "PAL-B" to whatever format is standard in latvia. If you run 'aticonfig' without any options you will get information on the available options.
[/SIZE]

---

### Post by bluemerle27 on 2006-11-05
thanks very much, that worked perfectly. just have to fiddle with reolutions to get it working out of tv but great. Thanks again. that was the last thing that i needed to make a full migration to ubuntu from windows

---

### Post by McLite on 2006-11-09
Thanks Jocko, that line worked great for me (just replaced **PAL-B** with **NTSC-M**).

What is with the black boxes with minimizing windows with fglrx?  Any way to get rid of those?

---

