---
title: "Gnome/Hard Drive/System Issue"
date: 2008-01-25
forum: General Help
---

### Post by ikt on 2008-01-25
Hi all,

I have an issue with my Ubuntu 7.10 Desktop.

It will load up the ubuntu logo + progress bar fine, but then when it trys to load Gnome it gets stuck on the orange background, the hard drive is intensely working but I have left it for 6 hours and there was no progress.

I can load the latest kernal in recovery mode fine, is there anything I can do to try and fix it?

---

### Post by LaRoza on 2008-01-25
* When did this start
* What happened between when it worked and first started

---

### Post by ikt on 2008-01-25
> **LaRoza said:**
> * When did this start
* What happened between when it worked and first started

It happened about 48 hours ago.

As far as I know nothing significant changed, also as far as I know the computer was on in the back room when it must have automatically rebooted.

Is there anyway to see via recovery console/logs what happened?

---

### Post by LaRoza on 2008-01-25
Try reconfiguring the Video card, it may be the issue:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by ikt on 2008-01-25
> **LaRoza said:**
> Try reconfiguring the Video card, it may be the issue:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

I did that, then rebooted and selected the non-recovery version of ubuntu and it still did the same thing 

Rebooted and tried that command in recovery console again and then typed startx, still the same thing happened----edit: I left it a couple minutes and eventually it came up with the error box: Internal error: failed to initialize HAL!

---

### Post by ikt on 2008-01-25
*bump*

because i'm still in the exact same situation I was in when I made the first post.

---

### Post by muuwt1 on 2008-01-25
relax its only been an hour. and did it stop at the third bar on the load screen?

---

### Post by LaRoza on 2008-01-25
> **ikt said:**
> *bump*

because i'm still in the exact same situation I was in when I made the first post.

Bumping after an hour? 

If you feel I gave bad advice, I asked for more information, which could help future members assist you, and tried the first thing that came to mind, which didn't work, but I tried.

It is also 0411 at the time I write this...

---

### Post by ikt on 2008-01-25
> **LaRoza said:**
> Bumping after an hour? 

If you feel I gave bad advice, I asked for more information

you didn't give bad advice, i'm just looking for more advice :)

I'm drinking every command and possible answer in, as this might help me solve future problems. I appreciate everyone who answers the thread =)

> **muuwt1 said:**
> did it stop at the third bar on the load screen?

It goes past the third bar, and loads all the way, then on the next screen as it starts to load gnome it gets stuck and hard drive activity goes crazy.

---

### Post by gwpritch on 2008-01-25
Since the Hardware abstraction Layer (HAL) seems to be failing run the following and post the results:

```
sudo hald --daemon=no --verbose=yes
```

Also, did you change anything in your gnome desktop configuration just before if failed to load?
If so try this:

```
mv .gconf .gconf-old
mv .gnome2 .gnome2.old
```

this will back up your gnome configuration files.

Try to restart X.

If the problem is with the gnome configuration, .gconf and .gnome2 will be reconstitued with the default settings and you will have a new desktop.

If you still get hung up, just change the files back to your originals:

```
mv .gconf-old   .gconf
mv .gnome2-old   .gnome2
```

and we can look at the HAL issue.

---

### Post by ikt on 2008-01-30
Cheers for the replys :)

My boss was just about ready to give up on it, so he stuck some spare ram in, packed it all up, and turned it on one last time... and it worked...

so it is working right now...

---

