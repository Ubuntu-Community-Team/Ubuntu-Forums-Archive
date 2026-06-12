---
title: "How do I make a backup image of my OS in Lubuntu 19.04?"
date: 2019-11-12
forum: General Help
---

### Post by iconoclast12 on 2019-11-12
I have an Atomic Pi with Lubuntu 19.04 installed onto the onboard storage (not an sd card). What I want to do, is just create an image of my entire installation. Online documentation is either outdated, or does not apply to my situation, so I do not want to use online docs as a reference to do this, because I have done this before and all it did was break my setup.. In windows, this is a fairly easy task using something like win32 disk imager, and since I'm more of a Windows guy, I'm well versed in understanding how to do it in Windows, but I'm no Linux guru.. I spent days getting this setup working the way I want it to, so I cannot afford to screw it up attempting to create a backup and not having a full understanding of what I'm doing.. But, I also cannot afford to have this break on me again in the future and NOT have a backup ready to restore it to the way it is now.. I NEED a backup..

1) I want to keep this as simple as possible.

2) I want to use a GUI utility to do this if at all possible and not the command line.

3) I'd like for someone to explain to me, in lamens terms, how I can create a backup image of my system in the simplest way possible without using any fancy commands or Linux jargon..

Honestly, if I could use a tool like win32 disk imager, where I can just pick the drive I wanna read from and then write an image to my desktop and choose a name for, that would be awesome....but I'm not aware of any utilities like this that will work with Linux.

Keep this in mind.. The onboard storage of the Atomic PI is part of the board, so I cannot remove it or take it out and put it into a Windows machine to create an image of it.. It will need to be done within Lubuntu somehow.

Can someone please help me with this?

Thanks!

---

### Post by tea for one on 2019-11-12
Have a look at Clonezilla [https://www.clonezilla.org/](https://www.clonezilla.org/)

I am not familiar with an Atomic Pi so you may have to experiment a bit.

Is it correct that your device doesn't have a usb port? If so, then Clonezilla will probably not be suitable

---

### Post by iconoclast12 on 2019-11-12
I have available USB ports, yes. I was hoping to write the image to a flash drive, actually..

---

### Post by tea for one on 2019-11-12
That sounds good.

You will need two usb ports - one to boot Clonezilla in a live session and the second for another usb drive where you will store the image.

Have a look at the Clonezilla website, where there is a wealth of information.

The Clonezilla interface is not particularly modern-looking but it does the job. 

Good luck

---

### Post by GhX6GZMB on 2019-11-12
Try Timeshift. Works for me and is easy to use. It's based on rsync.

---

