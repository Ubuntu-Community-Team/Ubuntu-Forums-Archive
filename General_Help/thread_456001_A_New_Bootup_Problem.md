---
title: "A New Bootup Problem"
date: 2007-05-27
forum: General Help
---

### Post by DMXell on 2007-05-27
A few months back I had a problem with the kernel giving me a critical error. I then tried to install Ubuntu by partitioning and Windows crashed. So, when I installed Windows again it reformatted my drive and I decided to try Wubi again today (a month or so later). I have Windows XP Home, FYI. So I installed it, rebooted and went through the blue setup screen. Then I rebooted again and there wasn't the kernel failure! Yes! But alas another problem. During the Ubuntu GUI bootscreen (with the orange bar) it freezes at the 2 and 3/4rth bars mark. Any ideas as to why?

---

### Post by Metacarpal on 2007-05-27
When you say it freezes at those points, do you mean that it hangs there for several seconds before proceeding?  If so, that's pretty normal.  The progress bar during Ubuntu's boot sequence fills as it completes certain tasks, rather than being a smooth time-progression.

Some tasks, such as enabling networking, can take a little longer than others.

If your machine is hanging for longer than, say, 10 seconds, or if it freezes and doesn't progress further at all, that may be an indication that Ubuntu is trying to load something that your machine doesn't like.

That said, how much RAM do you have?

---

### Post by DMXell on 2007-05-27
It's the latter. I let my PC sit there for six minutes with no change. As for my RAM, I have 1.5 GB. I use an eMachines so I'd expect that it doesn't like what Ubuntu is doing, my PC really sucks.

---

### Post by DMXell on 2007-05-28
Can anyone help?

---

### Post by ago on 2007-05-28
Edit c:\wubi\boot\grub\menu.lst and delete "quiet splash" everywhere you see it. This will show you more interesting messages during boot. You may also want to comment out "hidemenu" and set "timeout" to 5. This will show you a second boot menu, you can use that to select recovery mode.

---

### Post by DMXell on 2007-05-28
Removing quiet splash will do nothing, I've already tried it. I get a kernel panic of sorts, but I'll try the other two, thanks!

---

### Post by DMXell on 2007-05-28
Okay, three of the menu options result in kernel panics (including Recovery) and the fourth (Memtest) simply said "File Not Found" and sent me back to the menu.

---

### Post by ago on 2007-05-28
try adding "noapic nolapic acpi=off" as kernel parameters in menu.lst. If it does not work try to boot with the Ubuntu Live CD. If it still crashes then it's likely some incompatibility at hardware level.

---

### Post by DMXell on 2007-05-28
I don't know exactly where to add it, but I through it in where I thought it'd go. Also, if this won't won't and it's incompatible with my hardware, how would it be? I have a somewhat modern computer. Granted it has an outdated CPU (Intel P. 4) it meets all the specs. Enough RAM, more than enough CPU (2.93 GHz), format is NTFS (I believe that Wubi is designed to run on these), though I do have my internal graphics chipset turned off in favor of an nVidia GeForce 5200FX. Should I turn the chipset on?

---

### Post by calou on 2007-05-28
I don't know if this is the same problem or not but I loaded some new updates this morning (I believe there were 11 of them, don't remember what they were) but ever since its taken in excess of 5 minutes for Ubuntu to boot up and when it finally does I noticed some interesting effects like I now have to click twice to exit from Ubuntu and I can now not see my NTFS (Windows drive, I have a dual boot system) from Ubuntu.  I've also noticed that while its loading Ubuntu reports  "Loading hardware drivers . . . . . fail", it also indicates it can't mount a drive but the message goes by so fast I haven't been able to record the message.  Could the problem you're having be related?  Don't know since I'm a newbee to Linux/Ubuntu.  Has anyone else experienced similar problems since updating software today (5/28/07)?

---

### Post by DMXell on 2007-05-28
Yeah, that's not the same problem. Mine wouldn't even let me go into Ubuntu to update it (I want to so bad, just to get away from Windows =/).

As for the fix Ago, I think I put it in the wrong spot. Resulted in another kernel panic.

---

### Post by calou on 2007-05-28
Sorry, at first I thought I was hung up on the splash screen too but I waited and eventuallyI did boot.  Yeah, I know what you mean about dumping Windows thats why I'm on Ubuntu too.  Guess I'll start a new thread and see if I can get a solution to my problems, good luck.

---

