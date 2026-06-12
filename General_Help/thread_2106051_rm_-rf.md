---
title: "rm -rf"
date: 2013-01-17
forum: General Help
---

### Post by fhornplayer on 2013-01-17
I recently did a full wipe of Windows on a friend's computer replacing it with Ubuntu.  However, she's decided that she really doesn't like it and would prefer to have Windows back on her machine.

I've been looking up solutions online, but this seems to be a special case where the Windows installation disc is being completely by-passed, logging straight into Ubuntu regardless of the bios instructions.  There is no option for partition selection or formatting or anything useful.

So, I had the thought to use the "rm -rf" command to erase her machine and start from the ground up; however, I'm not entirely sure what in all this command entails... Will it erase the bios so that the machine won't even start?  Or will it simply erase all the working files/operating systems files?

My hope is that by erasing the operating system, the installation disc will be free to run its course.  Any and all help would be greatly appreciated!

---

### Post by sffvba[e0rt on 2013-01-17
No.  This will not accomplish what you seek.

Have you made sure that the BIOS is set to boot from the CD/DVD drive?


404

---

### Post by fhornplayer on 2013-01-17
I surely did.  The computer acts like it is reading the disc, but completely skips it and goes straight into Ubuntu...

---

### Post by sffvba[e0rt on 2013-01-17
> **fhornplayer said:**
> I surely did.  The computer acts like it is reading the disc, but completely skips it and goes straight into Ubuntu...

This is a long shot but may perhaps save a lot of time.  The next time you can hear the disc spin up, hit enter as Windows boot discs usually display a message, "Press any key to boot from CD/DVD".  Perhaps there is an issue with screen resolutions and the message is not displaying properly (long shot but you never know).

In any event, to re-install Windows you need to be able to boot from the disc, and nothing you do to your current Ubuntu install is going to have an effect on it.


404

---

### Post by sidzen on 2013-01-17
Do a search on "**How To Do Eveything With DD**" and/or download SystemRescueCD from either [*SystemRescueCD*]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") (for cd) site at [*unetbootin*]("http://unetbootin.sourceforge.net/") (for USB stick) and do the same with nuke utility.  You can wipe the drive with zeros, then reinstall what she what she wants.

---

### Post by fhornplayer on 2013-01-17
> **not found said:**
> This is a long shot but may perhaps save a lot of time.  The next time you can hear the disc spin up, hit enter as Windows boot discs usually display a message, "Press any key to boot from CD/DVD".  Perhaps there is an issue with screen resolutions and the message is not displaying properly (long shot but you never know).

In any event, to re-install Windows you need to be able to boot from the disc, and nothing you do to your current Ubuntu install is going to have an effect on it.


404

Ok, I tried it with no luck... The CD/DVD Drive seems to be in complete operation.  I'm completely puzzled as to why this is happening in the first place.  Any other thoughts that may help?  Thank you for the thoughts, by the way!

---

### Post by sffvba[e0rt on 2013-01-17
> **sidzen said:**
> Do a search on "**How To Do Eveything With DD**" and/or download SystemRescueCD from either [*SystemRescueCD*]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") (for cd) site at [*unetbootin*]("http://unetbootin.sourceforge.net/") (for USB stick) and do the same with nuke utility.  You can wipe the drive with zeros, then reinstall what she what she wants.

If the goal is to simply wipe the drive it can be done in a variety of ways.  You could also boot with your Ubuntu disc (if it will boot) or with Ubuntu on a USB, go into a live session and then use gparted to remove all partions on the hard drive.

I don't see this helping with getting Windows installed however.


404

EDIT: Have you tried your Windows media on another system?  Or booting Ubuntu on the problem system?

---

### Post by sidzen on 2013-01-17
you're right -- any LiveCD will work if the dd command is known, but this is a failsafe method 'cause i hate messin' with Windows

---

### Post by sffvba[e0rt on 2013-01-17
> **sidzen said:**
> you're right -- any LiveCD will work if the dd command is known, but this is a failsafe method 'cause i hate messin' with Windows

Please re-read the OP, the whole purpose of this thread is to re-install Windows.


404

---

### Post by SeanBlader on 2013-01-17
And to get back to your original question... nothing in Ubuntu will help to get Windows back. It will not clear the bios, it will not help the CD boot, and it will not continue to operate if you rm -rf which is "remove recursively and force without prompting". That's an effective way to make a paperweight if you don't know what you're doing.

It seems to me like your Windows disk itself is not bootable. This is pretty typical of older windows install disks, most windows upgrade disks, and a lot of recovery disks supplied with computers. Try it in another computer, try another Windows disk. And then check on the Windows help forums. As you can see the initial answers focused less on what you want to do, and more on what you wanted to try which is really of no help at all.

---

### Post by alphaamanitin on 2013-01-18
Good god how is this so hard?  What type of machine is it and can you find the MOBO manufacturer?  Nearly every MOBO will have a key, ESC, F2, or del are fairly comman, that you can hit and manually select your boot drive regardless of the boot order the BIOS has set.  I had a laptop that had issues with the BIOS working for selecting boot order so I always had to hit F12.  

Please provide the type (brand and model) of computer and if possible the brand of motherboard.  If that doesn't work than your Windows install disk is bad, as said before.

AlphaA

---

