---
title: "Windows dead, Ubuntu dying"
date: 2005-04-14
forum: General Help
---

### Post by Quest-Master on 2005-04-14
So I come back home from school today, open up my computer, and boot into Windows to put my brother on a program Windows-only. Funnily, as soon as the loading screen goes away, a blue screen appears with many errors on it and the next second the computer starts again. I try again with the option "Last working configuration," and guess what? Didn't work either.

Then I come to my lovely Ubuntu knowing it wouldn't fail me. X doesn't start. I reboot, and GDM crashes 6 times in 90 seconds, and continuously switches between the shell and a brown screen. A window also continuously opens up in the brown screen saying, "Attempting to load with different session manager." Continues returning this message.

After about another minute, it goes to a curses interface, pops a window saying, "Your session manager has crashes 6 times in 90 seconds. Something has gone wrong, and I will try different configuration :0."

Reboot another time, and Gnome finally starts up. However, my wallpaper is gone, and my gnome-terminal is acting weird.

What is happening? Is my computer dying? Someone, please help me. I'm afraid to shut down my computer in fear that it won't start up again now :(

---

### Post by fxer on 2005-04-14
Wow, that's not good. Sounds hardware related if it is happening reguardless of operating system. Do you happen to have another video card you can swap out and see if you have the same problems? 

Regardless i'd get everything backed up you are sure you don't want to lose before you try anything else, always a good first step :)

Reguardless, you may want to amend the title of your post here, "windows dead, ubuntu dying" sounds more like flame-bait than a computer issue ;)

---

### Post by Klin'Targ on 2005-04-14
This is definitely hardware related. My first guess would be a dying/corrupted hard disk if both ubuntu and windows are on the same HD. Run fsck on your HD in linux. I usually boot off of a live cd to do this, but the recovery mode boot option may work (haven't tested it). Either way make sure the system disk is unmounted before you run fsck! (It will warn you if your drive is mounted). 

Other things to test: 
ram (run memtest86, I believe its a boot option for ubuntu) 
pci cards (make sure they are all correctly seated) 
motherboard, power supply (both difficult to test unless you have spare parts laying around).
Usually pci card, motherboard, and power supply issues keep the machine from powering on at all though.

---

### Post by philipacamaniac on 2005-04-14
Hardware issues is what it sounds like. Unplug all and any peripherals, including printers, cameras, scanners, and external disk drives. If that doesn't help, I suggest doing the following.

I'm not sure how to check for critical errors in Ubuntu, so I would boot into Windows Safe Mode, and go to Start --> Run --> "eventvwr.msc" then choose the System Log. It will tell you if you have any hardware problems that caused Windoze to bluescreen. If there is nothing, then the Windows install is corrupt and you'll need to reinstall.

Oh, and disappearing wallpaper sounds like the computer got shut down improperly; strange things happen like that when on a sensitive filesystem like ext3. I once had a system freeze, so I shutoff my KDE Slackware desktop. When I brought it back up, ALL of my KDE configurations and customizations were lost.

---

### Post by Quest-Master on 2005-04-14
[QUOTE=philipacamaniac]Hardware issues is what it sounds like. Unplug all and any peripherals, including printers, cameras, scanners, and external disk drives. If that doesn't help, I suggest doing the following.

I'm not sure how to check for critical errors in Ubuntu, so I would boot into Windows Safe Mode, and go to Start --> Run --> "eventvwr.msc" then choose the System Log. It will tell you if you have any hardware problems that caused Windoze to bluescreen. If there is nothing, then the Windows install is corrupt and you'll need to reinstall.

Oh, and disappearing wallpaper sounds like the computer got shut down improperly; strange things happen like that when on a sensitive filesystem like ext3. I once had a system freeze, so I shutoff my KDE Slackware desktop. When I brought it back up, ALL of my KDE configurations and customizations were lost.[/QUOTE]
 Phew, I changed the session manager to KDM instead of GDM and everything's gone along smoothly with Ubuntu.

Also, my Windows is completely dead. It won't even start up in Safe Mode anymore. The partition is fine though.. but I was sort of expecting the Windows to die soon enough, hehe.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=Quest-Master]
Also, my Windows is completely dead. It won't even start up in Safe Mode anymore. The partition is fine though.. but I was sort of expecting the Windows to die soon enough, hehe.[/QUOTE]

Its not death, but suicide.

Darwin's formula at work....

---

