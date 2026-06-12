---
title: "[SOLVED] kernal panic root fs"
date: 2008-04-18
forum: General Help
---

### Post by Gripp on 2008-04-18
i was using kformula and my system locked up.. upon reboot i got two errors

33.893414
invalid compressed format (err=1)

33.894222
kernal panic - not syncing: VFS: mount root fs on unknown block (0,0)

looking around the only solution that i could find was 

On Live CD
Open Terminal and enter

Code:
sudo mount /dev/hda1 /mnt
sudo chroot /mnt /bin/sh
sudo update-initramfs -u


but this being a Wubi install i'm not certain how to correctly apply this.

when fixing my install error i changed the boot laoder to run on hd(1,0) 
what drive would that correlate to in the Wubi case?

---

### Post by Gripp on 2008-04-18
i got it fixed :guitar:  
i couldn't mount any hd** or sd** though they showed in my /dev folder..
but i was able to go into /media/<name of my drive>/ubuntu/disks/root.disk to get my Wubi install mounted
i think this was becuase i have my Wubi installed on my D: drive, rather than my C:

for others who run into this problem the method was:

boot to live CD (i.e. download and burn CD, change bios to boot from disk... etc) 

```

sudo mkdir /win
sudo mount -o loop /media/<nameOfMyDrive>/ubuntu/disks/root.disk /win
sudo chroot /win /bin/sh
update-initramfs -u 
```
 (for whatever reason it didn't recognize the sudo command after the chroot)

then i rebooted and got right in :)

---

### Post by Gripp on 2008-04-20
for whatever reason this has happened again.... this time just on a normal reboot

i guess my new problem is how to get that to stop... :(

---

