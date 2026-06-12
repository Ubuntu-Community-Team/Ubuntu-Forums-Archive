---
title: "Mediasmart HomeServer EX490 - NTFS Automount"
date: 2013-04-06
forum: General Help
---

### Post by Froberg on 2013-04-06
Hi all, 

I just registered tonight, this seemed like a good place to get information! 

I've spent a few hours setting up Ubuntu on this entirely interface-less homeserver. It's going fairly great and I've gotten it to automount my NTFS drives and partitions nicely.
However, if I unplug a drive and reboot - I can no longer access the server via VNC. This is very much an issue since, in the event of drive failure, I'd be up **** creek without a paddle fairly quickly. 

I've looked at various options for getting the darn thing to continue the boot process, but with no luck. Basically if I select restart from the power menu, pop out the hot-swap drive, wait a bit and try to connect ; Nothing happens.
I put the drive back in; Voilá, I can now connect. 

Here's my fstab mounting line: UUID=7A21227C04D8DE39  /media/Data  ntfs-3g  defaults,windows_names,auto,nofail,locale=en_US.utf8  0 0 

I'm fairly new at this stuff, hence why I'm using the desktop version even though it's a server, simply because having an interface really helps me with some of the functions I want to accomplish. Regardless, it shouldn't affect the actual usage of the thing. 

I really need there to be no prompts or other naughty stuff during bootup, as this thing has no connected keyboard, no mouse, no option of connecting a monitor. 

Please help, and if I've not made myself entirely clear, or ranted too much, please let me know so I can try and make myself more clear.

---

