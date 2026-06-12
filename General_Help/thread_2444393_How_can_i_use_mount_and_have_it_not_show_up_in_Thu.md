---
title: "How can i use mount and have it not show up in Thunar"
date: 2020-05-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-05-29
Xubunut 20.04
mount --bind /tmp/$USER-Desktop /home/$USER/Desktop
*/tmp/$USER-Desktop does get chmoded to now allow all users access
How can I a make this not show up under devices in Thunar?

---

### Post by TheFu on 2020-05-29
I'd be nervous about putting a mount in /tmp/ .   /tmp gets wiped at every boot.  Better to use /media/$USER-Desktop or /mnt/$USER-Desktop.  I'd also be nervous about overriding permissions on any user directories, especially if they are real people.

Are you doing this to get around some snap problems?  Both /media/ and /mnt/ should be available to snaps with the removable-media connection enabled.  In my testing with NFS mounts, the bind mount didn't help.  OTOH, if you've placed all users isn't a "users" group, and setup that group to be rwxs on the data directory, fantastic!

To enable the mount, the x-gvfs-show option is needed in the fstab or mount options. If that option isn't provided, then the mount shouldn't be displayed in any file manager. There have been a few launchpad bugs about this.

---

### Post by pqwoerituytrueiwoq on 2020-05-29
i like to keep my desktop clean, so storing it in /tmp makes that happen (i can't be lazy and not delete my temporary stuff)
so i should mount it like this to make it NOT appear as a device in thunar?
[FONT=courier new]mount --bind -o x-gvfs-show /tmp/$USER-Desktop /home/$USER/Desktop[/FONT]

i was using a ram disk for /tmp so i had a dynamic shared space for /tmp and my temporary personal files, i just put my old SSD in my system and my new motherboard support more drives than my old one and made that ssd a scratch disk for /tmp, my desktop, and swap to get swap off mechanical storage since i was using some of it cause my ram disk uses 50% of my ram, and for the last few days i had been using 2.5gb swap which is slow on a HDD

---

### Post by TheFu on 2020-05-30
interesting idea to put a ~/Desktop into /tmp/.  i just drop files into /tmp/ directly.

You really want swap to be on a slow disk so that you can "feel" when the system gets slow and close some programs before it crashes.  To limit how quickly swap gets used there is a kernel parameter that can be configured ... let me look it up.
Add that to the bottom of /etc/sysctl.conf 
```
vm.swappiness = 10
```
and run **sudo  sysctl -p**
Check that it was applied using **sysctl -a**

Of course, you can create a RAM disk and mount it where ever you like.  i don't have extra RAM to blow that way, so never considered doing anythng like that before.

Without x-gvfs-show in the mount options, no file manager should show the mount.  Sounds like a bug.  Do other file managers have the same issue?  Does the original mount, not the bind mount, have the x-gvfs-show option?
Most posts WANT the mounts to be displayed: [https://unix.stackexchange.com/questions/401291/how-to-get-the-trash-and-x-gvfs-show-partitions-on-thunar-via-awesomevm](https://unix.stackexchange.com/questions/401291/how-to-get-the-trash-and-x-gvfs-show-partitions-on-thunar-via-awesomevm)

---

### Post by Morbius1 on 2020-05-30
It is not entirely clear to me what you are trying to do here so this is more a generic answer to doing bind mounts under a user home directory or /media:

> so i should mount it like this to make it NOT appear as a device in thunar?
[FONT=courier new]mount --bind -o x-gvfs-show /tmp/$USER-Desktop /home/$USER/Desktop[/FONT]
Just the opposite:
> [FONT=courier new]mount --bind -o [COLOR=#ff0000]**x-gvfs-hide**[/COLOR] /tmp/$USER-Desktop /home/$USER/Desktop[/FONT] 

I should note that the ability to use x-gvfs-hide with a bind mount in this circumstance is only possible because a bug was fixed. I don't think it would have worked prior to 20.04.

---

### Post by pqwoerituytrueiwoq on 2020-05-30
> **TheFu said:**
> You really want swap to be on a slow disk so that you can "feel" when the system gets slow and close some programs before it crashes.
Well i have 16GB ram with 8 allocated to a file system i managed to run out of 8gb, but with what i did with that old sata 2 SSD freed up that 8GB so i can use 16 while giving me 16GB on the ssd and a 9gb /tmp
it is not like a sata2 30GB SSD is really worth anything now, it is enough for a linux boot drive or a scratch disk and since i have a faster (access time 7.5x and read is 10.9x) /root drive now
the only way i can see using swap in this config is to have a memory leek (i think ff has a very slow one with my addons)

for some reason i think 18.04 did not hard limit me to 8GB ram with my ram disk and would just push my unused fs space to swap before using swap for my so i could have 10gb used for the only time i remember really using swap was a out of control memory leak
even the way i had it it would not slow the system with swap on a hdd from a memory leak but i would hear the HDD and would ask why are you spinning up and look at my ram usage and go what the...
i have my top panel full of system monitoring data, most of them i made with the xfce4-genmon plugin

i have 2 HDDs and 2 SSDs hooked up along with a pair of hot swap bays
120gb nvme (x4 lakes) 120gb ssd
500gb 7200rpm hdd (primary high access files)
1tb 7200rpm hdd (additional stuff (VM disk and anything that would use a large amount of my primary drive), previously included swap)
30gb sata2 ssd
and i sill have a open sata port, but i would trade that along with a PCIe slot for a nvme drive
then i have a 2tb drive for backing up data (that i do not do as often as i should...)


> **Morbius1 said:**
> Just the opposite.....I don't think it would have worked prior to 20.04.
thanks i'll give that a shot, well i am using 20.04 so...

---

### Post by pqwoerituytrueiwoq on 2020-06-03
so this appear to be far more effective than i expected
the mount point is complete hidden from the file system
it does not appear in ls /tmp and i can create a directory of the same name in /tmp
somehow /tmp/ and my desktop do not have the same remaining free space (it is near where it should be so the mount is active)
edit: i just borked my /etc/fstab and it somehow did not break everything, i had my ssd partition type set as tmpfs when it was ext4, after fixing that all is as expected

---

