---
title: "Blank CD in ubuntu but read in Windows"
date: 2016-04-19
forum: General Help
---

### Post by christine4 on 2016-04-19
I am running Ubuntu 14.04, and I require assistance in how to view images on a burned CD. I have done countless searches, and none turned up specific solutions to my problem. 

When I insert the burned CD, the message: *"Unable to mount blank CD-R Disc, location is already mounted"*, appears. I am then prompted to choose a program to read it. Image Viewer, does not recognise CD data. Shotwell, doesn't even show a CD listed in its menu. I do get an icon on my navbar however, and when I click, it shows the title of the disk, with no files listed.

Paradoxically, the images on my burned CD, are read by another computer, running Windows.

The optical drive is obviously mounted in Ubuntu. Audio CD's and DVD's, run automatically when they are inserted too. The optical drive is working and the software exists to play other disks. There's seems to be a prejudice against reading burned ones though. You would think it was a burn problem, but the images show up perfectly in Windows, on a separate computer.

So how do I start to look for the problem, in order to fix it?

QUERY: could it be a driver issue? I've looked for driver updates for my Pioneer brand, but it only shows up for "Windows" OS. Do I have to look for a Linux one, or can I just install the Windows and Wine can decipher it?

---

### Post by T.J. on 2016-04-19
Have you tried opening the disc in your file manager?  If it appears to be blank, even though it contains data, it is possible that data was written to the CD, but the session was left open.  Until an open session is closed, the disc will be unreadable except on the system where the session was started.  Not all Windows programs close burning sessions properly.

---

### Post by DuckHook on 2016-04-19
Hi christine4 and welcome to Ubuntu and the forums.

Yours may be a hardware problem. Some optical drives have trouble reading burned CDs because such CD tracks are not made up of physical peaks and valleys (as exist in commercial CDs and DVDs), but are composed of dyes that change colour through the application of heat from a laser (the "burning" process). Your Windows optical drive may be more sensitive to burnt disks than your Ubuntu one. If so, then there is nothing you can do with the operating system to solve it.

Ubuntu comes with most drivers baked into the kernel, so there is usually no need to install additional drivers. The fact that you can play audio CDs and DVDs means that the system has the proper drivers already, recognizes the optical drive, and is accessing it properly.

Your Ubuntu machine's optical drive might also be too old to recognize specific types of discs. When writable drives were first introduced, they were split into two classes: there were CD-R drives and CD+R drives and some of them couldn't read disks burnt using the opposing standard. Newer optical drives can read disks of either format, but if your optical drive is too old, this might be the problem.

Try swapping your Windows optical drive into your Ubuntu machine and see if that works. If it does, then the problem is definitely with hardware (the drive) and not with software (Ubuntu).

---

### Post by christine4 on 2016-04-19
Thanks, to both of you. Your feedback gave me some other things to evaluate, and I suspect I now know the answer. 

The most likely candidate seems to be  hardware. I managed to get file manager to read a disk I burned in 2011  (in Ubuntu) thanks to TJ's suggestion. Some of the images came up, or none at all. Some  images only managed to half download. Which tells me, its a reading  issue with this particular optical drive, per Duckhook's suggestion. So I will now mark this as solved.

Thank you for taking the time to reply so promptly. :D

---

### Post by christine4 on 2016-05-05
Just as a follow up, I purchased an external DVD burner/drive, which I plugged in via USB. I got access to the pictures immediately. So it was the built in burner, having problems reading it.

Thanks for the suggestion DuckHook.

---

