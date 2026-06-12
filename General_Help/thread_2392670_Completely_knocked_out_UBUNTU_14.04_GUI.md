---
title: "Completely knocked out UBUNTU 14.04 GUI"
date: 2018-05-23
forum: General Help
---

### Post by mark allyn on 2018-05-23
Hello Everyone,

Somehow I managed to completely crash my 14.04 Desktop.  The crash has knocked out internet, cd drive, mouse, and I can't boot up.  I have no idea what I did.  Without internet or cd drive I can't reload the OS.

Any idea what to do other than simply throw the box out?

Regards,
Mark Allyn

---

### Post by Autodave on 2018-05-23
What DOES it do?  Boot up at all? What do you see when you start it?  Is this a desktop or laptop?

---

### Post by Frogs Hair on 2018-05-23
Is it a complete brick or do is there indications of hard-drive activity ?  This could be a hardware failure of some kind .

---

### Post by mark allyn on 2018-05-23
Autodave and Frogs Hair,

It is not a total brick.  I'm able to select the hard drive in the boot sequence (F9, F1) and following this the screen does come on and asks me to enter my ID.  When I do this and hit "enter" the screen remains illuminated but nothing happens at all.  I get no mouse cursor, the CD drive does nothing, and of course there is no file manager, no nothing except the illuminated screen.

Thanks for trying to help.

Mark

---

### Post by Autodave on 2018-05-23
When you say that the screen remains illuminated, exactly what is on the screen? If blank, is there any color or is just the backlight lit?

---

### Post by Autodave on 2018-05-23
Thinking some more: do you have a DVD with the install on it? Can you boot to the DVD? 

If you don't have the installation DVD, what happens when you choose the DVD at boot? Even w/o a disc in it, does the light light up and does it spin?

---

### Post by HermanAB on 2018-05-23
Hmm, try to boot with install media.  If that works, then you can recover your data for starters and once that is done, you can try to re-install.

As far as hardware failures go - bear in mind that even seemingly innocent things like faulty keyboards and mice can make a computer fail to boot.

---

### Post by deadflowr on 2018-05-24
Can you enter the recovery mode at boot?

---

### Post by mark allyn on 2018-05-24
Autodave, HermanAB, Deadflowr,

I have a CD/DVD with 14.04 on it.  The cdrom drive will not read it.  It will suck it in, the drive pilot light flashes a few times, and then nothing happens.  I have the tools to re-install the OS, but not the drive to do it.  I can't enter recovery mode either; in fact, the screen which gives this choice normally does not show up on my monitor.  BTW, I have desktop not a laptop, in answer to earlier question.  It's an HP Core Duo 34 bit box.

As far as what shows up after I type in my password, the answer is the same screen that was there before I entered the password.  The password window closes and leaves behind a wallpaper screen and a non-functioning cursor (arrow).

Thanks to all of you.

Mark

---

### Post by deadflowr on 2018-05-24
>  I can't enter recovery mode either; in fact, the screen which gives this choice normally does not show up on my monitor.

Try grabbing the screen manually by hitting the ESC or Shift key (depends if system is setup as legacy bios or UEFI, bios=shift uefi=ESC)
Do this when the initial machine Boot screen (the one with the machine's manufacturer or something related to that) goes blank.

---

### Post by Autodave on 2018-05-24
Just thinking here.........

You can get to the boot menu. I am assuming that the password you are talking about is the Ubuntu password and not a BIOS password. If this is true, then it sounds like a HD problem. However, the fact that you cannot boot to a CD would not be a HD problem. It does not sound like a memory problem, but it could still be.

Considering all of the above, I am thinking a drive controller issue even though the HD seems to be functioning somewhat since it prompts for password.

My suggestion? I would disconnect the HD and CD connector(s) from the mother board and make sure the connection is clean and tight.  And while you are in there, tell us what your HD cabl;e is: SATA or PATA.  SATA would be a wide (1.5" approx) flat cable and the power cable would have 4 colored wires going to it.  PATA cable would be about 3/8" to 1/2" wide.  

The HP Core Duo 34 you referred to is a laptop according to everything I found.

---

### Post by mark allyn on 2018-05-24
Hi Deadflowr

OK.  I discovered it is "shift" and booted to a recovery menu.  The screen shows 9 different items, starting with "Resume" and ending with "system-summary".  I'm guessing that "fsck" or "grub" is the item(s) to choose.  I'll start with fsck.  

Thanks for the tip!

Regards,
Mark

---

### Post by mark allyn on 2018-05-24
Deadflowr,

I ran "fsck", and then "resumed" the boot.  Same result as before: No mouse, no interntet, nothing shows up on the screen other than the wallpaper and a unmovable arrow.

Moving now to grub ...

Mark

---

### Post by mark allyn on 2018-05-24
Deadflowr,

Ah, dear me.  Now when I try to reboot and go into recovery mode, I can't get to the recovery menu. I selected the "advanced options" to try to get to the recovery menu.  The machine halts with a slew of messages, and then at the bottom of the screen there is a blinking light which does not respond to the keyboard.

I'm wondering if we're dealing here with hard disk issue.  I write this because the machine will boot normally from a USB solid state drive running 14.04.  I originally had thought I might have broken the BIOS but that doesn't seem to be the case.

I am not expert enough to know a test for a broken hard drive.  Or tests.

Regards,
Mark

---

### Post by deadflowr on 2018-05-24
> I am not expert enough to know a test for a broken hard drive. Or tests.
Yeah, hard drives be cracked.
if you can run from a usb and get internet try smart tools:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")
Backblaze has some (somewhat) helpful tips to look at:
[https://www.backblaze.com/blog/hard-drive-smart-stats/]("https://www.backblaze.com/blog/hard-drive-smart-stats/")

---

### Post by Autodave on 2018-05-24
If you can boot it to a USB HD, then it is probably time to replace the HD inside the case.

---

### Post by mark allyn on 2018-05-25
Hello Autodave and Deadflowr.

I suppose you're right.  I hate to abandon a lot of software that I took considerable time installing.

Thanks for your help.

Mark

---

