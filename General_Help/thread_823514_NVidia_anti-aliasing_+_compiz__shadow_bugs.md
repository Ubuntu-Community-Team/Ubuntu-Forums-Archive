---
title: "NVidia anti-aliasing + compiz : shadow bugs"
date: 2008-06-09
forum: General Help
---

### Post by ®om on 2008-06-09
Hi,

I enabled antialiasing :
[img]http://images.imagup.com/03/1213014171_Capture.png[/img]

After setting these parameters :
```
nvidia-settings -l && compiz --replace&
```

Antialiasing works.

But now, there are a lot of bugs, especially for shadows and opacity :
video of the bug (play with vlc for example) : [http://dl.free.fr/bf3LQKMVL/aa-bug.mkv](http://dl.free.fr/bf3LQKMVL/aa-bug.mkv)

Is there a way to use antialiasing without having such bugs?

Thank you by advance

---

### Post by Nullack on 2008-06-10
Have you tried the latest nvidia driver? 173?

---

### Post by ®om on 2008-07-08
> **Nullack said:**
> Have you tried the latest nvidia driver? 173?

No, I haven't.
I use the package **nvidia-glx-new** (169.12) in ubuntu repositories.

Can anyone who have nvidia drivers v173 try to reproduce the problem, please?

---

### Post by flows on 2008-07-08
Some weeks ago, I tried it myself and had the same problem. I was just going for a second try :) In a moment, I'll post my results.

[Edit:]
Well, it's all the same with 169.12, Hardy 8.04.1 and an Nvidia 8400M GS. So far I haven't tried the new driver. Actually, I don't really want to try due to a stable system...
Another issue, by the way: Wobbly windows become VERY slow when activating AA. But this is probably due to the character of the plugin.

---

### Post by Spaz022765 on 2008-08-18
I am experiencing the same exact thing.. 
Been looking for a few weeks for a fix.

I'm using Hardy and the v173 nvidia drivers on an 8800gtx, installed by envyng. 

Anybody have any suggestions?:confused:

---

### Post by TheWiseNoob on 2009-04-22
I used the command

```
nvidia-settings -l && compiz --replace&
```in jaunty and now compiz won't load, as well as the rest of my desktop. Could somebody help me with a way to fix/reverse this?

---

### Post by TheWiseNoob on 2009-04-22
double post

---

