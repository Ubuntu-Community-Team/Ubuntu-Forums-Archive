---
title: "tweak after re-sizing swap partition"
date: 2008-06-17
forum: General Help
---

### Post by mvaranda on 2008-06-17
Just a quick note that might help someone else:

I used a rescueCD to increase the swap partition after I had increased RAM.
However, Ubuntu 8.04 was not recognizing the new swap partition.
System Monitor->Resources was showing 0 bytes (0.0%) of 0 bytes.

the fix:

used gparted to find the swap partition's name (sda6 for my machine).

then:

me@-ubu-lt:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 07D7-080E -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 443621da-00cc-4447-bdbb-24a6c61912f3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-06-17 14:16 4adf4f76-8996-40a4-9d72-3325d1294256 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 F4085014084FD3F0 -> ../../sda2


so the new UUID for sda6 is 443621da-00cc-4447-bdbb-24a6c61912f3
Then I needed to fix it in /etc/fstab file:

sudo gedit /etc/fstab

and update the line for sda6:

# /dev/sda6
UUID=443621da-00cc-4447-bdbb-24a6c61912f3 none            swap    sw              0       0

last thing I did:

sudo swapon -a

Then I got it back to work :-)

Have fun,
MV

---

### Post by JC Cheloven on 2008-06-18
> **mvaranda said:**
> 
...used gparted to find the swap partition's name (sda6 for my machine).
then:

me@-ubu-lt:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 07D7-080E -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 443621da-00cc-4447-bdbb-24a6c61912f3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-06-17 14:16 4adf4f76-8996-40a4-9d72-3325d1294256 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-06-17 18:31 F4085014084FD3F0 -> ../../sda2

so the new UUID for sda6 is 443621da-00cc-4447-bdbb-24a6c61912f3


Just a note. When finding out the UUIDs, perhaps this command is easier to remember: ```
sudo blkid
```
Greetings

---

