---
title: "Dual boot Ubuntu 12.10 and Windows 7, no longer able to start Ubuntu"
date: 2012-10-19
forum: General Help
---

### Post by themagicmnm on 2012-10-19
Hi all,
I have installed Ubuntu 12.10, dual booting with Windows 7 on my Lenovo x120e.

Everything was working fine until windows installed a series of updates.  Now, I get grub when I turn on the computer, but if I select Ubuntu the screen turns black and nothing happens.

If I log in to Ubuntu using recovery mode, I can get to Ubuntu.  I have tried using recovery mode to repair grub (it says this is successful), but it did not remedy the problem.

I am still able to log into windows just fine.

I've tried google and forum search but can't seem to find someone having a similar problem to me.

Any help is very much appreciated!

---

### Post by kc1di on 2012-10-19
> **themagicmnm said:**
> Hi all,
I have installed Ubuntu 12.10, dual booting with Windows 7 on my Lenovo x120e.

Everything was working fine until windows installed a series of updates.  Now, I get grub when I turn on the computer, but if I select Ubuntu the screen turns black and nothing happens.

If I log in to Ubuntu using recovery mode, I can get to Ubuntu.  I have tried using recovery mode to repair grub (it says this is successful), but it did not remedy the problem.

I am still able to log into windows just fine.

I've tried google and forum search but can't seem to find someone having a similar problem to me.

Any help is very much appreciated!

Not exactly sure what might have happened but would seem that somehow grub was messed up. 
you might be able to fix it with Boot-repair tool found[ here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by cacapo on 2012-10-19
Just to second the question. This occurs also with a fresh install. The first reboot of ubuntu works just fine, but the second time you try to boot all you get after Grub is a black screen and a mouse-arrow.

---

### Post by cacapo on 2012-10-19
Just found out that this does not happen if I let Grub load Ubunut passively. If just idle and let the counter go to 0 I get a correct load of login etc. Strange. Has to be a Grub issue.

---

### Post by cacapo on 2012-10-19
The problem goes away if I switch to gdm.

---

### Post by themagicmnm on 2012-10-20
> **cacapo said:**
> The problem goes away if I switch to gdm.

What is gdm?

---

### Post by themagicmnm on 2012-10-20
> **kc1di said:**
> Not exactly sure what might have happened but would seem that somehow grub was messed up. 
you might be able to fix it with Boot-repair tool found[ here.]("https://help.ubuntu.com/community/Boot-Repair")

No dice on boot-repair.  Same black screen, no pointer or anything, it flashes once then goes black again and nothing happens.  Any help is very much appreciated.

---

### Post by kc1di on 2012-10-20
> **themagicmnm said:**
> No dice on boot-repair.  Same black screen, no pointer or anything, it flashes once then goes black again and nothing happens.  Any help is very much appreciated.

This isn't a EUFI machine is it?
can you post the output of boot-repair log. it should have given you a webpage address to get it from.

---

### Post by Geezanansa on 2012-10-20
The black screen issue with 12.10 is a known bug.  After installing 12.10 and then on rebooting was greeted with blackscreen and no input.  Rebooted and loaded grub (by holding shift at/just after POST) to get kernel choice and booted ubuntu.  Once logged in - updated system.  When updates were being installed i read information in the text area of update window referring to _**not log into a default desktop session once and move/update a xconf file and/or a X11org file.**_
There was even a link to launchpad for more info.  The updates finished installing so rebooted and got black screen.  Like OP have to let grub load and then boot kernel to get to log in screen.
Some report switching to and from tty (ctrl+alt+(F1-F6))gets them to log in screen.


Trying to find the information i refer to second time is proving to be more than time consuming.

Using an nvidia card on this system and had trouble getting proprietary driver installed-jockey not behaving as expected.
Trying to evaluate many issues at once so very difficult to keep perspective.  Good fun trying to learn though.   
> cacapo              **Re: Dual boot Ubuntu 12.10 and Windows 7, no longer able to start Ubuntu**
         The problem goes away if I switch to gdm.     **GNOME Display Manager**



How did you do that cacapo?


lightDM is a X display manager.

It is the non loading of x display manger = black screen

How to fix?

Some workarounds here [http://ubuntuforums.org/showthread.php?t=2070426&highlight=black+screen](http://ubuntuforums.org/showthread.php?t=2070426&highlight=black+screen)

---

### Post by cacapo on 2012-10-21
> How did you do that cacapo?
```
sudo apt-get install gdm
```and then answer the questions to chose gdm as default

cheers

---

