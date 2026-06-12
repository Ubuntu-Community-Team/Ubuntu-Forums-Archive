---
title: "Various Problems"
date: 2016-05-02
forum: General Help
---

### Post by AlexStargazer on 2016-05-02
Hello all:

I recently upgraded from 15.10 to 16.04. I say upgraded, since I had to install from a USB due to an unknown network error. I initially tried installing Korora; that worked, until I rebooted the second time and Cinnamon disappeared. I couldn’t even open a terminal. Then I tried Linux Mint: installing the nvidia driver on mint would cause it to fail to boot, and my motherboard would beep out a graphics card error.

I’ve managed to install 16.04, and although it works without any *serious *problems, it does have a number of inexplicable niggles.

By the way, 15.10 was stable: I couldn’t mount my Android phone, but aside from that (and the occasional Banshee crash, which was Banshee’s fault I assume) everything worked fine. Well, I did try to install Cinnamon on 15.10, but got blurry fonts when I logged into Cinnamon.

Anyway, about 16.04...

My hardware:

[LIST]
[*]Desktop computer.
[*]Gigabyte Z87x-D3H
[*]Networking via ethernet.
[*]Dual 1080p monitors.
[*]Intel I5-4570.
[*]Nvidia GT 650 1GB.
[*]8GB RAM
[*]Ubuntu installed on 120GB SSD, no other OS on that disk.
[*]I also have a hard drive (WD 500GB Black) with Windows 7 on it, where I also keep my files.
[/LIST]

The first niggle I experience is in the boot-up process.  I have the UEFI boot order to (USB), (SSD), (HDD) (and DVD somewhere in there). While booting, the computer beeps twice, and what looks like a grub menu comes up—only I can’t see any writing. Then it beeps again, and I get to the log-in screen. Logging into Unity works fine, although logging into Cinnamon does show an Ubuntu logo on the desktop, then the screen flashes, and Cinnamon loads. I’m wondering if this is normal behaviour, since I’ve not seen it before.

Anyway, initially when I tried to play SuperTuxKart, I couldn’t change the graphics settings. Now that issue has disappeared (?)

Then, a day later, I had the system *freeze*—not even the mouse or Ctr+Alt+T worked. I rebooted, it worked; but the Unity UI fonts looked blurry (other fonts, like on Gedit, didn’t). I rebooted again and things were as normal (?)

I’ve not had it freeze again.

Cinnamon’s wallpaper used to revert to the Ubuntu default if I opened Nautilus. It could not be changed except by logging out. I’ve changed the default to Nemo for all file actions as a work-around.

The final problem I’ve had is that LO Writer renders the Minion Pro font  on my book incorrectly (the kerning is awry). Weirdly, Minion Pro  renders fine on Gedit.

That’s all of it. Anyone know where to start?

---

### Post by grahammechanical on 2016-05-02
So, these various problems are not actually with Ubuntu + Unity but with an alternative desktop installed onto Ubuntu. Correct? I just like to be clear about things. And you are reporting having issues with Cinnamon on Ubuntu over two release cycles.

---

### Post by izznogooood on 2016-05-02
I would advise you to wipe the slate clean. Backup what you need, then Install Ubuntu Mate 16.04. Then Install Cinnamon. 

I would try MATE because various reports I´ve seen states that this works well with "difficult" UEFI Bios´s .

---

### Post by AlexStargazer on 2016-05-03
Both actually. I get some issues with Cinnamon—e.g. with the logging in—but I also had Unity hard-freeze on me a week ago. As I said in my post, I had to re-start twice to get Unity back to normal. Being forced to hard reboot a Linux PC is not normal; I’ve never heard of a Linux problem that needs rebooting twice!

Also, the new Gnome Software app shows me ‘system updates’ (see screenshot: [https://drive.google.com/uc?export=download&id=0BzBJDYgJplomT2htR2Q3bkxSVnM](https://drive.google.com/uc?export=download&id=0BzBJDYgJplomT2htR2Q3bkxSVnM)) even when the Software Updater says there are no updates. On Cinnamon, it sometimes gives me notifications as well. Any idea why the Gnome Software app seems to think there are updates when there are none, or why it even ships with this feature seeing as to how Software Updater is meant to take care of it?

It’s not that my problems are dealbreakers, it’s that they’re so weird and intermittent. 

---------------------

As for Izno:

> 
I would advise you to wipe the slate clean. Backup what you need, then Install Ubuntu Mate 16.04. Then Install Cinnamon. 

I would try MATE because various reports I´ve seen states that this works well with "difficult" UEFI Bios´s .



Thanks for the suggestion, but I’d really rather not re-install AGAIN. I have exams in two weeks and this is my main PC (I have a MacBook Pro but I can’t use my dual monitors with that!) Korora and Linux Mint already gave me havoc.

That said, you do think the UEFI might be to blame? Is it worth trying to boot into BIOS legacy mode, just to see? I think my UEFI has that setting buried somewhere...

---

### Post by izznogooood on 2016-05-03
No I dont, I suspect i was answering another post. I have no idea how this got here (Beer perhaps.. ;) )

---

### Post by AlexStargazer on 2016-05-11
I&#8217;ve noticed something that may account for some of the strange behaviour I&#8217;m seeing of Ubuntu&#8212;the OS seems to believe I have a Xeon series integrated graphics: [URL="https://drive.google.com/file/d/0BzBJDYgJplomRHA3X3JrMXFNRmM/view?usp=sharing"]https://drive.google.com/file/d/0BzBJDYgJplomRHA3X3JrMXFNRmM/view?usp=sharing 


[/URL]

---

### Post by vasa1 on 2016-05-11
Hi,

Ii may be better to post several specific questions, one to each thread, because there'll be less confusion and each thread will be of more use to those who come looking for solutions.

Obviously, having informative titles for each thread would help both you and others.

---

