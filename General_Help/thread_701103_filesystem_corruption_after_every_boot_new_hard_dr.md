---
title: "filesystem corruption after every boot? new hard drive/clean 7.10 install"
date: 2008-02-19
forum: General Help
---

### Post by WasabiVengeance on 2008-02-19
I just bought a brand new hard drive for my thinkpad t60 after the old one with my windows partition crapped out and installed 7.10. After several problem free boots, several different programs started seg fault'ing. I set the drive to fsck on every boot (tune2fs -c 1 /dev/sda1) and rebooted. A few duplicate inodes were found and it successfully rebooted, no problems. It happened again a few days later and at this point fsck is failing on EVERY boot, requiring a manual fsck. This drive and the installation is a week old.

Any thoughts guys? I'd immediately look to the hard drive if it wasn't a week old.... Does 7.10 have any known problems with  intel 945GM chipsets or something quirky like that that would cause constant filesystem corruption?

On [ this thread ]("http://ubuntuforums.org/showthread.php?t=270388") I found this comment: "I've used "hdparm -W 0 /dev/hda" (and equivalent in /etc/hdparm.conf) to completely disable the drive's write caching. Hopefully that will work." Any thoughts on that as a possible solution?

---

### Post by WasabiVengeance on 2008-02-19
bump. Help me out here guys :/

---

### Post by C14rk3y on 2008-02-19
Im having the exact same issue.  Brand new hard drive, and asking for manual fsck.

Im very new to ubuntu and Im also dual booting but I just have to figure this out, lol.  after running manual fsck I also get the inode error asking me to resize or relocate, cant remember right now.  But when I hit (y) they just keep going and going.

Im lost now as I thought I was prepared for the manual fsck (as this happened to me before), but Im just getting the same msg.

Please help, thanks :)

---

### Post by WasabiVengeance on 2008-02-19
Sorry to hear about your trouble man. 

I also tried changing my sata controller mode from compatiblity to AHCI in my bios. No luck.

I'm probably going to try changing some hd parameters tonight, will post the results.

---

### Post by jrusso2 on 2008-02-19
When hard drives go bad they usually do it when they are new or after 3 years

---

### Post by C14rk3y on 2008-02-20
Im still not sure what to do then.  I really dont want to re-install (again), as it seems to eventually do the same thing.  Someone please help, I hate being on the M$ side.

You would think having a brand new hd would be a good thing, lol.

I've installed the OS three times now thinking I had fixed the problem.  Im not an idiot and I've been reading these forums for days before posting.  I just dont know what to do anymore.  I know I can get this working, I just need some help now, lol.  It works great for 24-48 hrs then gives me that msg.  I know what sda its on and Im doing exactly what you guys have posted here in these forums previously.  I can write the exact msg I get if that helps....

And Im very sorry to WasabiVengeance, as I've hijacked your thread.  Im just having the same problems and thought it was better than starting a new topic :)

---

### Post by WasabiVengeance on 2008-02-21
Nothing to be sorry for. The issues are the same and we both need a solution :/ 

Btw, what chipset are you using? My t60 has an intel 945gm I believe. If we have the same chipset, perhaps ubuntu is shipping with a flakey driver?

---

