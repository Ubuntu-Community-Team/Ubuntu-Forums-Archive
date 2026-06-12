---
title: "ubuntu fails to boot"
date: 2012-12-04
forum: General Help
---

### Post by hhall on 2012-12-04
Hi all. I seem to need help.

Overnight, my ubuntu installation appears to have developed a major problem. It fails to boot. 

To be more exact, the computer starts normally when switched on, but it takes ages for the GRUB screen to appear. Once I choose for it to boot in Ubuntu, it switches to a purple screen (no loading indicator, just purple), or occasionally to a black screen with a flashing cursor. After that, nothing happens.

I have tried to boot through recovery mode, but that does not work either.

This problem occurred suddenly, literally overnight. I think the evening before, ubuntu performed some updates. I run on a dual install with Windows 7, which I hardly ever use (I do right now, of course).

Can anyone suggest what I might do about this?

Thanks.

---

### Post by hhall on 2012-12-05
Hi again.

I managed to start ubuntu as a live session from a USB stick. I ran the GRUB repair program - but it did not help. 

This is the link it produced: [http://paste.ubuntu.com/1411448/](http://paste.ubuntu.com/1411448/)

I really need my system to work again, this is by the worst and the most frustrating problem I have had in nearly 4 years on ubuntu. And not a single reply so far...

HH

---

### Post by puurokauha on 2012-12-05
I have same problem. But my computer wont show grub at all. It boots normally to logon, I can hear login sound and login, but screen stays black. All I see when I boot my computer is bios and after that screen stays black. I also have dual boot to windows 7. And this problem came today, yesterday it was ok.

System
Ubuntu 12.04
Windows 7
AMD Radeon HD 5770

---

### Post by hhall on 2012-12-05
Bump - does anyone know anything about this?

---

### Post by hhall on 2012-12-05
Oh well. I ended up simply backing up my data, wiping the ubuntu install entirely (with gparted, leaving the disk space unallocated) and then reinstalling as dual boot. Considering my lack of experience, it seemed the quickest and cleanest way. Everything works fine now.

HH

---

### Post by hhall on 2012-12-06
Or not.

It worked for 1 day. Ubuntu booted ok several times after the reinstall. Now, I can not boot any more. Instead,  I get the "unknown filesystem. Grub rescue" message. To make it worse, live session does not work, neither from CD, nor from USB.

I have no idea what to do.

Does anyone?

HH

---

### Post by oldfred on 2012-12-06
If it worked and then stopped, is it really some sort of hardware issue.

Often memory issues can cause that type of issue. You might want to run memory tests from grub menu. 

Some also suggest removing one memory stick (if you system is configured so you can) and test, then try other memory stick. Sometimes just cleaning contacts helps. You can use an eraser and then clean with alcohol. Make sure it dry before reinstalling.

---

### Post by hhall on 2012-12-06
Thanks, Oldfred.

Yes, I am beginning to fear you may be right. I have tried booting from a memory stick and from CD (DVD, actually), and it worked only oonce on many tries, from a live DVD, and then crashed. Maybe a HDD issue, or eve a motherboard one? Running a check from a Gparted live CD now...

HH

---

