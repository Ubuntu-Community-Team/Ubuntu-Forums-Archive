---
title: "mIRC bot in Ubuntu 8.04"
date: 2008-05-20
forum: General Help
---

### Post by Ron Overdrive on 2008-05-20
Ok I got me a quasi-unique situation. For a while I was running an mIRC bot for someone in a VMWare image with Windows XP running and an UltraVNC server running for remote access. Then I upgraded to 8.04 not realizing VMWare doesn't exactly work in 8.04. Tried using the guides for installing it under Hardy with no luck it just spits out errors at me saying vmware isn't configured. 

So my alternative is setting up a quota'd account thats restricted from using sudo and run mIRC via WINE. Now is there a way I can log into my box remotely using NoMachine NX and not end up killing the mIRC bot when I close the session? Same deal if I log in locally?

I've looked around for some kind of mIRC script to Eggdrop interpretor, but have had no luck and the guy isn't about to learn TCL to rewrite his script so this is pretty much what I'm limited to.

---

### Post by Thirtysixway on 2008-05-20
Does VirtualBox work on 8.04?  You could try that as an alternative to vmware.

---

### Post by rev0lv3r on 2008-05-20
VMWare is not too difficult to set up with the new kernel

[http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html](http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html)

[http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel)

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

It should be one of those links
Basically the issue is something changed so when you install vmware and it does the compiling modules portion, you have to first edit the source -- but there are scripts in the above links to do it for you
It's just a simple replacement though

I am running 8.04 Ubuntu + VMWare Workstation 6

BTW: can you not run the bot from within linux? I'm sure an eggdrop can do what you need?

---

### Post by Ron Overdrive on 2008-05-26
> **Thirtysixway]Does VirtualBox work on 8.04? You could try that as an alternative to vmware. [/quote]

Yes VirtualBox works in 8.04, but as far as I know its not like VMWare Server where it can run as a back ground service that doesn't get shut down when the user logs out.

[QUOTE=rev0lv3r said:**
> VMWare is not too difficult to set up with the new kernel

[http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html](http://diamondsw.dyndns.org/Home/Et_Cetera/Entries/2008/4/25_Linux_2.6.24_and_VMWare.html)

[http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel](http://blog.creonfx.com/linux/how-to-install-vmware-player-workstation-on-2624-kernel)

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

It should be one of those links
Basically the issue is something changed so when you install vmware and it does the compiling modules portion, you have to first edit the source -- but there are scripts in the above links to do it for you
It's just a simple replacement though

I am running 8.04 Ubuntu + VMWare Workstation 6

BTW: can you not run the bot from within linux? I'm sure an eggdrop can do what you need?

I've tried the VMware guides before starting this thread and have gotten no where with VMware Server which is what I need. Just gives me configuration errors when its been patched and the drivers compiled/installed so I dunno what the issue is. From what I've seen on the forums I'm not the only one the guides have failed for.

As for the eggdrop bot, like I said in the last sentence of my post Eggdrop cannot be used. Its not my bot and the guy who made it isn't about to learn TCL just to convert it to an eggdrop bot (this is a custom bot, not one of those generic scripts). I'm simply hosting this for the guy who made it since he doesn't have an always on connection.

---

### Post by rev0lv3r on 2008-05-26
> **Ron Overdrive said:**
> Yes VirtualBox works in 8.04, but as far as I know its not like VMWare Server where it can run as a back ground service that doesn't get shut down when the user logs out.



I've tried the VMware guides before starting this thread and have gotten no where with VMware Server which is what I need. Just gives me configuration errors when its been patched and the drivers compiled/installed so I dunno what the issue is. From what I've seen on the forums I'm not the only one the guides have failed for.

As for the eggdrop bot, like I said in the last sentence of my post Eggdrop cannot be used. Its not my bot and the guy who made it isn't about to learn TCL just to convert it to an eggdrop bot (this is a custom bot, not one of those generic scripts). I'm simply hosting this for the guy who made it since he doesn't have an always on connection.

Ah yes, my reading comprehension fails me :D

Let me get this straight (re VMWare) - You are running Ubuntu 8.04 as the host, and you want to create an image of WinXP
This shouldn't be too hard, I am doing the same

Can you list your hardware specs?
I have done this successfully on a Gigabyte DS3 mobo, Intel C2D 1.8ghz (E6300), and 1gb ram + Geforce 7600
I am running the latest kernel available from the Hardy repos
What about you?

---

### Post by Ron Overdrive on 2008-05-29
> **rev0lv3r said:**
> Ah yes, my reading comprehension fails me :D

Let me get this straight (re VMWare) - You are running Ubuntu 8.04 as the host, and you want to create an image of WinXP
This shouldn't be too hard, I am doing the same

Can you list your hardware specs?
I have done this successfully on a Gigabyte DS3 mobo, Intel C2D 1.8ghz (E6300), and 1gb ram + Geforce 7600
I am running the latest kernel available from the Hardy repos
What about you?

The host is running XUbuntu 8.04 upgraded from 7.10. I already have a working vmware server image when it was 7.10 so I don't need to create a new one. As for hardware specs is an AMD Athlon XP 2600+ (1.9ghz) with 1.2gigs DDR ram and a Geforce 6600GT.

---

### Post by rev0lv3r on 2008-05-29
> **Ron Overdrive said:**
> The host is running XUbuntu 8.04 upgraded from 7.10. I already have a working vmware server image when it was 7.10 so I don't need to create a new one. As for hardware specs is an AMD Athlon XP 2600+ (1.9ghz) with 1.2gigs DDR ram and a Geforce 6600GT.

Which kernel do you have
I believe an issue with 2.6.24 requires some of the vmware sources to be modified when you compile your modules during the (i think) configuration? maybe installation.

---

### Post by Ron Overdrive on 2008-05-29
> **rev0lv3r said:**
> Which kernel do you have
I believe an issue with 2.6.24 requires some of the vmware sources to be modified when you compile your modules during the (i think) configuration? maybe installation.

Its 2.6.24 and I've tried patching the code. It compiles and installs the files, but doesn't run.

---

### Post by rev0lv3r on 2008-05-30
> **Ron Overdrive said:**
> Its 2.6.24 and I've tried patching the code. It compiles and installs the files, but doesn't run.

That's interesting

Can you try this in a terminal

'sudo vmware'

It should output something back into terminal.

---

### Post by Ron Overdrive on 2008-05-31
> **rev0lv3r said:**
> That's interesting

Can you try this in a terminal

'sudo vmware'

It should output something back into terminal.

That was the 2nd thing I tried, same error. Claims its not configured when it is.

---

### Post by rev0lv3r on 2008-05-31
> **Ron Overdrive said:**
> That was the 2nd thing I tried, same error. Claims its not configured when it is.

Try reconfiguring it
"sudo /usr/bin/vmware-config.pl"

---

### Post by Ron Overdrive on 2008-06-01
> **rev0lv3r said:**
> Try reconfiguring it
"sudo /usr/bin/vmware-config.pl"

Uhh... how to put this.. I've tried everything with VMware and have gotten no where so I've given up on it till it shows up in a repository. Thats why I started this thread, to find alternatives.

---

### Post by rev0lv3r on 2008-06-01
Ah, that's a very good point

Alternatives, hm, have you tried Virtualbox or Xen?

I do not think VMWare will show up in a repo because it's not open source, but I could be wrong

I know Virtualbox and Xen are opensource (i think)

---

