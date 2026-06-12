---
title: "I can't load linux... Please help..."
date: 2008-06-17
forum: General Help
---

### Post by mtgmutton on 2008-06-17
I was running my dual-boot Hardy/XP machine and everything was fine, until I rebooted from Hardy and nothing would load... It was in the grub menu (Hardy was listed three times), but when I tried to boot, the screen just went black and the system rebooted. Then, I tried LiveCDs of Hardy, Gutsy, PCLinuxOS, Linux Mint 4.0, and openSuSE 10.3, but I got the same problem with all of them. I have deleted my linux partition in the hopes that it was corrupted or something, but I still can't load anything but XP, which I fixed with "fixmbr" in the recovery console. Please, if you have any advice, help me as soon as you can! :confused:

---

### Post by mtgmutton on 2008-06-18
OK, now I got the PCLinux OS 2007 disk to load in safe mode, but the partition editor confuses me... I checked it out, and it had a 1008 MB partition that I didn't recognize... it had 1000 mb free, though. I don't know what this means. Was my linux partition not deleted properly? Please help soon! I hate not having linux on my computer!

---

### Post by beckols on 2008-06-18
I believe that extra partition is your swap space.  A swap partition is created when you install linux; it's purpose is to handle overflow from the memory.  For example, if you are running too many things, and they require more memory than you have in your RAM, your swap space acts as a backup, albeit a very slow one.  It's better to just be conscientious about your memory usage, though, as swapping slows down your computer considerably.  The bright side is that you won't ever get "Not enough memory" errors (cough windows).

---

### Post by mtgmutton on 2008-06-18
Thanks for replying. I have 2GB of ram, and I deleted my swap partition as well, so I have no idea what this could be... Again, I can't load ANYTHING but the purely evil ms windows... except for PCLinuxOS Live CD in safe mode. everything else just goes to the black screen as if it's changing to show the login, then reboots...

---

### Post by beckols on 2008-06-18
Ok, so just to clarify... you have an xp partition, a ~1 GB unknown partition, and the rest is unformatted soon-to-be linux space?

---

### Post by mtgmutton on 2008-06-18
It would be, if only I could load the Linux Mint 5.0 Elyssa disk!

---

### Post by beckols on 2008-06-18
You can't load any of the CD's even from within Windows??

---

### Post by mtgmutton on 2008-06-18
Wow. I've been using Linux for almost a year an a half, and I didn't know I could load them from windows... I feel silly. Do you think fragmentation could have caused it? windows suggested that I defrag... I haven't done that in months... I'll try loading a disk through windows.

---

### Post by mtgmutton on 2008-06-18
OK. I put the disk in my disk drive, and windows understands that it has a name and files on it. How would I load it from windows?

---

### Post by beckols on 2008-06-18
I don't know if fragmentation could have caused it, but 3 months is a long time to go without a defrag no matter what haha.  I have mine run nightly automatically on vista.

---

### Post by mtgmutton on 2008-06-18
The defrag is done. I'm going to try loading a linux disk again.

---

### Post by beckols on 2008-06-18
If it's an ubuntu liveCD, there should be a file on there called wubi-cdboot.exe, this will get you started installing it from windows, but you will have to reboot to continue it.  If it is Linux MINT 5, then I'm not sure how their CD's work.

---

### Post by mtgmutton on 2008-06-18
I couldn't get it to load from rebooting into it, but Linux Mint is based on Ubuntu, so it should be similar.

---

### Post by mtgmutton on 2008-06-18
> **beckols said:**
> If it's an ubuntu liveCD, there should be a file on there called wubi-cdboot.exe, this will get you started installing it from windows, but you will have to reboot to continue it.  If it is Linux MINT 5, then I'm not sure how their CD's work.

No, there isn't any such file. I'm not sure what to do. Do you think it's safe do delete that random partition? Windows can't see it.

---

### Post by beckols on 2008-06-18
When you say "you can't get it to load" what exactly do you mean? Tell me exactly what happens from bootup.

Also, what is the file format of the unknown partition?

---

### Post by lswest on 2008-06-18
Did you change any hardware lately?  Also, what is the random 1GB partition formatted as?  Can you access it from XP?  And you won't find a WUBI installer on Linux Mint, so far only Ubuntu offers WUBI (it is Windows Ubuntu Installer, after all ;)).  Can you post the specs of your machine too?

---

### Post by mtgmutton on 2008-06-18
OK. I'm using a Dell Dimension 3000, so I see the dell screen on a black background (with the options of F2 for setup and F12 for boot menu). Then, the disk loads onto the menu, with the normal options like "try or install *insert linux here*", and "boot from hard drive", etc. Then, I choose "try or install". It shows some text sometimes, pretty normal. Then it switches to a black screen as if it's going to load the login screen. At that point, it simply reboots.

---

### Post by lswest on 2008-06-18
Have you changed any hardware lately in the pc?  And can you give us some more information about the mystery partition?

---

### Post by mtgmutton on 2008-06-18
> **lswest said:**
> Did you change any hardware lately?  Also, what is the random 1GB partition formatted as?  Can you access it from XP?  And you won't find a WUBI installer on Linux Mint, so far only Ubuntu offers WUBI (it is Windows Ubuntu Installer, after all ;)).  Can you post the specs of your machine too?

OK. I don't know what it is formatted as, the PCLinuxOS partition editor confuses me... I'm very used to GParted. I can't see it in XP. I have 2GB of Ram, a 3.00 Ghz processor, a new 256 MB Geforce FX5200 graphics card, and a new 500 Watt power supply. I also have a 320 GB hard drive. Linux was working fine with the graphics card and power supply, which I just added. I've had them for a week and my Ubuntu 8.04 just broke yesterday.

---

### Post by beckols on 2008-06-18
When it first stopped working, you said you did a reboot from hardy and then it wouldn't come back up... what was the reason for the reboot?  Did you just update/install any software?

---

### Post by mtgmutton on 2008-06-18
Actually, yes. Ubuntu had just installed some updates and told me to reboot, so I did. That's when this mess started.

---

### Post by beckols on 2008-06-18
Well, unfortunately you formatted it, because the synaptic history log files probably could have been salvaged to see if that was what caused it.  Hmm, whenever you boot from a liveCD get to a terminal and try [THIS]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") link.  I'm not sure if it will work or not, but it's worth a try.  Make sure you change (hd0,0) appropriately.  Grub is a little out of scope for me, but to me it seems like that has to be where the problem originates.  I think fixmbr just makes xp the default bootloader, I don't think it gets rid of grub so possibly it is just corrupted.  Anyone with more experience with this, please feel free to step in and correct me

---

### Post by mtgmutton on 2008-06-18
I tried this with the PCLinuxOS disk because it's the only one that works... It didn't work. When I type "setup (hd0)", it says, "error 15: file not found". I don't see how grub would help me, though. And a little more about the mystery partition: Only PCLinuxOS can see it. I looked for it in winows and in a partition editor I downloaded, and neither of them saw it. Only PCLinuxOS notices, and its partition editor can't edit... only view. When I look at the "file system type" column, it says that it is a "rootfs" or root file system... Does anyone know what this means?

---

### Post by mtgmutton on 2008-06-18
I HAVE SOLVED THE PROBLEM!!! it turns out that the plug that sent power from my power supply to my disk drive was messed up, so I put in another one, and it worked perfectly. Now I am typing this in Linux Mint 5.0 Elyssa R1  :)

---

### Post by beckols on 2008-06-18
Never would have thought of that since you were able to load the cd in windows... oh well, congrats on figuring it out.

---

### Post by mtgmutton on 2008-06-18
Thanks. And thank you for all your help. :)

---

