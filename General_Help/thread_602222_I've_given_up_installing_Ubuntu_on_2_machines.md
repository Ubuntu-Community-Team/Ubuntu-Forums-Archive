---
title: "I've given up installing Ubuntu on 2 machines"
date: 2007-11-04
forum: General Help
---

### Post by samosamo on 2007-11-04
Friends, I ask you... what good is a laptop that wireless hardly works, and suspend causes it to crash?  If even Ubuntu can't do this, then linux is not ready for the desktop.  My options are slim, either use Vista which is my least favorite OS, or go back 5 years (feels like 100 years) and use the ancient XP.

Machine #1: My trusty Compaq v2000z.

I first tried with Feisty.  The bcm43xx driver proved too much to handle.  After I got the wireless actually working (as much as it could work) the wifi would not wake up after sleep/hibernation.  I called it quits at that point.

When Gutsy came out, I tried again.  Since I last tried someone wrote an easy installer script for bcm43xx with offline support.  Too bad offline support isn't ready for Gutsy yet.  Eventually get it working, and fire up fglrx for my ATI Radeon 200M.  Compiz is very pretty.  I'm exhausted from jumping up and down because I am so excited that my laptop runs Ubuntu now.   Time to go to sleep!  Oh, whats that?  fglrx is incompatible with Gutsys kernel?  Causes it to crash on suspend/hibernate?  Nice beta testing, jerks.

Machine #2: My HTPC.  Tried Mythbuntu (Gutsy)

Problem #1- I have 2 drives in RAID0 (bios).  Ubuntu live CD sees them both individually.  Did some reading (WHYY SO MUCH READING??) and found out I need dmraid installed.  But I have no internet.  ****.  Why wasn't dmraid included, what kind of dumb **** is this?  Its not a proprietary driver.  Its not developed by a company that gives no love for linux.  Whats the excuse?
Problem #2- it uses an ASUS PCI 802.11g card with the, yes you guessed it, the bcm4318 drivers.  This machine is not easy to lug to an internet cafe to plug into wired internet to start screwing with ndiswrapper.  I try a few tricks for about 2 hours to get it working, then give up.  I want my 2 hours back.  I'm a fool though, and I know I will try again when the ndiswrapper-offline-installer gets Gutsy deb included.

Let me also make it clear that I've been using Linux for years on server machines.  I believe there will be a day when linux will be ready for the desktop but not today.  Ubuntu is amazing so far, keep up the good work.

---

### Post by kidders on 2007-11-05
Hi there,

With all due respect, there is a difference between Linux not being able to do something, and *you* not being able to do it. I have been using Linux on desktops for years, with perfectly satisfactory results. Wireless networking, RAID, graphics & STR do work (and have done for some time) ... it's a matter of knowing how.

One suggestion I would make is to try Feisty, or a desktop build from another distro. You may have better luck with an OS that's more than a few days old. If that doesn't work out, not to worry ... Linux isn't for everyone! If it were, life would be kinda boring.

---

### Post by tashmooclam on 2007-11-05
It can be frustrating, and my Dell laptop with the broadcom card has unsatisfactory wireless. At least in 7.1 I could get some success, but the wireless is not robust.
My solution is I bought an Intel wireless card for $24, which should arrive shortly. Intel has Linux drivers on its website. Changing the wireless card is a simple operation on the Dell D600. 
I think that it's OK to spend $24 to switch to a good operating system.
Since I can sell my XP Pro disks on Ebay, I will come out ahead. I'll get at least $50 for them. 
I had also problems with suspend. 
It is true that Ubuntu seems to require that the computer owner has access to DSL or faster to really install the system. I don't know how I could have done it without it.

---

