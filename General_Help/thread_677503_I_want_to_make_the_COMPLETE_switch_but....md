---
title: "I want to make the COMPLETE switch but..."
date: 2008-01-24
forum: General Help
---

### Post by MrSootentai on 2008-01-24
I love Ubuntu. Absolutely Love Linux. Free is for me (as my dad always said).
But I'm stuck. I've had so many little problems here and there with Ubuntu that honestly I don't know what to do. I want to reinstall completely wiping the Vista partition but I'm not sure. Let me just give you a quick list here:
1) Heat - for some reason I can NEVER get it done below 46 degress C, but under Windows and BackTrack 3.0 Beta I've gotten it down to 32 degrees C easy. I've closed every possible application and system service I don't need but to no avail. I also don't want to have to keep gkrellm on all the time to control the fans.

2)Video Card Issues - So many of them. I love Compiz, because honestly it's so handy. The cube is gorgeous but so are the effects. But I can't use dual-screen when I have XGL installed. XGL seriously takes up 5-14% of my CPU the entire time it is on. But once I uninstall the XGL I can run everything perfectly, but no compiz =[

3)It seems that for some reason, after a couple of weeks of using Ubuntu, I always have to fsck the drive and fix it up. It's getting annoying, and recently I've ran into the trouble where my distro doesn't even boot up all the way (just loads to black screen with mouse).

5)Hibernate and Suspend NEVER work, don't know why. Plus my power manager doesn't even show that I have a battery installed. Oh yeah, and the screen on the laptop never turns off. I can't force off.

4)Just overall stability. I'm not sure if it's my laptop model (Dell 1420 not N), but these problems seem like they shouldn't be here. In-Line Microphone doesn't work, Webcam doesn't work under flash apps, video card has been buggy (under vesa AND intel drivers). Wireless drivers with my card are also getting to be a hassle (but I ended up settling with Wicd which worked wonders).

Overall I'm just sort of frustrated. I'm downloading the Dell 7.10 1420N DVD hoping that maybe if I reinstall with that, that maybe my problems will be fixed. If not I am willing to just end up using LinuxMint (seems simpler right now) or just make the jump to ArchLinux (but I don't have the time to set it all up).

Sorry if it's a little long but I just wanted some opinions from you guys.

PS:I am currently dual booting Vista Home and Ubuntu 7.10. Vista sucks compared to Gutsy, too much cluttering and slow speeds.

---

### Post by pointone on 2008-01-24
Problems 2 and 5 can be solved by [updating your ATI driver to the latest version]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"). (I assume you're running ATI. NVIDIA and Intel don't require Xgl, as both support AIGLX in the default drivers). Note the section about suspend / hibernation in the guide; I needed to edit /etc/default/acpi-support before mine would work, as described in the guide.

Problem 1 I don't really see as a problem. Unless you're trying to overclock or notice major instability, 46 degrees leaves more than enough headroom. Have you considered that Ubuntu may not be running your fans as fast as Windows is? Also keep in mind that running desktop effects will increase power consumption and heat output.

As for 3, make sure you have enough free space on your drive. If it's running close to the brim, you may experience some trouble. When you mention fsck, are you talking about the automatic fsck that runs every 20 to 30 mounts? If so, this is not idicative of a problem; it's just a maintenence feature.

---

### Post by MrSootentai on 2008-01-24
Thank you for the fast reply.
Well I'm not running an ATI card, but I noticed that I could never get Compiz working without installing Xserver XGL from synaptic, and I thought that was just something I had to do. Maybe now I can uninstall it and fix that consumption.

The heat issue to me is kinda big mainly because I use i8k Plugin for Gkrellm under Gutsy and my temp doesnt lower past 46 when idle, but in Windows and Backtrack its easily 46 on a medium load (right now i have a couple downloads going, and a virus scanner working). But maybe it really isnt a big deal.

And the FSCK isn't the automatic, but rather one that I have to go through and use. Most of the time when I have a problem, when booting up Gutsy it tells me to enter root pass because of 'illegal inodes' then i run fsck and fix them up and reboot.

Usually whenever I had that black screen problem I could just fsck and it would be fixed, but now it just wont work.

---

