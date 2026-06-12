---
title: "Ubuntu randomly crash"
date: 2007-01-29
forum: General Help
---

### Post by daftman on 2007-01-29
Hi, I need some guidance pin pointing the problem
My ubuntu crashes randomly, once every 12 hours. When this happens, I cannot even get a a terminal from tty1 to tty6. I can't remotely access it from ssh and alt+sysrec + (r,s,e,i,u,b) does not work.

I am suspecting it has something to do with my hardware. However, if I dual boot on to windows, it would not crash for days. It could even be the kernel and/or swap file.

Can anyone guide me to trapping this problem and identifying what is wrong with it?

---

### Post by jazzgossen on 2007-01-29
I think your best bet is to try to monitor the log files in /var/log/, especially /var/log/syslog.

---

### Post by Johnathon on 2007-01-29
If you can't find anything, it may be related to my own crash of this style.

Are you finding core dumps in your /home/$username folder?

---

### Post by daftman on 2007-01-30
I checked the message log and the kernel log
The only thing I find interesting is that when my system crash, there is usually a message relating to gconfd such as "receive signal 15 exit cleanly" or "gconfd not in use, exiting"
There is nothing significant in the syslog. However, this type of messages only occur when I run gnome. If I was in command line interface (CLI) there would not be any log of a crash. The system would freeze or would become extremely unresponsive i.e taking 15 minutes to log in or process an "ls" command.

Could there perhaps be memory leaks that take up all my swap file or ram?

---

### Post by Rui Pais on 2007-01-30
Hi,
It could be problems with the filesystem...
Try to load from a livecd and do  :
[CODE]e2fsck -f /dev/<yourh_ubuntu_partition_here[>/CODE]

And are you hardware specifications? Specially whats your graphical card what and module you use for it?

---

### Post by jazzgossen on 2007-02-01
One of the users on my computer has a similar problem. She gets logged out if she leaves the computer for a while, and the syslog says that gconfd received signal 15. It started occuring a couple of weeks ago. I don't have a solution but you can check [this thread]("http://www.ubuntuforums.org/showthread.php?t=336892&highlight=signal+15"), and I also posted a thread about my problem [here]("http://www.ubuntuforums.org/showthread.php?t=350814").

---

### Post by dmwit on 2007-02-01
daftman -- I have identical symptoms, right down to the cryptic log messages.  When the problem started a week ago, crashes were infrequent, usually around 12 hours.  It has gotten progressively worse, to the point where it is now only about five minutes.  When it crashes, everything stays on the screen, but nothing responds... I have to turn off the power. =(

I can confirm that it is not related to a corrupted filesystem -- fsck reports that the drives are clean.

It is also not (CPU) overheating -- I put a notifier in the lower right of my temperature, and it was a steady 54-55C from boot to crash.  (That's apparently fairly normal for PIV's... =)

I even did a clean install of Edgy to see if I had inadvertently installed some nasty thing -- but it still dies after a few minutes.

Does anyone have any more clues as to what it might be?

~d

---

### Post by Rui Pais on 2007-02-01
> **dmwit said:**
>  When it crashes, everything stays on the screen, but nothing responds... 

hi, this means that everything in screen is frozen but you still can move mouse and click over stuff?

---

### Post by dmwit on 2007-02-01
> **Rui Pais said:**
> hi, this means that everything in screen is frozen but you still can move mouse and click over stuff?

Hi Rui,

No, the computer is totally non-responsive by the time everything is frozen.  The mouse doesn't move, the keyboard does nothing, etc.

~d

---

### Post by Rui Pais on 2007-02-01
> **dmwit said:**
> Hi Rui,

No, the computer is totally non-responsive by the time everything is frozen.  The mouse doesn't move, the keyboard does nothing, etc.

~d

So it shouldn't be the graphical drivers/agpgart one... and you already eliminate the broken filesystem and the the overheating possibilities too... 

But, you said you install a fresh one and it froze too? From the default and with nothing more installed? Then it looks definitely an hardware issue. Either you have some hardware that make ubuntu froze or you have something die in that box? memory sticks usually are responsible for such kind of frozens... If you have 2 sticks, or some old from an upgrade try to change to 1 stick or an old one and see if it still happens.

---

### Post by dmwit on 2007-02-01
> **Rui Pais said:**
> memory sticks usually are responsible for such kind of frozens... If you have 2 sticks, or some old from an upgrade try to change to 1 stick or an old one and see if it still happens.

Okay, I will try this as soon as I can.  Thanks for the hint!
~d

---

### Post by dmwit on 2007-02-04
Thanks, that seemed to solve it.
~d

---

