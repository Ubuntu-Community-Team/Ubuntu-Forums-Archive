---
title: "Can not get into bios.  Want to install ubuntu."
date: 2020-01-12
forum: General Help
---

### Post by Tom_Carr on 2020-01-12
I have a dell optiplex running Windows 10.  I want to intstall ubuntu.  I inserted the DVD, which has worked fine for other installs, and turned on the compute but when the computer boots up, it looks at the DVD but then opens from windows on the hard drive.  It must be the boot sequence so I tried getting into the bios, using F2, then tried F12, then tried several advanced options I found on line but nothing lets me get into the bios. 

I can open windows file manager and see the  ubuntu  DVD.  Is there anything I can click on the DVD that will let me install it, even though windows is running?

---

### Post by Quarkrad on 2020-01-12
F2 appears to be the way to go.  Are you tapping it fast enough, soon enough and long enough after switching on?

---

### Post by Autodave on 2020-01-12
Turn computer on and instantly start tapping the F2 key.  Do NOT press it down and hold it: tap it quickly and continually.

---

### Post by Tom_Carr on 2020-01-12
I have tried F2 just as described, several times.  It doesn't work, and I'm not the only one who has this problem.  Do a google and you will find other people with the  same problem, and various solutions, none of which work for me.  Is there a way to install ubuntu while windows is running, from the file manager?

---

### Post by dragonfly41 on 2020-01-12
Not from the file manager.
Starting with Windows 10 some time ago (on a Dell) these are the steps I remember following:

shrunk internal drive size to create space for Ubuntu (if internal Ubuntu is preferred)
installed Rufus
purchased a USB flash drive (8GB +)
downloaded Ubuntu 18.04 iso
burned LiveUSB using Rufus
used F12 to set one time boot option SansDisk
launched "Try Ubuntu" (do not trigger "Install Ubuntu" until you are ready)
experiment with Ubuntu

My advice would be to focus on installing Ubuntu on an external HDD in a container or better still an SSD, perhaps 1TB.
I have an SSD in a Startech two bay docking station.

Regarding F2 / F12 I found this ..

[https://www.dell.com/community/Laptops-General-Read-Only/Unable-to-enter-bios-setup-with-F2-key-on-boot/m-p/4223360#M772362](https://www.dell.com/community/Laptops-General-Read-Only/Unable-to-enter-bios-setup-with-F2-key-on-boot/m-p/4223360#M772362)

---

### Post by CelticWarrior on 2020-01-12
> **Tom_Carr said:**
> I have tried F2 just as described, several times.  It doesn't work, and I'm not the only one who has this problem.  Do a google and you will find other people with the  same problem, and various solutions, none of which work for me.  Is there a way to install ubuntu while windows is running, from the file manager?

If nothing else works - I really doubt it but for the sake of argument I'll assume it's true - you should be able to [access UEFI settings (which you call BIOS but really isn't for more than a decade now) **from Windows**]("https://itsfoss.com/access-uefi-settings-windows-10/") . When there, besides selecting the intended boot order, also make sure to disable Fast Boot to make it easier to use the assigned key (F2) next time, without the help of an already installed OS.

Please note that the above method has nothing to do with installing Ubuntu from Windows.

---

### Post by yaminb on 2020-01-12
> **Tom_Carr said:**
> I have tried F2 just as described, several times.  It doesn't work, and I'm not the only one who has this problem.  Do a google and you will find other people with the  same problem, and various solutions, none of which work for me.  Is there a way to install ubuntu while windows is running, from the file manager?


One thing to check. Is your keyboard plugged into the USB? If it is, pay attention to the lights on the keyboard. 
Do they come up when you first boot your computers? If it is lit up, that means your keyboard is working.

If the lights don't come up, that means the keyboard is not 'started' yet and so F2/DEL or whatever won't do anything.

One 'workaround' you can try is to use the 'reset' button on your PC. I'm not sure if your specific computer has one.
Basically boot normally as if you're booting into windows, then press the reset button after you see your keyboard light up (NOT THE POWER BUTTON).

Then when it boots, press F2 to boot into the BIOS.

---

### Post by CatKiller on 2020-01-12
> **yaminb said:**
> One thing to check. Is your keyboard plugged into the USB?

Along similar lines, what the initial no-OS part of the boot sequence *really* likes is a PS/2 keyboard. Everything else is a substitute of varying quality. So a keyboard might work fine plugged into a USB 3 port when there's an OS loaded, but would need to be in a USB 2 port when there isn't; or might not work in *any* port with no OS unless "Legacy USB Support" is turned on to convert USB signals into PS/2 ones.

Being able to turn on Legacy USB Support, or to turn off Fast Boot, requires being able to enter the BIOS Setup in the first place, of course. Welcome to PC troubleshooting. Being able to select to boot directly into the Setup from within an OS is one of my favourite innovations of UEFI. Without that you need to reset the BIOS to defaults and hope that they're sensible.

---

### Post by oldfred on 2020-01-12
One more, along similar lines.

Cold Boot.
If fast boot in UEFI/BIOS is on, you often do not have time to press f2 or f12.
But cold boot or full power down, if laptop remove battery. Hold power switch for 10 seconds to drain all power. Then a cold boot should force UEFI to do a normal start not a fast boot. So then you have a short time to press f2.

---

### Post by sgage on 2020-01-12
Seems to me this issue would be better addressed on a Dell forum. It is not an Ubuntu issue.

---

### Post by Tom_Carr on 2020-01-13
More info:

It is an optiplex 3040

The keyboard is a dell, pluged into usb, and the light on the keyboard comes on right away.

However, the "Dell" logo never comes up on the screen.  The screen just stays dark for a while, then starts to load windows.

If I hit F2 a few times when I turn on the power, the screen stays black and windows never comes up.    If I then hit escape, it brings up windows.  This suggests that the keyboard is working fine, but the monitor is not.  It may be in the bios setup but I just can't see it.  Then when I hit esc it exits bios.  I am going to try another monitor.

---

### Post by CatKiller on 2020-01-13
> **Tom_Carr said:**
> However, the "Dell" logo never comes up on the screen.  The screen just stays dark for a while, then starts to load windows.

That sounds very much like Fast Boot (aka the BIOS option that means you can never get back into the BIOS) is enabled. It skips most of POST, hardware detection, and simply loads exactly the thing that it loaded last time.

The two options for correcting that are given upthread.

---

### Post by Tom_Carr on 2020-01-13
Problem solved !!!

There were two monitors plugged in to the computer.  It had some kind of dual monitor configuration.  One of the monitors was not plugged in to power and never came on.  I unpluged it, and now the bios comes up on the other monitor, which I thought was the only monitor.

Thanks everyone for your help on this.  Now that the problem is solved there is a feeling of exhilaration.

---

### Post by VMC on 2020-01-13
Try booting from a USB flash instead of DVD.

---

### Post by Tom_Carr on 2020-01-13
> **VMC said:**
> Try booting from a USB flash instead of DVD.

Will do.  I need to read up on how to do that, but I definitely want to learn.

---

### Post by Tom_Carr on 2020-01-13
I am so far behind the times.  I will have other questions.  Not sure if I should start a new thread or just keep asking questions here.

---

### Post by CatKiller on 2020-01-13
> **Tom_Carr said:**
> I am so far behind the times.  I will have other questions.  Not sure if I should start a new thread or just keep asking questions here.
New threads. And marking solved threads as solved. 

You want people that know about whatever the new issue is (that wouldn't necessarily know about your old issue) to be able to find your thread, and we want people that have the same issue to be able to find solutions. You can always add a link to a prior thread if you feel that it adds needed context.

---

### Post by Tom_Carr on 2020-01-13
I will mark this thread as solved and start a new thread.

---

