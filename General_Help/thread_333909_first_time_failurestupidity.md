---
title: "first time failure/stupidity"
date: 2007-01-08
forum: General Help
---

### Post by johnwillyums on 2007-01-08
I don't think I'm quite ready for ubuntu. I downloaded 6.10 and made a copy in Nero and then played it. I seem to have installed Gimp etc plus firefox, which I already use with xp and then realised I don't know what I'm doing. I have no idea how to make a partition and, every time I start up, the bios gets me to open xp so I don't know how to boot from disc. Can anybody help or am I not up to it yet? I just wanted to try ubuntu as I am attracted to the ethos and everything I've seen has intrigued me but I don't want to endanger a pc full of phpotos and music.:-k

---

### Post by oyvindaa on 2007-01-08
So what you're saying is that you haven't yet installed Ubuntu and your computer won't boot from the CD?

If that's the case then you've to go into your BIOS and make sure the computer boots from your CD-ROM.

The standard ways of getting into the BIOS is by pressing Esc, Del or F2. Depends on what brand your computer is, really.

---

### Post by spin2cool on 2007-01-08
When you boot your computer with the CD in the drive, the Live CD loads up and you'll get to try using ubuntu without doing any installation.  It's a great way to see if you like it.  Keep in mind that the installed version willbe much faster and will allow you to do much more custimization and stuff.

If you like what you see, you can install Ubuntu by clicking on the icon on the desktop.  After you get started with your ubuntu installation, you can find lots of help both here on the forums, and at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by Rhubarb on 2007-01-08
I advise you to backup your photos, music, and documents first.
As if something should go terribly wrong, you'd lose all your data.

Once you've got everything backed up, you can be as adventurous (and reckless) as you like.

Another button that might let you into the BIOS is F10 or F12.
You need to change your boot order so it boots from CD before your hard disk.

---

### Post by Clopy on 2007-01-08
Just watch your computer when it starts. It usually tells you which button you have to press to get into BIOS. There, search for an option named boot order or something similar. Make sure you choose CD-ROM first there, and after that, the hard disk. Press F10 to save and exit from the BIOS. Then your computer will boot from the live-cd.

---

### Post by johnwillyums on 2007-01-08
> **oyvindaa said:**
> So what you're saying is that you haven't yet installed Ubuntu and your computer won't boot from the CD?

If that's the case then you've to go into your BIOS and make sure the computer boots from your CD-ROM.

The standard ways of getting into the BIOS is by pressing Esc, Del or F2. Depends on what brand your computer is, really.
Thanks for your suggestions. I tried all of them and cannot get into the BIOS. Also my initial BIOS list says F2 for setup and F11 for boot menu so I tried both of those and nothing. On the second page I get a choice between Windows XP and Windows recovery console plus Press F8 for troubleshooting. I tried that and all it does is stop the countdown to open XP. I'm stuck.

---

### Post by Rhubarb on 2007-01-08
Ok, I've got 2 solutions that might help you.

(1) As soon as you turn your PC on, press the F2 button repetitively until it lets you into the BIOS

If this doesn't work, then
(2) Are you using a USB keyboard (rectangular plug)?  If you've got a spare PS/2 (circular plug) keyboard, plug that in instead and try solution number (1) again.

Most old PCs BIOS (Pentium 3 and older) don't recognize a USB keyboard until the operating system is loaded.

Hope this helps (anything to help GNU / Linux claim another PC) :)

---

### Post by johnwillyums on 2007-01-08
Dear Rhubarb. Thanks. I got into the BIOS by pressing F11 and selected the cd drive to boot from. This got me to a menu and I checked the integrity of my disc. No problems. I then clicked start or install ubuntu. This got me a dark screen with the ubuntu logo and a bar with a moving orange light. This carried on for several minutes and then I got a page of MSDOS (I assume) with a small white bar at the bottom. I left this for ages assuming it would move on from there but it remained the same. I tried pressing several F keys plus escape plus alt/del but nothing happened. After about 15 minutes nothing had changed so I pressed the escape button on the tower and rebooted windows. So that where I am now. I still haven't managed to run ubuntu and am unsure about where to go from here. Also I don't know how to partition off the windows section on my drive. As you say anything to help GNU claim another PC but it's a pretty scary process when you are as inexprienced as I am. I am running a celeron D 3.06 with a gig of ram and I have a half full 80gig c drive plus a 120 gig d drive both using XP home

---

### Post by Rhubarb on 2007-01-09
We're almost there, hang on a bit longer!

It sounds as if your burn of the Ubuntu iso disc image was bad.
If you've got a burnt copy of Ubuntu, then please burn another copy of it - but make sure to burn it at a really slow speed - say 4x or 8x.

If you try to boot from the newly burnt CD or are using the pressed Ubuntu CD that you got via snail mail, and you still can't boot up properly into the live CD environment, then I suspect it could be your optical drive at fault - you might need to buy / borrow a newer one.

If you do manage to boot from the live CD nicely it should take you into a nice orange desktop where you can move your mouse around / play games / do whatever you like.

Once you are here double click on the install icon on the desktop.
Follow all the prompts, when it asks you how you wish to partition the drive, tell it to resize the existing partition (it should default to around 60% on a blank drive (you're isn't blank) - you can change this if you wish).
Then let it install.  There you are, you've got a dual boot system, and will be presented with a menu to boot into windows / ubuntu on start up.
*Note: If you do want to install, defragment both drives in windows first, and when installing make sure it's to your 80GB winxp drive to resize and install to

It does sound a bit weird that it'd found no defects on the CD - try reburning it at a slower speed anyway.
The DOS prompt you were assuming - could you type stuff in there?
If it was a blinking cursor (and not much activity from your optical drive), that's ok, just let it blink there for another 15 minutes (it should only take 30s, but I've known it to take longer).

Hope all this helps, I know there's a nice guide that helps you get things going somewhere, but you seem to be experiencing some odd problems there indeed.
As always report back here and let me know how it turns out (fingers crossed).

---

### Post by johnwillyums on 2007-01-14
Dear Rhubarb and anyone else.
Thanks for your helpful suggestions. I downloaded a fresh copy of 6.10 from canonical and burnt it at 8x. I then went through the procedure again, checked the discs integrity-ok- and then rebooted. I booted from the disc and once again got a dark screen with the ubuntu logo and a flashing orange bar, after a few seconds this changed to a dark screen with a flashing cursor at the top which quickly moved on to a page of code with a cursor at the bottom. I tried typing but nothing happened. The code meant very little to me but I could see do_page_fault plus some numbers and "fixing recursive fault but reboot is needed!", also "BUG:unable to handle kernel NULL pointer dereference at virtual address"
I left this for about 15 minutes but nothing changed so I pressed the red reboot button on my tower and went through the same process again. This time the code page seemed to be flashing upwards so I was quite hopeful that something was happening, however as I stared at the flashing code it seemed to me to be just flashing rather than changing in terms of numbers or letters.
I escaped and tried again and this time the flashing screen eventually stopped flashing and once again showed a steady page of code. This time , amongst other things I could see "kernel panic-not syncing:fatal exception in interrupt" and BUG:unable to handle kernel paging request at virtual address ffffd370"
So that's where I'm at now, any suggestions would be welcome. Cheers, Johnwillyums

---

