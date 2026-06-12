---
title: "Removable media and Ubuntu"
date: 2006-11-07
forum: General Help
---

### Post by ramiro on 2006-11-07
I noticed that Ubuntu will automatically mount removable media as async. What this means is that data will not be written to the device immediately, rather it is stored temporarily in memory and then written later. While some people say this is a huge advantage especially when removable media is used a lot (such as a bootable USB stick) in general this causes problems when I want to use a memory stick to transfer some data and when I unmount the drive and pull out the stick, the data isn't there!

I currently ensure that the transfer is finished by watching the flashing light on my usb thumbdrive, but the sd card reader in my laptop doesn't have such a light. The next thing I did was manually unmount it in the terminal, which would wait for the write to finish before giving me control of the terminal again, so at least I know when I can remove the disk.

This is obviously not a good solution for the average person, and since my girlfriend is now using Ubuntu 6.10 on her laptop and is using the SD card reader in there, I don't think this is a very good solution to the problem.

What I would like to know is:

1) is there an easy way to make removable drives mount as sync by default, as a temporary solution?
2) in future versions of Ubuntu, could this be the default (or at least give users the option somewhere, such as in "removable drives and media" preferences
3) if not, then at least notify the user that the drive is writing data and do not remove it. Nautilus by default simply unmounts the drive I imagine but doesn't wait for the process to be finished. At the very least it should give a progress bar saying "data is currently being written to the device, do not remove yet" or something along those lines

But for now, some way to make it automatically mount async would be good as this would solve quite a few issues

---

### Post by CatKiller on 2006-11-07
I thought you got exactly that kind of progress bar if you right-click on it and select Eject.

---

### Post by ser1alsn1per on 2006-11-08
if i pull out my usb drive in edgy with out right clicking and ejecting a pop up box comes up and says unsafe removal next time right click and eject

---

### Post by ramiro on 2006-11-09
nope, if I right click and then click eject, I get nothing. No popup window, no progress bar, nothing. (Nte that 6.06 had a little icon that said "writing data, please wait" or something to that effect, but no longer in 6.10)

even under 6.06 after the popup had gone away, it was STILL writing to the removable device. removing it was unsafe. In edgy it doesn't seem to even show the window, so there is no notification of when it was safe to unmount

---

### Post by givré on 2006-11-09
> **ramiro said:**
> nope, if I right click and then click eject, I get nothing. No popup window, no progress bar, nothing. (Nte that 6.06 had a little icon that said "writing data, please wait" or something to that effect, but no longer in 6.10)

even under 6.06 after the popup had gone away, it was STILL writing to the removable device. removing it was unsafe. In edgy it doesn't seem to even show the window, so there is no notification of when it was safe to unmount
Hum, do you actually use gnome.
1. You have the popup when you eject.
2. The popup finish when eject is finish.
At least that's how it works for me and for almost every people.
Your problem is rather strange.
Did you do an upgrade from dapper, or whatever that could lead some importnat package left ?

---

### Post by Timokl on 2006-11-13
> **ramiro said:**
> even under 6.06 after the popup had gone away, it was STILL writing to the removable device. removing it was unsafe. In edgy it doesn't seem to even show the window, so there is no notification of when it was safe to unmount

Edgy seems to have a problem with flash card readers in general. In Dapper, my card reader worked smoothly out of the box, after upgrading to Edgy, nothing happened after plugging in a card.

Now, my digital camera's SD card seems to work, but my smart phone's memory stick is not recognized, yet.

You may want to take a look at the following thread which helped me: [http://www.ubuntuforums.org/showthread.php?t=200360]("http://www.ubuntuforums.org/showthread.php?t=200360")

Bye,
Timo

---

