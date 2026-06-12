---
title: "Shrinking video from 700mb to 100mb for web use"
date: 2007-09-05
forum: General Help
---

### Post by CameronCalver on 2007-09-05
Hello i have a small 40 minute dvd that i ripped with dvd:shrink but the smallest size i could do was 700mb so how do i shrink to 100 mb so i can use it to put on things like google video , youtube, myspace?

---

### Post by Hallvor on 2007-09-05
You could always transcode it with VLC if you have it installed.

[http://www.linux.com/articles/53757](http://www.linux.com/articles/53757)

---

### Post by Shin_Gouki2501 on 2007-09-05
Hello CameronCalver!
have u tried stage6.com?

---

### Post by CameronCalver on 2007-09-06
Hey i downloaded VLC how do i transcode the video with it?

---

### Post by Hallvor on 2007-09-06
> **CameronCalver said:**
> Hey i downloaded VLC how do i transcode the video with it?


Read this: [http://www.linux.com/articles/53757](http://www.linux.com/articles/53757)

---

### Post by southernman on 2007-09-06
I like to use mencoder for this type of work. If you can upload a sample for me to have a gander at... I'll see what sort of commands you need to use on the file to reduce it down and TRY to keep the quality as close to original.

---

### Post by CameronCalver on 2007-09-07
None of these are really working all i wanted was a program/script that will let me specify a amount of mbs and it will set the bit rates and so on and yeh.

---

### Post by Hallvor on 2007-09-07
Calculate it then (requires sun java):

[http://www.videohelp.com/calc.htm](http://www.videohelp.com/calc.htm)

It is not that hard.

---

### Post by CameronCalver on 2007-09-07
i dont get it man sorry i need a full guide from someone

---

### Post by fragos on 2007-09-07
I don't believe the programs mentions allow you to change file size by specifying a new file size.  You'll need to set the available parameters to values that have as a result a smaller file.  Take a look at [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html)

---

### Post by CameronCalver on 2007-09-07
Thanks im actually getting somewhere so now im getting ```
No audio encoder (-oac) selected. Select one (see -oac help) or use -nosound.

Exiting...

```
how do i fix this?

---

### Post by southernman on 2007-09-09
-oac copy

---

### Post by AnRa on 2007-09-09
You may try [Avidemux](http://packages.ubuntu.com/feisty/graphics/avidemux)! ;)

---

