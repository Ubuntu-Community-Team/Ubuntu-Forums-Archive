---
title: "Login Screen Off Center!"
date: 2007-04-11
forum: General Help
---

### Post by Falkon on 2007-04-11
My login screen is too far to the left, there's just black space on the right, and it's too far to compensate with my monitor settings.  How can I fix this?

Everything else is centered, though...

---

### Post by Salpiche on 2007-04-11
Have you tried hitting alt+e to restart x while you are still in the log on screen? I have had the same issue a few times and I have temp fix it with restarting x

---

### Post by Salpiche on 2007-04-11
Have you tried hitting alt+e to restart x while you are still in the login screen? I have had the same issue a few times and I have temp fix it with restarting x

---

### Post by Salpiche on 2007-04-11
woops! 

sorry didn't mean to double post

---

### Post by Falkon on 2007-04-25
Tried it, didn't work.

---

### Post by cloudedice on 2007-04-25
I'm having the same issue.

Video card is an GeForce4 MX440. Xorg is using the "nv" driver. I'm having other issues with nvidia that I don't want to deal with yet.

I can temporarily fix the issue by logging in and running "sudo xvidtune" and playing around with the settings for a while.  As soon as X restarts, it goes back to having the big black section on the right. This happens even when the ModeLine given to me by xvidtune is placed in xorg.conf.

This is a **significant** shift to the left. Probably about 3 inches on my 22" screen.

Any help is GREATLY appreciated.

ice

---

### Post by johnh123 on 2007-04-26
I have a somewhat similar problem- had it with XP as well.  My desktop is shifted about an inch to the right.  With the nvidia xp drivers, I could go in an 'adjust' the screen and shift it back to the left so it looked right.  Is there an nvidia 'control panel' with ubuntu like there is with xp, or any other way to shift my picture back to the left?  (on my monitor, the 'left' button doesn't work, so I can only go further to the right.)

---

### Post by Erlander on 2007-04-26
I have a similar problem.

However what I have noticed is that different screen resolutions and refresh rates will do this.

I think the problem is that the login screen is at a different resolution and refresh rate to what I set the screen at.  What we need to be able to do is to set the login resulution and refresh rate to fix this,

Rob

---

### Post by cloudedice on 2007-05-02
Hazzah! I was able to fix my problems!

I essentially followed [this thread]("http://ubuntuforums.org/showthread.php?t=422918&highlight=nvidia+envy").

After this instruction:
"Now change your xorg.conf to change to the NV driver and restart your system."

I went to [http://www.nvidia.com//object/unix.html](http://www.nvidia.com//object/unix.html), downloaded the driver for my GeForce4 MX440 (Linux AMD64/EM64T Latest Legacy GPU Version (1.0-96xx series): 1.0-9631).

I had to install xorg-dev: ```
sudo aptitude install xorg-dev
```
I installed nvidia-settings: ```
sudo aptitude install nvidia-settings
```
Finally, I ran the NVIDIA driver installer: ```
sudo sh NVIDIA-Linux-*.run
```

I let the NVidia installer take care of editing my xorg.conf file and rebooted. When the system came up, everything was hunky-dory.

ice

---

### Post by topsakatanner on 2008-05-28
> **johnh123 said:**
> I have a somewhat similar problem- had it with XP as well.  My desktop is shifted about an inch to the right.  With the nvidia xp drivers, I could go in an 'adjust' the screen and shift it back to the left so it looked right.  Is there an nvidia 'control panel' with ubuntu like there is with xp, or any other way to shift my picture back to the left?  (on my monitor, the 'left' button doesn't work, so I can only go further to the right.)

I have searched several different days with every search value I can and no one seems to have an alignment problem as bad as this.

When I start Ubuntu Hardy now (I changed my login window to the better looking blue from the horrible tan color) my login screen is shifted EXTREMELY far to the left and top, so far that only about 1/2 square inch of the lower-right corner of the login display is showing in the top left corner of my screen. 

The mouse pointer is up there in that corner, and I can move it around it's little 1/2 inch cage, but I can't use the login screen because it is completely off-screen. There are two pointers, the one I can move in the corner, and one frozen in the middle of the black emptiness which is the rest of my screen. 

I have a dell desktop and I'm using a 42' Westinghouse LCD for my monitor (connected with the vga cord). I thought this was just a problem with my Windows XP (which I barely ever use now that I have Ubuntu dual boot), but now it's started with Ubuntu. HELP!

Has anyone ever seen a solution? HELP!

The only way to bypass is to move the mouse back and forth during the entire boot up in which case the pointer shows up first (going back and forth, back and forth, while I wait). THEN the login screen shows up, so annoying. I have formatted my hard drive at least five times while using windows and it always has this bug. AAAAH! help....

---

