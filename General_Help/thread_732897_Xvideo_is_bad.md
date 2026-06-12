---
title: "Xvideo is bad"
date: 2008-03-23
forum: General Help
---

### Post by SuperBo on 2008-03-23
Before when I watch movie with xvideo, quality is very good.
But when I run smplayer with xv, image quality is very bad.
Since that time, the quality of image when play with xvideo is very bad.
How can I reset xvideo config.

---

### Post by rvm4000 on 2008-03-23
What does "quality is very bad" mean?

A very high contrast or something like that?

---

### Post by SuperBo on 2008-03-24
I think that is a very high constrast.

---

### Post by rvm4000 on 2008-03-24
When playing a file SMPlayer sets the brightness, contrast, hue... to 0, which supposedly would provide a normal image, but it seems it's not the case in some systems.

Edit the configuration file (~/.smplayer/smplayer.ini), look for **dont_use_eq_options** and set it to true. That way SMPlayer won't try to change those video settings (well, unless you change them in the video equalizer).

---

### Post by SuperBo on 2008-03-24
Thank you very much. I have fixed this error.
But when I play video with Smplayer, some time, it stop suddenly.

---

### Post by rvm4000 on 2008-03-24
Take a look at the mplayer log (Options->View logs) when that happens. Probably mplayer complains about something.

---

### Post by SuperBo on 2008-03-24
This is SMPlayer log file.
[http://www.box.net/shared/ih23evvkk8](http://www.box.net/shared/ih23evvkk8)

---

### Post by rvm4000 on 2008-03-24
This is a bug in mplayer. It crashes sometimes when it can't find a character in the font (for the subtitles).

The quick workaround is to disable the SSA/*** library in preferences. But I think this bug was already fixed in svn.

I've made some packages with recent versions from svn, maybe you can try:

[http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588](http://sourceforge.net/project/showfiles.php?group_id=185512&package_id=260588)

---

### Post by SuperBo on 2008-03-25
I have set "dont_use_eq=true". Then I try to change some equalizer, and now, xvideo quality is high contrast again.

---

### Post by rvm4000 on 2008-03-25
Adjust the contrast in the equalizer too until the image is good.

---

### Post by SuperBo on 2008-03-25
> **rvm4000 said:**
> Adjust the contrast in the equalizer too until the image is good.
Thank you very much. I use gxvattr to adjust xv setting. Now It's fine.:guitar::guitar:
When I install Mplayer svn, it inform that "conflicts with Mencoder". Do you have a suitable Mencoder package.

---

