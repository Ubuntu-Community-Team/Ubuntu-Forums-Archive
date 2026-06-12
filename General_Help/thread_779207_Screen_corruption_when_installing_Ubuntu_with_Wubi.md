---
title: "Screen corruption when installing Ubuntu with Wubi"
date: 2008-05-02
forum: General Help
---

### Post by OMA2k on 2008-05-02
Hello, I've tried to Wubi-install both the regular Ubuntu 8.04 and Kubuntu-KDE4, and in both cases I got a corrupted screen after rebooting into the Ubuntu install (check the attachment to see what I'm seeing). I can see the ubuntu/kubuntu boot logos with the progress bar, but after it starts Xorg, then I see nothing but garbled colors.

It seems only a display issue, because even if I can't see anything but the colourful corrupted screen, the install goes on fine, and then proceeds to reboot into the OS, but again with corrupted display.

This didn't happen when I installed Ubuntu without Wubi some time ago in a dedicated partition (it wasn't 8.04, though), so I don't know if some part of Wubi could be causing this. Maybe it's something related to 8.04, I don't know.

Is there any way to try to fix this?

---

### Post by wilsonq77 on 2008-05-02
That is what I got on the VGA channel too but after the page with the language selection.

What vidio card are you using and what resolution is set??

---

### Post by wilsonq77 on 2008-05-02
I used Wubi and the iso off my hard drive and after the reboot (Note correction) I got exectly what you got.  I hit enter a couple of dozen times and after some hard drive thrashing it rebooted.  When i tried to boot to Ubuntu I got the same screen issues.  The VGA channel has a blank, black screen with an error message "out of range signal...change to 1920X1200@60Hz" which is interesting because that is what it's set to.  The DVI-D channel has a flashing orange screen and ctrl-alt-+ changes it a bit but only to wierd lines.

The logo is crisp and clean on boot and then well, houston we have a problem.

I also ran a diagnostic on the Nvidia card and it seems ok.

---

### Post by OMA2k on 2008-05-02
Hi, my card is a nVidia too, but it's an old one. It's a nVidia TI4200, manufactured by Creative. My monitor reports that colourful screen as a text mode screen, so something goes wrong at that point and the proper graphic mode isn't even started. Weird.

Did you try to make a regular Ubuntu install? (non-Wubi)

---

### Post by ago on 2008-05-03
Press ESC after Ubuntu at boot and select safe graphic mode
You may also try the Live CD, but I'd be surprised if it behaves differently

---

### Post by wilsonq77 on 2008-05-03
Okay, I worked out a partial solution.  Thanks to ago and the sticky up there.

I downloaded a new Wubi 8.04 to its own folder on the C: drive.  I moved the iso to that folder and ran Wubi.exe and it started.
On the first boot you have to get to that esc key really fast.  Otherwise the loader get going and all the choices that pop up on the boot menu are normal or recovery mode.  If you get to the esc fast, ASAP (emphases needed) then you get the menu with "safe graphics mode".  For some reason Wubi will default to manual.  Click the "install" icon on the desktop and fill in the stuff.  At the partitioner you need to add a / and /usr and a swap into the empty space and after about 5 minutes of making mistakes you get running.

The screen coruption is still there in normal mode.  I'll try to get new drivers loaded as time permits.

But hey, if you use "safe graphics mode" she all works :)

---

### Post by daheshan on 2008-05-03
oh man..does this mean I can't run Ubuntu in normal mode without partition?

---

### Post by OMA2k on 2008-05-03
Ok, you're right, ago. I tried to burn the ISO to a CD, booted the LiveCD and after the CD menu and the boot logo, I got the colorful corrupted screen as well, so it's nothing related to Wubi.

In that case, it must be an issue with the new 8.04 version of Ubuntu, since I've installed in the past other versions of (K)Ubuntu in this machine with no display problems. Hardware support should be better in newer versions, not worse, shouldn't it? :)

---

### Post by ago on 2008-05-03
Both wubi and the Live CD provide a safe graphic mode (and there are some extra options too on the Live CD). Probably if you google for the make and model of your card you will find some advice.

---

### Post by OMA2k on 2008-05-04
I'll check elsewhere about this issue.
Thanks for your time, ago!

---

