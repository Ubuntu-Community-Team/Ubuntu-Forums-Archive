---
title: "Uh Oh, grub rescue. error: failure reading sector 0x112908 from 'hd0'"
date: 2019-09-30
forum: General Help
---

### Post by scruffycrumpet on 2019-09-30
[http://paste.ubuntu.com/p/YWKndsrWYD/](http://paste.ubuntu.com/p/YWKndsrWYD/)

I think the trouble started when my computer froze and i stupidly did a hard reset.

When I rebooted, i got a (Initramfs) console, and after googling for a bit i ran a manual fsck a couple of times, and now im totally stuck.

upon boot i get:
```

error: failure reading sector 0x112908 from 'hd0'
Entering rescue mode...
grub rescue> 
```

I tried boot repair, no recommended repair. i tried reinstalling, i REALLY dont want to lose all the work on my computer, and it said there was no OS found on the computer.

Any ideas? thanks

---

### Post by guiverc on 2019-09-30
'*failure reading sector*' sounds like a hardware issue to me with your disk, and `fsck` or trying to repair `grub` is the last thing I would do.  I would check on the health of your hdd well before I tried to use it (ie. read & particularly write to it).

I would suggest booting a 'live' image (so disk isn't being used), then check the SMART (self monitoring advanced analysis & reporting tech. found in drive's chips, ie. reading it won't use disk surface).

I would ensure the disk is healthy, maybe it's just a bad block you can lock off, but I'd access health first using `smartctl`, `gnome-disks`, `kde partition manager` or whatever tool you prefer (or have on the 'live' system booted).

If the disk is dying - you need to know that ASAP - so you can use any life left to get your data off, not use it to try & return it to normal.  If it's healthy, you needn't worry and can then start trying to get it to working shape...

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by scruffycrumpet on 2019-09-30
alright i have made a backup using ddrescue, but to be clear i have no idea what im doing. I dont understand the file type that ddrescue made, but its only ~500 MB so im skeptical that its what im looking for. 

Also, the right click function isnt working on my live ubuntu system for whatever reason so im having trouble copy pasting the response from smartctl, i tried writing the output to a file with '> myfile.txt' and got premission denied.

is there anything else i can do to try to save my files before i reinstall ubuntu?

---

### Post by guiverc on 2019-09-30
`gnome-disks`, `kde partition manager` or almost any gui tool is easier to understand than `smartctl` If you loaded a desktop 'live' I'd suggest the gui tools as they don't just provide all data, instead give a summary which is more suitable to users (with quick 'pre-fail", "old-age", "OK" etc instead of reams of figures).

I won't advise on `ddrescue` as I've only rarely used it (if a drive fails, I just go to backups)

if it were me I'd only copy the files I needed, but I'd not even do that until the health of the drive was ascertained. Smart uses data stored on chips so doesn't risk any further damage.  I also wouldn't re-install until you've verified the 'backup' (a simple copy of files allows easy exploration/opening of files to ensure they're okay - the ddrecscue image may allow for this, I don't know)

You haven't said what Ubuntu 'live' system you're using so I can't help there (except the redirect to >myfile.txt error was because you weren't in a /home/$USER/ directory and thus didn't have permissions).

When I was happy with the drive (SMART study completed), I'd then run `badblocks` ([https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia) but it tells you little) and then assess any bad blocks detected (where they used? where on the file-system (ie. what files are potentially corrupted), then decide if a repair is possible, or I should re-install.  If i re-installed, I'd use 'something-else' & not-format so it doesn't erase any data there. I'd have my backups, but this saves time if you don't have to restore data... It also will re-add any additional packages you added to your system automatically (if from known/Ubuntu sources) again saving setup time.

ie.  SMART check, badblocks - then decide on plan would be my approach.

---

