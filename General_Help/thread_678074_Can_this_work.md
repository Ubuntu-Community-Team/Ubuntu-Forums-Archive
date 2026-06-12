---
title: "Can this work?"
date: 2008-01-25
forum: General Help
---

### Post by joeynosek on 2008-01-25
I want to reuse a Dell 4300 Dimension circa 2001 machine (1.4 GHz processor and 512M RAM/Ethernet card/2 IDE hard drives -2 and 20 Gb)to build a video/audio media and data file and print server which provides for centralized user administration functions (similar to Windows Active Directory) which can be administered remotely either from a machine connected on my home LAN or from a web interface.  I have not checked this out yet but if there are any open PCI slots, I would like to add HDTV tuner (to make the server also a PVR) and USB 2.0 cards (to speed up data transfer between external hard drives and other peripherals if that makes sense).  I would eventually like to run it as a web and FTP server as well but not for a while.  The clients are currently a Compaq Presario PC running XP Pro (wired connection), a MacBook running OS10, and a Dell notebook running Vista (both notebooks wireless).  My ISP provides me with a dynamic IP address from which I have asymmetric DSL service.  The router is a Linksys WRT54G.

I would prefer at this stage of my Linux ability (none) to have the most intuitive GUI for setup and administration with the option of moving to a command line interface for these things as my abilities grow (I am essentially a techno-dope with geeky tendencies, I guess).  How do I check hardware compatibility and the functions the motherboard supports?  I know the mobo does not support SATA drives or RAID configurations.  Does it make sense for me to get a new mobo and maybe a power supply for what I want to do so it will work right (RAID/USB 2.0/SATA/PCIe slots/PVR/HDMI outputs)?  Do I need a new video card?  My understanding is that since I want to run the server as a “headless machine” (it will be in a cabinet along with the DSL modem and router), video and sound cards are not really necessary.

I know this is a lot of stuff for 1 machine to do but I have read so much about the capabilities of Linux with old hardware that I couldn't throw the old machine away without finding out if it could do all this.  Maybe I look for another old machine to take some of the load?  That's possible if it makes things work better but I would prefer to make it all work on the one machine if at all possible.

Help!

---

### Post by rosegarden78 on 2008-01-25
Try my post [here]("http://ubuntuforums.org/showthread.php?t=677959") or the how-to [here]("http://ubuntuforums.org/showthread.php?t=385981"). :KS  EDIT:  Sorry you say headless?  Use Ubuntu Server don't install windows environment maybe use Blackbox.

---

### Post by joeynosek on 2008-01-25
Thanks for the reply rosegarden 78 (and editor).  I was wondering if Ubuntu server was the solution or not.  I have also been advised by someone outside this forum that I should use Feisty.  I have no idea what Ubuntu to use to do what I want to do.  

Also, am I dreaming when I say I want all this to happen on 1 machine? If it can all work on 1 machine, can it work on this machine? If hardware is necessary, how do I determine that?

---

### Post by rosegarden78 on 2008-01-26
A LAMP server runs in the background of my windows manager.  When you boot a Linux PC the kernel load first.  You have six terminals and a seventh for X server.  If you want headless press Ctrl-Alt-F1 through F6 to use your headless terminals.  When you want a GUI press Ctrl-Alt-F7 to switch to X server.  Yes Ubuntu is six headless servers and and one GUI at same time.  Their help manuals are detailed should explain this.

---

### Post by joeynosek on 2008-01-27
I need to get into the user manuals.  But I think my best bet is to just load Ubuntu (I am going to try both the desktop and server editions of 7.10) on the open 10 gig partition which is currently NTFS formatted as the D drive (the other partition is the C drive with xp pro) and just start experimenting to learn this OS.  I figure I can always reformat the partition with Ubuntu installed using xp and start over with a clean slate until, with the good help I read in this forum and the user manuals, I get things running the way I want and with no problems.

As a windows guy wanting to create a linux do-it-all server I feel like I am still shooting from the hip.  Does anybody have any advice on this approach?

---

