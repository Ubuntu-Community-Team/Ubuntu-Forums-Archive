---
title: "Ubuntu Won't Bootup Since Update"
date: 2008-06-07
forum: General Help
---

### Post by OpVines on 2008-06-07
I've been using Hardy for a few weeks and today I got an update. So I did the update and restarted my computer, except now it won't get past the bootup screen where that orange bar is going back and forth. It goes forward for like 3 seconds then completely stops. I even waited like half an hour to see if it would continue booting up but it doesn't. Recovery mode locks up to. The last line is "29.490269 ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1" then it completely stops too.

Can anyone help me figure out how to fix this so I can use my computer?:mad::mad::mad:

Even the Gutsy CD I had from before won't even boot. It gets locked up at the screen where the bar is loading...

---

### Post by d.kusummmanth@gmail.com on 2008-06-07
contact some forum admin by PM.

---

### Post by saratchandra on 2008-06-07
Try booting to the old kernel

---

### Post by OpVines on 2008-06-07
None of the old kernels work. The exact same thing happens. And who are the forum admins I should contact then?

---

### Post by saratchandra on 2008-06-07
I'm no expert, but try booting into the recovery mode to check where its exactly stopping to boot.

---

### Post by OpVines on 2008-06-07
Sarat, if you read my post, it says I tried recovery mode and where it exactly froze.

---

### Post by saratchandra on 2008-06-07
Sorry OpVines, its too late in the night;)

---

### Post by OpVines on 2008-06-07
This is an emergency. >_< I'm panicking pretty hard. Is my computer ruined forever?

---

### Post by OpVines on 2008-06-07
Bump!

---

### Post by saratchandra on 2008-06-07
Sorry that I can't help you, but my advice is to start a thread in the absolute beginner talk. You might get more replies there. And your computer is DEFINITELY not ruined forever. In the worst scenario you have to reinstall ubuntu or windows XP.

---

### Post by knutschr on 2008-06-07
> **OpVines said:**
> 
Even the Gutsy CD I had from before won't even boot. It gets locked up at the screen where the bar is loading...

That isn't possible unless there is a hardware failing?

---

### Post by Sealbhach on 2008-06-07
This must be very distressing. I'm sorry but I'm a civilian user and don't know much.

Maybe try System Rescue CD - at least you could get in and have a look around?

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)


I'm sure it's nothing to worry about. Sorry to hear you're having trouble.

.

---

### Post by OpVines on 2008-06-07
I tried the System Rescue CD, and Ubuntu freezes before the CD can load. This is hopeless. I can't even get the bootup CD of Gutsy to work. 

Is this really a hardware problem? The entire computer's been working flawlessly until I rebooted after the update...

---

### Post by ethanklein on 2008-06-07
I Occasionally have the same problem. WTF is Hardy so broked :(

---

### Post by OpVines on 2008-06-07
Ethan, would you mind telling me how you fixed it?

---

### Post by saratchandra on 2008-06-07
OPVines, it is clearly an OS problem. Did you configure your bios to boot from the CD drive before using the gutsy and system rescue CD? As far as I know, you should not boot into ubuntu at all when you're using a rescue CD.

---

### Post by OpVines on 2008-06-07
The Ubuntu CD boots before the OS does, but the same problem occurs that after a couple seconds of the orange bar moving, everything freezes.

The System Recovery doesn't even load before Ubuntu does, for whatever reason.

I've tried letting it log in through recovery mode, and it's frozen  at exactly the same line I mentioned above. I'll try letting it sit for like an hour or so, but the fact that it freezes at the exact same location every single time is a little alarming. I bought the computer 3 years ago and it didn't come with an extra Windows XP CD...

---

### Post by OpVines on 2008-06-07
Bump!

---

### Post by OpVines on 2008-06-07
For whatever reason, even though I've tried booting it at least 40 times today, this one bot seemed to work, and I got on like I do regularly. Thanks for the help guys.

As a follow up, should I run anything to make sure everything is working properly before I restart the computer again?

---

### Post by Sealbhach on 2008-06-07
That's great news. If I were you, I'd leave it running and bump this post again tomorrow and the next day until you find out what it might be.

Also, if you do reboot, boot in recovery mode and select the option ot "fix broken packages" and also run the other diagnostic there.


.

---

### Post by Dragonbite on 2008-06-08
I am by far not an expert. As a percaution I would back up all of your files if at all possible (USB pen drive, network share, external hard drive, etc.) before rebooting.

When you go for a reboot, check your hardware. Try resetting the RAM modules and double-check the cable connections. While it is highly unlikely that anything had happened there is no sense killing yourself with software if it's hardware.

Is there anything that you have added recently (wireless PCI? ) which may be messing the system up?  2nd hard drive? additional ram (which could be a bad module)? etc.

You say that you have tried the Rescue Mode and it doesn't work, but I don't remember if you tried booting into a live session? It may even be worth it to try a different live-session distro such as Knoppix, Fedora or Damn Small Linux.  Koppix and DSL are live-cd orientated and I suspect if any CD can boot to live these should be able to. Fedora has the advantage of being backed by Red Hat so they have some pretty good inner-working when it comes to the kernel and systems.

Definitely keep us posted!

---

