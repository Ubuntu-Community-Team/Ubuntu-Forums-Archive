---
title: "Fuzzy Icons in Ubuntu Software Center"
date: 2012-11-20
forum: General Help
---

### Post by Dstep038 on 2012-11-20
Hey there when ever I go into the software centre my icons and text look like this.
[IMG]http://img585.imageshack.us/img585/5715/screenshotfrom201211192d.png[/IMG]

Any Ideas?

---

### Post by Magatame on 2012-11-22
I also get this, any fix on it?

---

### Post by Impavidus on 2012-11-23
It looks like a buggy graphics driver.

GUI programs often produce pixel maps stored in video memory and somehow these pixel maps got scrambled. I once had the problem of my skewed scaled-down wallpaper replacing the small cloud icon of my weather monitor whenever I ran a flight simulator. Problems are more likely to occur when you use a lot of video memory.

Make sure you've got the correct graphics drivers. There are many threads on that (as it's one of the most occuring problems on Ubuntu). If you've got a very recent graphics card you may have to wait for some bug fixes.

---

### Post by Dstep038 on 2012-11-23
Thanks a lot for the help. I have an nvidia gtx570 so that may be the problem then.

---

### Post by Majlo on 2012-11-23
Hello,

I suspect you have nvidia card and using nouveau driver which is installed by default.
Install proprietary driver and this will fix the issue 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

