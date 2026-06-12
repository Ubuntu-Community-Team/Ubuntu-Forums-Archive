---
title: "Wubi Install on other Partitions"
date: 2007-07-17
forum: General Help
---

### Post by Orbital75 on 2007-07-17
I am looking at different method for installing Ubuntu and just recently ran across Wubi.

Here is my Question....

I have 3 Hard Drives in my System and am curious if I can install Wubi on anything other
than the IDE 1 Master.

I have  C: and D: partitions on my Main IDE 1 " Master "
On my second Drive, I have a G: Partition which is on IDE 1 " Slave ".

Of course E: and F: are Optical Drives.

I also have a H: drive that I use to edit my Home Movies... 

So, can I install Wubi on my G: Drive or does it have to be on the Same Drive as Windows.
All drives are formated in NTFS.  

I guess I could put it on D: if I had to but since I only have a 40 gig drive space is kinda limited
I think I have 16 gig free on the D: partition and 6 gigs free on my C:

Thanks for your help, this may be the way to go.

---

### Post by ago on 2007-07-17
You should be able to install wubi on any drive with enough free space

---

### Post by Orbital75 on 2007-07-17
Thank you...... I'm thinking about putting it on my Slave Drive ( G:) .
Let's cross or fingers.  

Oh how much Space will it required after it's all loaded up?

I have 6 gigs free on C: but of course XP needs room to breath.

---

### Post by ago on 2007-07-17
I would install 6-8GB whatever you can spare, if it's for a quick try 4GB will do, but then you will not able to install much software.

---

### Post by Orbital75 on 2007-07-18
Thanks...... One other thing.  As you can tell I am very cautious before I try something.
I lust like to know what I'm getting into before I just install something.

I've read that Wubi is prone to Hard Boots.  What does that mean?
I am familiar with Cold and Hot boots but what is a Hard Boot.

Any gotcha?
" Wubi filesystem is more vulnerable to hardreboots (unplugging the power) than a normal filesystem, so try to avoid them. "

Thanks

---

### Post by porcorosso on 2007-07-20
I'm no expert on this, being only in the process of downloading the alternate .iso as I type this message, but I think "hard reboot" is referring to a hardware-instigated restart of the system. In other words the system loses and then regains power, or someone hits the reset button. That's not good for Windows, either. But with Wubi the Ubuntu installation is done to a virtual disk which itself resides as a single file on the Windows file system. If the computer is restarted improperly then the Windows partition would be starting with the "dirty bit" set, meaning the system wasn't shut down properly. That's what I know. The next paragraph is what I've surmised.

It's possible that the dirty bit being set causes autochk, a component of Windows which checks the ntfs system partition at boot time if the dirty bit is set, to run. And that may interfere with the boot loader. Or, perhaps, there's some other effect that interferes with being able to load Ubuntu after a hard reset. That's my guess anyway. I've only posted this because I saw that your post had gone unanswered for a couple of days.

I imagine these guys are pretty busy, what with the development cycle and trying to tend to newbs like me.

---

