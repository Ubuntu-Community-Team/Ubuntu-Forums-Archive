---
title: "User permissions changed..."
date: 2006-10-05
forum: General Help
---

### Post by aznlnx on 2006-10-05
I accidentally removed my user in the ADMIN group and now i have no access to any administration rights. ](*,) 

How do I get the permissions back to get admin to my user?

I'm such a newb but i'm loving this OS. So much fun.

My original intentions was to gain access to configure my splash screen but the system told me I was denied. So my logic told me to give me rights to do so.....and um yeah you know the rest of the story..(OOOPS) .hahaha

Can someone please assist?

THanks so much.

---

### Post by aznlnx on 2006-10-05
bump....help me please! I want to tweak and I can't! :(

---

### Post by jalm111 on 2006-10-06
Looks like you pwned yourself  :)

reboot your system and stop at the grub loading screen (hit escape or something). Than go down to the line that says:
kernel          /vmlinuz-2.6.15-27-386 root=/dev/hdb4 ro quiet splash
and change it to (hit e and than e again i think):
kernel          /vmlinuz-2.6.15-27-386 root=/dev/hdb4 ro init=/bin/bash

thank boot using that option. You will now be on your system as root but your / will be mounted read only so you can't change anything. Here's how you remount it

mount -o remount,rw -t ext3 (or whatever your / is) than /dev/hd_something / 

if you dunno what /dev/something should be do mount-l and you'll see:
/dev/hdb4 on / type ext2 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)

the first one is the / so in my case it would be /dev/hdb4

now that we can actually write to / as root you simply need to add yourself back to the group (usermod -G[capital if you wanna append admin to groups that user is already in, lower case if you wanna make the user a member of admin and ONLY admin group adn make admin the main group anyways...] admin username)

then reboot and you should be good. I know this is kinda dirty looking but it's also late and I'm tired .... :)

---

