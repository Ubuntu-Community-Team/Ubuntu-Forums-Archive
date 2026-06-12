---
title: "initramfs / fsck at startup"
date: 2021-01-07
forum: General Help
---

### Post by cuchul on 2021-01-07
Hi

Last night I tried to rename a file in my documents folder, but it failed to rename. It was a libreoffice writer odt document, I'd almost certainly loaded it earlier in the session, but it was definitely not open when I tried to rename it. I shut down the computer and went to bed. This morning, at boot I dropped into the initramfs prompt at boot. There was no indication of the error, exit and reboot were also unresponsive. Finally I Ctrl-alt-del rebooted, and the next time it dropped to initramfs, it actually mentioned fsck. I ran fsck /dev/sda2, which repaired the problem and the system booted up. Firefox mentioned that it couldn't recover the previous session, so I'm not sure of the actual cause.

So far so good. The problem for me is, last June I installed linux mint on this hardware, which was all brand new. Specifically, it's a new disk. Mint gave this exact same problem intermittently around once a month. I eventually asked on the mint forum, and the popular consensus was that I should not have installed mint 19.3 and then upgraded to mint 20, I should have installed 20 clean.

[https://forums.linuxmint.com/viewtopic.php?f=46&t=334128&p=1913317&hilit=initramfs+fsck#p1913317](https://forums.linuxmint.com/viewtopic.php?f=46&t=334128&p=1913317&hilit=initramfs+fsck#p1913317)

I duly installed ubuntu 20, and it's been fine for 2 entire months.

Now, Linux is utterly goddam brilliant. However, I'm a developer. Linux is code. I assume it's mostly good solid code, with occasional parts of brilliant code. Still, code has bugs. It doesn't mean linux is bad, just that things sometimes break.

My question is basically, is this normal? If not, is it my disk, or possibly another part of my hardware? If it's software, it's baked into both ubuntu and mint, or possibly it's libreoffice? Or firefox? Do I need to even be worried, or just keep running fsck every month without a care in the world?

EDIT if you read the mint thread, note I have since bought a UPS, so no more surprise shutdowns.

---

### Post by Impavidus on 2021-01-07
Assuming you don't run them as root (never do that), there's no way Libreoffice or Firefox could cause boot problems. And it's not normal to get random filesystem errors. This smells like a hardware problem. Your drive may be new, but could be bad anyway. Or just poorly connected.

---

### Post by cuchul on 2021-01-07
Hm. Well I'll re-seat the cables, but would that not show up in the disks report?

---

### Post by CelticWarrior on 2021-01-07
No.
It may show in SMART tests though.

---

### Post by cuchul on 2021-01-12
Well I ran the extended smart self test in disks, and it looks ok to me. If it is in fact about to fail catastrophically, at least it's under warranty for another 18 months.

---

### Post by cuchul on 2021-02-12
A month later, and it happened again. fsck appeared to fix everything. The timing is peculiar, is there some sort of process that only triggers once a month, or .. should I actually be tracking the dates this happens on? 7 Jan, 12 Feb, yeah probably not.

A comment for the initramfs devs, the help command does not actually list fsck as a possible command you can run. I was trying to remember the command, if fsck had been listed, I'm reasonably sure I would have been able to recall the correct syntax. As it is I had to search the internet for the solution from scratch.

 Anyway, I'm back up and running, no apparent damage, but my firefox profile got removed, I had to log back in, so I cleared the cache as well, because most of my settings had to be re-imported anyway. Kinda tiresome, but could be worse.

---

