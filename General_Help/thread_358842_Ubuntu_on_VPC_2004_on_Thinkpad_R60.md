---
title: "Ubuntu on VPC 2004 on Thinkpad R60"
date: 2007-02-11
forum: General Help
---

### Post by tisgrandupnorth on 2007-02-11
First up, my knowledge of Linux is small. Tiny.  I know lots about Windows, but nothing about Linux.  But I want to come to the other side.

I'm trying to install Ubuntu 6.10 from an iso on Virtual PC 2004 5.3.582.27 running on a Lenovo ThinkPad R60, which has an ATI Mobility Radeon X1400.

We work fine until I have gone past the 'Start or Install Ubuntu' option, through the loading screen and the come into the screenie below.

[IMG]http://computers.drewgraham.net/images/external/ubuntuvmscreenie.jpg[/IMG]

This, to me as a Windows guy, says display driver.  But is it the VM display driver, or the laptop display driver?

I have tried various resolutions and colour depths, as well as the VGA=771 option recommended on the Help at the boot screen, but it only makes the corruption look different at best.

Can someone point me in the right direction please?

---

### Post by davidvasta on 2007-02-11
Are you using the GUI installer or the text installer?

I have found in the past that using the text installer works better and give linux a chance to install and find the hardware later. You might try when you hit the first screen typing in TEXT and letting the text install run, It's not as sexy but it might work?

I found this[ link to a how too.]("http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx")

This post sounds like he is having the same trouble you are. VirtualPC does not emulate the video card you have . I think it uses an smaller Intel Card in the virtual mode or that is what it is as far as the VPC knows.

-David

---

### Post by tisgrandupnorth on 2007-02-11
David,

Many thanks.  I came across that post when doing the google, but couldn't figure out where he'd got to - he said he's installed it through a 'default install'.?

Sorry to be a complete noob, but where do I type 'text'?  I've tried typing it at the F1, F2, F3 etc, gui and pressing escape and typing it, but with no success.

I'm hoping to give the vpc a go before making my laptop dual boot.  I already run Windows 94 - 2000 as VPCs, but, obviously, I've not had any problems so far

Should I have downloaded the alternate CD for a textual install?

---

