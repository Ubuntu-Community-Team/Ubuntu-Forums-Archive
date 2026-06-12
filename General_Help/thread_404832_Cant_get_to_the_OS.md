---
title: "Cant get to the OS"
date: 2007-04-08
forum: General Help
---

### Post by Bobberb on 2007-04-08
Ok, So I install wubi and everything is fine
I reboot and hit the "Ubuntu" option in my boot menu
it loads and loads and loads, and then I get some errors and from there is just gives me a CLI and I have no idea what to do!

the errors include something with I-O and kernel panics


also, this is Wubi under a bootcamped macbook

---

### Post by Bobberb on 2007-04-08
Hello everyone, I seem to have a problem booting feisty (beta) on my dell 1.8ghz 768 mb ram 128mb gpu box.

When I try to boot the CD I just get an error that something is not connected and something about an I-O


(I might need a bios upgrade, but Ill try that later)

---

### Post by aysiu on 2007-04-08
So are you saying you get the I-O errors when you use Wubi *and* when you use the Feisty installation CD?

---

### Post by Bobberb on 2007-04-09
> **aysiu said:**
> So are you saying you get the I-O errors when you use Wubi *and* when you use the Feisty installation CD?

yessir

---

### Post by aysiu on 2007-04-09
Can you post as much information as you have?

For example, what are the specifications for your computer (processor, RAM, etc.)?
What are the *exact* errors you get (I know it's annoying to have to break out the pen and paper to write it down, but verbatim relaying of error messages are more likely to lead to a solution)?
Do the Feisty CD and Wubi give the same errors? Or are they slightly different?

---

### Post by Bobberb on 2007-04-09
> **aysiu said:**
> Can you post as much information as you have?

For example, what are the specifications for your computer (processor, RAM, etc.)?
What are the *exact* errors you get (I know it's annoying to have to break out the pen and paper to write it down, but verbatim relaying of error messages are more likely to lead to a solution)?
Do the Feisty CD and Wubi give the same errors? Or are they slightly different?

not anymore, it was a floppy disk error, now it just gets stuck at the 3rd block out of 20 during the boot after grub (orange and black bar)

---

### Post by Bobberb on 2007-04-09
I have given up on wubi, I am bringing this to general help

[http://ubuntuforums.org/showthread.php?t=405318](http://ubuntuforums.org/showthread.php?t=405318) (the boot problem)

---

### Post by aysiu on 2007-04-09
Do you know what a checksum is?

What are the specs on your computer?

Freezing up during a boot of the Desktop CD (or "live CD") usually has to do with one or more of the following:
1. Not enough RAM
2. Hardware failure
3. CD that got corrupted during the ISO download
4. CD that got corrupted during the ISO burn

---

### Post by Bobberb on 2007-04-09
It is not about that anymore 

the CD is fine, I installed perfectly (i wiped windows, so no more wubi)

The problem is the startup will not....go (past the 3rd "block/section")

---

### Post by Bobberb on 2007-04-09
> **aysiu said:**
> Do you know what a checksum is?

What are the specs on your computer?

Freezing up during a boot of the Desktop CD (or "live CD") usually has to do with one or more of the following:
1. Not enough RAM
2. Hardware failure
3. CD that got corrupted during the ISO download
4. CD that got corrupted during the ISO burn
It might be a hardware failure, I do not know, but I was able to INSTALL with the alternate cd (but not get past the boot screen)

---

### Post by Ptero-4 on 2008-09-28
Were you using the same Desktop CD for both wubi (on the Mac) and installing on the Dell box? It could be a bad download/bad burn (would explain why it fails in BOTH installs).

---

### Post by ago on 2008-09-29
parent is an issue from beta 2007...

---

