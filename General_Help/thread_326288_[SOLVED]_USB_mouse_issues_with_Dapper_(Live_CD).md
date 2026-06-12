---
title: "[SOLVED] USB mouse issues with Dapper (Live CD?)"
date: 2006-12-27
forum: General Help
---

### Post by mmtowns on 2006-12-27
Hello.  I am currently in the process of testing Dapper on my machine.  From what I have read on other posts, it seems as if it may be helpful to post some information about my computer:

AMD Athlon XP 1700
384 PC2100 RAM
Nvidia Geforce2 MX 400

I am currently running the Dapper Live CD, one I downloaded myself (although the same 'problem' exists when using one from ShipIt).  When I boot from the CD, my Microsoft Wheel Mouse Optical USB cursor is very slow and 'jerky.'  Everything else seems to run fine from the CD.  A few things I have noticed...
I switched out the USB mouse for a PS2 Microsoft mouse and the problem no longer exists.  This leads me to believe that there is a problem/conflict with the USB mouse.  I do not have this problem with Windows XP, but interestingly I have the same issue when booting a Fedora liveCD and a Mepis LiveCD.  

I have tried to search the forums for similar problems, but to no avail.  Perhaps someone out there has had a similar problem or knows a workaround so that I can get my USB mouse working?  I would like to get it working before I make the total switch from XP to Ubuntu.  Any insight/suggestions would be greatly appreciated.

Thanks for your consideration.

---

### Post by dannyboy79 on 2006-12-27
that's so wierd. I get the same problem when using a PS/2 mouse with Xubuntu (Dapper version) on my laptop. I would suggest looking at your output from 
sudo lspci -v
that should tell you the usb controllers and maybe you can gogle using that info? i know the settings for mouse control are kept within the xorg.conf file I think. just do a sudo find / -name xorg* from a command line. then first always back it up before editing, sudo cp xorg.conf xorg.conf-backup (if working from a live cd, not sure what you can do here? you might have to learn how to use the live cd with the persistant option where it uses the config files that you save on a usb stick, it is a vaild option when using a live cd?) then you would edit the xorg.conf and look for the mouse section and trial and error with various changes. you could also reconfigure your xorg.conf file, that's done by doing sudo dpkg reconfigure or something like that? people talk about it all over these forums. sorry I couldn't be more help. good luck

---

### Post by mmtowns on 2006-12-28
Thanks for your efforts.  I'm also have difficulties with my SB Live sound card that I'm thinking may only be related to the LiveCD.  I'm hoping the USB mouse issue is only a LiveCD problem as well.  Time will tell if I can carve out some time to do a hd install.

Thanks again for taking the time to respond to my message.

---

### Post by dannyboy79 on 2006-12-29
well that can be true and not true. just so you are aware the live cd will act the exact same way the hd install will! basically the advantage of doing the hd install is speed for one thing but also that you can make config changes and they'll stick. so needless to say, if something isn't working with the live cd, it won't work with the hd install. you will obviously have to ask for help to see if you can get them working. i can't say that they will not work ever, but I can tell you if you simply install onto the hd without any config changes, they will not work just like the live cd. all the install does is copy all contents from the cd onto your hd and that's it. good luck

---

### Post by mmtowns on 2006-12-29
Thanks!  I was unaware that the live cd would act the same way.:( 

I'll keep searching the forums and messing with the config files to see what can be done.

Again, I really appreciate your insight.

---

### Post by mmtowns on 2007-10-14
I finally got around t doing a HD install of Feisty.  The issue I was having was related to ACPI.  I tried out a few other flavors of Linux.  One allowed me to startup with "no acpi" and my mouse, ethernet, sound, etc. issues were solved.

Since then, I've added "noacpi acpi=off" to the boot parameters on the live cd and now on grub for my HD install.  I'm finally happy with Ubuntu.   My only issue (due to my boot parameters, yes) is that I have to manually turn off my machine after Ubuntu shuts itself down.  I think the last thing I see is "System is getting ready to halt..."

I guess I can live with this....

---

### Post by Shazaam on 2007-10-14
The livecd will run MUCH slower (and jerkier) than an installed system.
Hmm. Running ALMOST the same setup as you and I didn't have to add any boot params.
AMD AthlonXP2500
Soyo KT600
SBLive 5.1
2gigs ram
Logitech wireless keyboard/mouse (USB, plugged into the ps/2 ports with adapters that came with them)
BFG 7800GS vidcard.
Dapper.

---

### Post by mmtowns on 2007-10-14
I had this same issue with several linux distros.  I have a Gigabit motherboard (don't recall the exact model) and it works just fine under XP.  Really strange that ACPI was the issue.

---

