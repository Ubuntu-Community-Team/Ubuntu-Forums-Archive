---
title: "this just started today"
date: 2024-04-01
forum: General Help
---

### Post by jadaja on 2024-04-01
i have an hp pavilion g7 i7 16 gb ram 650 gb hdd laptop. i went to do updates/upgrades via the terminal and got this; dpkg: unrecoverable fatal error, aborting:tabase ...  loading files list file for package 'libapparmor1:amd64': cannot read /var/lib/dpkg/info/libapparmor1:amd64.list (Input/output error)
E: Sub-process /usr/bin/dpkg returned an error code (2)


i've tried to do apt -f install, sudo dpkg --configure -a, and various other things that i can't even recall now and none of them worked. i saw 'similar' stuff online but nothing to do with the above file specifically. i've racked my brain to figure it out. i do know my hdd may be going bad but i don't have the money to get a new one at the moment and i have no clue as to when i'll be able to get a new one for my old system. if you can help me figure out how to fix this problem so i can do updates/upgrades w/o buying a new drive thanx.

---

### Post by jadaja on 2024-04-01
almost forgot i'm using jammy jellyfish 22.04.4

---

### Post by Impavidus on 2024-04-02
apt can't read the list of installed files for the package libapparmor1:amd64 due to file corruption. That sounds like a broken harddrive indeed.

Maybe reinstalling linapparmor1 helps. Maybe apt can still do so:```
sudo apt reinstall libapparmor1
```Or maybe not. In that case, dpkg may do the trick, but it's more manual.

---

### Post by jadaja on 2024-04-16
i ended up buying a new drive. the old 1 was so bad that i couldn't even do a backup of it so i had to use a the backup that i used when i put jammy on it originally. oh well. maybe i can still get stuff off it once i get an external enclosure. i'm gonna place a solved marker on this one. i was having some weird problems being caused by that old drive, like it wouldn't let me finish watch a tv series on dvd for some reason, was stuck on season 2 disk 2 ep 3. awfully weirdly specific, to be precise, it was the reboot of kung fu. altho i haven't had a chance to retry, yet, i suspect it was the reason i couldn't watch avatar: the way of water too and to i tried disks from 2 different libraries. weird crap like that.

---

