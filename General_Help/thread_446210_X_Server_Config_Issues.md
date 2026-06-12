---
title: "X Server Config Issues"
date: 2007-05-16
forum: General Help
---

### Post by ismisunderstood on 2007-05-16
I just finished my Wubi install, and am having a problem getting Ubuntu to run.

When starting, I get through to where I have an Ubuntu image, and a loading bar, bar gets almost all the way across when I get an error message:

```
"Failed to start the X Server...might not be configured correctly...view the report..."
```

Viewing the report, I get two errors at the bottom:

```
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

     Fatal Server Error:
no screens found.
```

So...now what?  I'm almost totally new to linux/unix/Ubuntu (only exception is small usage of a live CD to pull windows files from a bad windows install), so please speak slowly using small words :sad:

Guess I should also mention, I'm using a Dell Inspiron 6400, which is running some wierd version of an ATI Mobility 1300 (or 1400, depending on who you're talking to.  The drivers the same...at least in Windows).  I'm assuming that might have something to do with this issue.

Thanks!

---

### Post by teaker1s on 2007-05-16
> Wubi is an unofficial Ubuntu installer for Windows users that will bring you into the Linux world with a few clicks.
**with that said** if you can type in ubuntu try-
```
sudo dpkg-reconfigure xserver-xorg
```
select vesa as your driver and try ubuntu again

---

### Post by ismisunderstood on 2007-05-17
Still having the same problem.  I tried first the suggestion of selecting VESA as the driver, then when that failed, also tried selecting ATI as the driver, both had the same result.  

Also, during the configuration prompts, both the video card and monitor(laptop display) were identified as "generic video card" and "generic monitor", respectively. 

Any other help would really be appreciated.

((By the way...what was the first comment made in reference to?  Should I have posted this in a different forum?  If so, could you possibly help me determine where would be a better place to put this?))

---

### Post by teaker1s on 2007-05-17
my first comment was made to say that I haven't tried a wubi install yet,  I've experience with ubuntu. I believe your issue is a display issue and not a wubi related one-If it is my appologies.

Now what make and model graphics do you have-I'll look for information for you?:KS

---

### Post by clpo13 on 2007-05-17
Try [this tutorial]("http://ubuntuforums.org/showthread.php?t=399913"). It's specifically for Inspiron 6400/E1505 laptops with ATI x1400 graphics.

I haven't tried it with Wubi, but I know it works on a straight installation of Ubuntu 7.04, so it should work.

---

### Post by ismisunderstood on 2007-05-18
Looks like it's working, 'cause I'm typing this from inside Ubuntu!  

As an aside, I did try really hard to follow the directions in that howto, but the second time running the /dellinstall still gave me some errors.  I didn't get a chance to read exactly what they were, but after restarting it logged me in, so I guess there's not a lot to complain about!

Thanks a bunch.  Now I just have to learn how to use this darn thing...

---

### Post by Prom1 on 2009-01-29
> **ismisunderstood said:**
> I just finished my Wubi install, and am having a problem getting Ubuntu to run.

When starting, I get through to where I have an Ubuntu image, and a loading bar, bar gets almost all the way across when I get an error message:

```
"Failed to start the X Server...might not be configured correctly...view the report..."
```

Viewing the report, I get two errors at the bottom:

```
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

     Fatal Server Error:
no screens found.
```

So...now what?  I'm almost totally new to linux/unix/Ubuntu (only exception is small usage of a live CD to pull windows files from a bad windows install), so please speak slowly using small words :sad:Thanks!

Got the same problem.
The system I'm using a Dell OptiPlex GX260, which is running built in INtel video chipset 64MB max. 

Tried :

```
ctrl+alt+f2
sudo dpkg reconfigure xserver-xorg
```

I see no settings for VESA only US Keyboard :(   - odd as Wubi v8.04 worked on WinXP SP2, but I've upgraded to SP3 months ago. I only have a VGA connection to my LCD.

---

