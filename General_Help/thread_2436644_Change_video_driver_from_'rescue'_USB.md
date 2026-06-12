---
title: "Change video driver from 'rescue' USB"
date: 2020-02-10
forum: General Help
---

### Post by Nick Hopton on 2020-02-10
A few weeks ago I installed a new GEFORCE GT 730 graphics card and I also installed the 'Recommended' NVIDIA driver.

This was fine until yesterday, when I added a second monitor to the system. The display on the second monitor was not correct, it 'overfilled' the screen. At this point an evil maggot in my brain told me to try a different driver, which I did. The result of doing this was the complete loss of picture on both screens, the booting process stalled, apparently at a memory check.

Fortunately I had rescue system installer on a USB stick and using this it was possible to live boot the machine. My problem now is how to use the 'live' system to change the driver settings back to how they were  before (I can live with one monitor for the time being). I wonder if there is a config file I can edit to do this? Failing that any suggestions or pointers to a solution would be greatly appreciated.

Ubuntu 18.04 

Nick.

---

### Post by CelticWarrior on 2020-02-10
Some of us would appreciate elaborating on the second paragraph ;) (I know I would)

Please describe what you did to change the driver and to which one. And please clarify what happens when you try to boot normally (not the Live USB), how far it goes...

---

### Post by CatKiller on 2020-02-10
> **Nick Hopton said:**
> My problem now is how to use the 'live' system to change the driver settings back to how they were  before (I can live with one monitor for the time being).

The process is pretty straightforward. You'd boot your live system, then you'd mount your installed system's partition. Then you'd use chroot to say that / is that partition's mount point, so any commands that you run would be done as if you were running them on your normal install. Then you'd uninstall whichever incorrect driver you'd installed, and potentially reinstall the correct one.

We don't have enough information to help with the last step, as CelticWarrior says.

---

### Post by Nick Hopton on 2020-02-10
In the first instance the Ubuntu driver installed automatically by default when I installed 18.04. In the second instance I used the GUI provided to install the 'Recommended' NVIDIA driver. Both worked, getting back to either would do nicely. I can't give you the details of the driver that's causing the problem, I didn't keep notes and of course the machine is currently 'operating in a mode of non-functionality' so I can't check that way. During booting the machine hangs at what appears to be a memory or file check of some kind.

---

### Post by Nick Hopton on 2020-02-10
Booting fails with a flashing underscore cursor and this message on an otherwise black screen: 

/dev/sda1: clean, 719434/61054976 files, 96553187/244190208 blocks

Then nothing!

---

### Post by CatKiller on 2020-02-10
That message is just information that the standard filesystem check has been done. It's not got anything to do with your graphics issue, it just happens to be the last message displayed before it starts the graphics system, which then fails because of the broken driver installation.

Since you can't remember which one you had and which one you installed it's probably best to just purge all the nvidia stuff and then install just the one driver package. I'm sure either package would have been fine, but the presence of the first one prevented the installation of the second one; the nvidia driver doesn't switch cleanly between branches.

Since your graphics card is still supported, you can just go for the highest-numbered branch you have available after you've purged all the nvidia stuff.

---

### Post by Nick Hopton on 2020-02-10
Well yes, but the problem is that that the system isn't working, it won't boot. How would I do what you suggest from the 'live' system running from a USB stick?

---

### Post by CatKiller on 2020-02-10
> **Nick Hopton said:**
> Well yes, but the problem is that that the system isn't working, it won't boot. How would I do what you suggest from the 'live' system running from a USB stick?

Chroot, as I said in my first post. 

There's plenty of information available on how to do package management from the command line.

---

