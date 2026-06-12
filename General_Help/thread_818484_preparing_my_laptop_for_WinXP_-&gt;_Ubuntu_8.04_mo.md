---
title: "preparing my laptop for WinXP -&gt; Ubuntu 8.04 move"
date: 2008-06-04
forum: General Help
---

### Post by IvanIvan on 2008-06-04
Hello!

I'm planning on moving completely to Ubuntu (now I run it inside VMware on WinXP).
I have IBM/Lenovo Thinkpad T60p. Here are the complete specs:
- Intel Core 2 Duo T7200, 2GHz
- 15" UXGA IPS TFT 1400x1050, FlexView
- ATI Mobility FireGL V5250, 256MB
- 2GB DDR2 RAM
- 100GB SATA HDD
- DVDRW
- modem
- Gb LAN, WLAN
- USB, fingerprint reader, etc.

and I have a couple of questions before moving:

1. How to organize my partitions? I have a 100GB HDD inside and it's currently divided like this:
C: (20GB) - Windows only
D: (18.5GB) - Programs
E: (54.6GB) - various "stuff", no installations here...

How do you recommend I organize my partitions?

2. What's the situation with drivers? As you see I have ATI Mobility FireGL. Will it work under Ubuntu?

that's all the questions I have for now, any advice would be appreciated.

Regards,

- Ivan, Zagreb

---

### Post by prince_niceguy on 2008-06-04
You can resize your biggest partition and use the space for ubuntu. I would recommend

6 GB for / i.e. root partition
2 or 4 GB of swap (should be more than your RAM)
4 to 8 GB of home (depends on what you are planning to do, if you are going to ripping of dvd for back up or something then you may need more space in home, you can also use other drives too.)

I think ATI drivers are supported, video play back might give some issue but all in all the laptop should be supported out of box.

---

### Post by IvanIvan on 2008-06-04
> **prince_niceguy said:**
> You can resize your biggest partition and use the space for ubuntu. I would recommend

6 GB for / i.e. root partition
2 or 4 GB of swap (should be more than your RAM)
4 to 8 GB of home (depends on what you are planning to do, if you are going to ripping of dvd for back up or something then you may need more space in home, you can also use other drives too.) 

edit:

I think you're right. I think I'll take 15GB off the E: partition and set it up like this:

6GB for root
4GB for swap
5GB for home

also, can I just start the installation without backing up files on my current E: drive? Can Ubuntu be installed in the free space of E: partiton without "touching" the other files?

---

### Post by prince_niceguy on 2008-06-04
Some questions before we partition the disk.

1. are you going to have any other OS on the system?
2. are you planning to share the folder with some other OS on the network.
3. did you found any hardware related issue when you had ubuntu installed on the larger partition? if yes, which one, we can try resolving that.
4. are you planning to install any development software or something like eclipse, database server, application server etc.
5. is your comp going to be shared with some one else?

---

### Post by IvanIvan on 2008-06-04
> **prince_niceguy said:**
> Some questions before we partition the disk.

1. are you going to have any other OS on the system?
yep. WinXP. 
I'm thinking of this:

C: Windows XP
D: programs (for Windows)
E: "stuff" and...Ubuntu (6 for root, 4 for swap and 5 for home)

is this possible?
> **prince_niceguy said:**
> 2. are you planning to share the folder with some other OS on the network.
I want to be able to access files on E: from inside Ubuntu (the "stuff")
> **prince_niceguy said:**
> 3. did you found any hardware related issue when you had ubuntu installed on the larger partition? if yes, which one, we can try resolving that.
Not that I remember. It was back in version 6 so it's been a while. :)
> **prince_niceguy said:**
> 4. are you planning to install any development software or something like eclipse, database server, application server etc.
oooohhh yes. I'm going into the whole LAMP suite. Eclipse, Java, Tomcat also... lots of developing & testing...This is working fine right now inside VMware, I don't see why it woudn't work on a "real" installation.
> **prince_niceguy said:**
> 5. is your comp going to be shared with some one else?
nope. just me and my account.

---

### Post by Pjotr123 on 2008-06-04
You might find this installation how-to handy:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

Greetz, Pjotr.

---

### Post by prince_niceguy on 2008-06-04
> yep. WinXP.
I'm thinking of this:

C: Windows XP
D: programs (for Windows)
E: "stuff" and...Ubuntu (6 for root, 4 for swap and 5 for home)

is this possible?

yes it is possible, if you do not want to reinstall windows then just resize your largest partition as I said earlier.

> oooohhh yes. I'm going into the whole LAMP suite. Eclipse, Java, Tomcat also... lots of developing & testing...This is working fine right now inside VMware, I don't see why it woudn't work on a "real" installation.
i would recommend creating another partition /opt to have your development apps on it. you can also use your home directory for it, but having separate partitions helps just in case you think of formatting home dir for some reason, your progs will still be there.

your "Stuff" drive should be accesible in ubuntu without any problem. so, go ahead and partition based on your need, if you are planning for db make sure you have good amount of swap more than your ram at the least.

let us know how it goes...

---

### Post by IvanIvan on 2008-06-05
thanks for all advice,
I'll do the installation today or tomorrow so I'll check back in.

Now, other questions:

1. I am curious about program installtions/uninstallations. I know the best way to install programs is via Synaptics (apt-get) since it is in a way "Add/Remove Programs" in a sense that it can perform a decent uninstall. 
I'm wondering what's the situation with programs that I install myself. If the program doesn't have an uninstall script, how do I properly uninstall it - custom deleting all those libs and bins or...?
This question is linked to no particular software, but in general. A sense of keeping my Ubuntu clean & tidy.

2. how does Ubuntu handle video files? what's the best player/codec? VLC? I need to be able to play a variety of files (divx,xvid,h.264,ogg...)

---

### Post by Pjotr123 on 2008-06-05
> **IvanIvan said:**
> thanks for all advice,
I'll do the installation today or tomorrow so I'll check back in.

Now, other questions:


2. how does Ubuntu handle video files? what's the best player/codec? VLC? I need to be able to play a variety of files (divx,xvid,h.264,ogg...)


You can simply apply two easy how-to's.

First this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Then this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should take you about 20 minutes in all, depending on the speed of your internet connection.  :-)

Greeting, Pjotr.

---

### Post by IvanIvan on 2008-06-05
OK, Ubuntu is installed...next set of questions. :)


1.I didn't do proper partitioning and now I have a primary parition size of 19GB and swap of only 1GB. :/ 
Is there a way to change that to 16GB primary/4GB swap without having to reinstall?

2. After install, I ran the update manager, it picked about 120 megs of updates, everything went fine, but know when I boot GRUB shows 2 versions of Ubuntu (for 2 different kernel versions). Why is that?

3. How do I check if all of my hardware is properly installed? Is there a "device manager" in Ubuntu to see all the hardware and drivers?

4. I can't connect to my home network? I tried to set up a location in network settings (I entered my SSID, WPA2 passphrase, static IP, restarted and nothing...the WLAN icon on my T60p is turned off)

5. How do I install drivers for my ATI Mobility FireGL V5250?

thanks

---

### Post by archer6 on 2008-06-05
> **IvanIvan said:**
> Hello!

I'm planning on moving completely to Ubuntu (now I run it inside VMware on WinXP).
I have IBM/Lenovo Thinkpad T60p. Here are the complete specs:
- Intel Core 2 Duo T7200, 2GHz
- 15" UXGA IPS TFT 1400x1050, FlexView
- ATI Mobility FireGL V5250, 256MB
- 2GB DDR2 RAM
- 100GB SATA HDD
- DVDRW
- modem
- Gb LAN, WLAN
- USB, fingerprint reader, etc.

and I have a couple of questions before moving:



I have the _exact_ same configuration on my ThinkPad T60p
Currently I'm running XP Pro SP3 only. 

My goal: 
1) Leave WinXP alone (for now).
2) Leave the (hidden) rescue and recovery partition (to restore the factory XP image and ThinkPad drivers in the event of a bad crash)  alone. 
3) Dual boot with Ubuntu 8.04. 
Use 1/2 the hard drive for XP and the other 1/2 for Ubuntu.

Questions: 
1) Will I "see" the rescue and recovery partition when using  the partitioning utility on Ubuntu ? 
2) Will I still be able to use the ThinkVantage button to launch and use the rescue partition to reload the factory image of XP and ThinkPad specific drivers, in the event of a catastrophic crash, as before? 

Any other tips and suggestions I'm completely open too. 

Thanks in advance for the responses.

---

### Post by IvanIvan on 2008-06-05
why would you completely remove WinXP? I had the same thought but I decided to leave XP and go for the dual boot option. It offeres much more flexibility.

> **archer6 said:**
> Questions: 
1) Will I "see" the rescue and recovery partition when using  the partitioning utility on Ubuntu ?
I don't think so. The "point" of recovery partition is to be hidden, that is you should be able to see it only form Thinkvantage Rescue and Recovery program.

> **archer6 said:**
> 2) Will I still be able to use the ThinkVantage button to launch and use the rescue partition to reload the factory image of XP and ThinkPad specific drivers, in the event of a catastrophic crash, as before?
unfortunately no. :(
read this and it will all be clear:
[http://www.pc.ibm.com/us/notebooks/thinkpad/t-series/workstation.html](http://www.pc.ibm.com/us/notebooks/thinkpad/t-series/workstation.html)

---

### Post by archer6 on 2008-06-05
> **IvanIvan said:**
> why would you completely remove WinXP? I had the same thought but I decided to leave XP and go for the dual boot option. It offeres much more flexibility.


I don't think so. The "point" of recovery partition is to be hidden, that is you should be able to see it only form Thinkvantage Rescue and Recovery program.


unfortunately no. :(
read this and it will all be clear:
[http://www.pc.ibm.com/us/notebooks/thinkpad/t-series/workstation.html](http://www.pc.ibm.com/us/notebooks/thinkpad/t-series/workstation.html)

Thanks for the link. It's all clear now. So I called Tech Support and they are sending me a set of the factory recovery discs. 

Your suggestion of dual boot sounds good. So what would you suggest as far as partition sizes when I do the Install from the  Ubuntu Live CD I just received from Canonical.? 

As long as I'm going to run a dual boot setup I would leave some space on the XP side for Outlook & the Office Suite. I also use OneNote which links to Office. 
MS says system requirements for office = 400MB HD space
                     For MS OneNOte    = 100MB HD space

How would you suggest that partition map look, size per partition? 

Thanks!

---

### Post by IvanIvan on 2008-06-06
> **archer6 said:**
> Your suggestion of dual boot sounds good. So what would you suggest as far as partition sizes when I do the Install from the  Ubuntu Live CD I just received from Canonical.?
you say you have an exact system like mine? (100GB HDD?)

What's your current partition organization in Windows?
C: ?
D: ?
etc.

---

### Post by archer6 on 2008-06-06
> **IvanIvan said:**
> you say you have an exact system like mine? (100GB HDD?)

What's your current partition organization in Windows?
C: ?
D: ?
etc.
Yes, my ThinkPad is exactly the same as yours. 
My 100GB HDD is one large volume just as it came from the factory. It has the "hidden" rescue & recovery partition, and I have not created or done any partitioning on it. Thus I simply have a  C: drive.

---

### Post by IvanIvan on 2008-06-06
> **archer6 said:**
> Yes, my ThinkPad is exactly the same as yours. 
My 100GB HDD is one large volume just as it came from the factory. It has the "hidden" rescue & recovery partition, and I have not created or done any partitioning on it. Thus I simply have a  C: drive.
well, if you want to keep Windows, my suggestion is this:

C: 15GB (only and ONLY Windows + Thinkvantage software)
D: 15-20GB Program Files, Games... (all "installations")
E: 70-65GB "stuff" (no installations here, files, backups, etc.)
....on this E: partiton you can install Ubuntu with the parition sizes as recommended above (by prince_niceguy)

---

### Post by archer6 on 2008-06-06
> **IvanIvan said:**
> well, if you want to keep Windows, my suggestion is this:

C: 15GB (only and ONLY Windows + Thinkvantage software)
D: 15-20GB Program Files, Games... (all "installations")
E: 70-65GB "stuff" (no installations here, files, backups, etc.)
....on this E: partiton you can install Ubuntu with the parition sizes as recommended above (by prince_niceguy)
 Excellent! 
I truly appreciate your help with this, as after years with windows, I am entering this Ubuntu project with no knowledge of Linux. However that said I'm now studying Ubuntu with great enthusiasm. Once I have my T60p setup like this, then I will have Ubuntu with me everyday as this is my main work laptop which I travel with. Which in turn will then allow me to learn Ubuntu as my time permits. 

One remaining question please: when using the partitioning tool that comes on the 8.04 LiveCD will I be able to "see" the ThinkVantage rescue partiton so it's not accidentally overwritten? And if required is it possible to "move" it to accomplish the partition layout you have suggested? I plan on following your partiton layout exactly as it fits my needs perfectly. 

Finally thank you for your fast responses to my questions as I'm eager to get this done. I will be doing so just as soon as it's all clear to me.

Arcer6

---

### Post by IvanIvan on 2008-06-07
> **archer6 said:**
> One remaining question please: when using the partitioning tool that comes on the 8.04 LiveCD will I be able to "see" the ThinkVantage rescue partiton so it's not accidentally overwritten? And if required is it possible to "move" it to accomplish the partition layout you have suggested? I plan on following your partiton layout exactly as it fits my needs perfectly.
I'm **not** sure about that. :(
Try asking here: 
[http://forum.thinkpads.com/](http://forum.thinkpads.com/)
it's the best community for Thinkpad users, surely someone there knows. :)

---

### Post by eZtaR on 2008-06-07
> **IvanIvan said:**
> OK, Ubuntu is installed...next set of questions. :)


1.I didn't do proper partitioning and now I have a primary parition size of 19GB and swap of only 1GB. :/ 
Is there a way to change that to 16GB primary/4GB swap without having to reinstall?

2. After install, I ran the update manager, it picked about 120 megs of updates, everything went fine, but know when I boot GRUB shows 2 versions of Ubuntu (for 2 different kernel versions). Why is that?

3. How do I check if all of my hardware is properly installed? Is there a "device manager" in Ubuntu to see all the hardware and drivers?

4. I can't connect to my home network? I tried to set up a location in network settings (I entered my SSID, WPA2 passphrase, static IP, restarted and nothing...the WLAN icon on my T60p is turned off)

5. How do I install drivers for my ATI Mobility FireGL V5250?

thanks

1. Just boot the livecd and load up the partition manager (gparted).

2. It's so, if you have issues with the new kernel, you can choose only to boot the old kernel.

3. I think i remember seeing something like it, but for now just go to System > Administration > Hardware Drivers.

4. My guess is that you need to install your network drivers with ndiswrapper, there are loads of guides for doing that here on theese forums.

5. I'm blank if step three doesn't show up anything.

---

### Post by IvanIvan on 2008-06-07
> **eZtaR said:**
> /cut
thnx but I managed to set up everything I need (well, almost...still need to configure wpasupplicant and other stuff...)

---

