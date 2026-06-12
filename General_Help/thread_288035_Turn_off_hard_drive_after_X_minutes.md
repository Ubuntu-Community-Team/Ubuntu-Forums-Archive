---
title: "Turn off hard drive after X minutes?"
date: 2006-10-29
forum: General Help
---

### Post by purifyyourmind on 2006-10-29
In Windows there's a feature to turn off the hard drive after X minutes. It's handy because Suspend mode in both OSes will stop all networking activity.

So let's say I start a download/upload before I go to sleep that will take four hours and I wake up in eight hours. If the computer suspends after an hour, I'll wake up to find three hours left on the DL/UL (or worse, like when Firefox gives up on a download). But with the "turn hard disk off after X minutes" feature, the DL/UL will be complete and the hard drive will have been off for four hours.

Any way to do this in Ubuntu? Thanks!

---

### Post by lukon on 2007-01-24
Bump.

Ya, I'm interested in this also.

---

### Post by Onimae on 2007-01-24
System>Preferences>Power Management

The second slider seems to be something close to what you want to do. I could be wrong, though. I've never tried this, but it might be worth a shot.

**Onimae**

---

### Post by lukon on 2007-01-24
Well, Onimae,

I suspect the control you mention will controll the power-down for the entire computer. Ya, I looked into that one too.

But some people are interested in controlling the power-down behavior of individual hard drives, shutting down 2 out of three hard drives at 5 minutes of inactivity, for example.

And the way to do this is revealed on this post thread here:

[http://www.ubuntuforums.org/showthread.php?t=179074]("http://www.ubuntuforums.org/showthread.php?t=179074")

---

### Post by esaym on 2007-01-24
I am also interested in this.  I think everyone is actually.  I miss the days of win98 when this actually worked.

To do it properly you have to stop access to the hard drive.  I really haven't figured out how to do that yet :( 

[http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713](http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713)

---

### Post by lukon on 2007-01-25
> **esaym said:**
> I am also interested in this.  I think everyone is actually.  I miss the days of win98 when this actually worked.

To do it properly you have to stop access to the hard drive.  I really haven't figured out how to do that yet :( 

[http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713](http://www.linuxquestions.org/questions/showthread.php?p=2486713#post2486713)

Yes, I see the problem discussed at the link you give. The solution at the link I provided above ([http://www.ubuntuforums.org/showthread.php?t=179074]("http://www.ubuntuforums.org/showthread.php?t=179074")) probably works for me because the drives I want to turn off after 5 minutes of inactivity are Windows VFAT drives that Linux won't be accessing unless given explicit commands by the user. But turning off a Linux drive would be a problem if Linux, or a Linux application, keeps accessing it.

---

