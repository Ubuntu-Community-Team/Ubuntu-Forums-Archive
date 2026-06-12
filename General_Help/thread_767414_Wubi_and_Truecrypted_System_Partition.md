---
title: "Wubi and Truecrypted System Partition"
date: 2008-04-25
forum: General Help
---

### Post by snaildarter on 2008-04-25
I have XP using Truecrypt on the entire drive (what the Truecrypt folks call "System Encryption").  I have tried to install Ubuntu with Wubi, thinking it would work fine.  It doesn't, halting at the common initramfs/Busybox prompt.  I've tried everything I can think of from what I researched.  I just want to make sure that this is impossible before I give up.  Any thoughts?  Thanks

---

### Post by ago on 2008-04-25
encrypted  disks are not supported at the moment

---

### Post by snaildarter on 2008-04-25
Thank you, ago.  Since you say, "at the moment," does that mean that this feature is being planned in the future?  thanks

---

### Post by ago on 2008-04-26
possibly but that doesn't depend on me

---

### Post by strasharo on 2008-11-21
So, is it supported in Interpid Ibex?

---

### Post by strasharo on 2008-11-24
Bump.):P

---

### Post by ago on 2008-11-25
Don't think so, do not recall anyone working on that, but might be wrong. For it to work truecrypt must be available in the main repository as a module and be included in the initrd (if an official module is available I might be able to influence the second step).

[http://packages.ubuntu.com/search?keywords=truecrypt&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=truecrypt&searchon=names&suite=intrepid&section=all)

---

### Post by strasharo on 2008-11-25
Understood, thank you for the answer. ;)

---

### Post by martincs14 on 2009-02-18
hey

i also have xp (pro) and have whole drive encryped with truecrypt.

as i understand i cannot install wubi.

what if i decrypt the hard drive, install wubi and reencrypt it
(all with truecrypt)

would that work?

thanks for help.

martin

---

### Post by gbold on 2010-07-28
Hi Martin-
Quick answer is No as I have tried the same thing (XP Pro with Ubuntu as a WUBI session).  It did work when I had my C: drive encrypted but not the D: drive (where Ubuntu is located, it was an extended partition).  I had changed the D: drive partition to a primary drive and re-encrypted everything, only to find that Ubuntu hangs since it cannot find the "drive" it is installed on...
Greg

---

### Post by r0ggins on 2012-12-08
I'm glad I found this thread before I installed Wubi and re-encrypted. That would have been a good 3 hours of wasted time.

---

