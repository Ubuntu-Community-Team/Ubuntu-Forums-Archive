---
title: "Other OS linked and mounted in Ubuntu dual boot"
date: 2018-02-22
forum: General Help
---

### Post by maffys on 2018-02-22
Hi to all, i’m new to linux and i’ve installed Ubuntu on my pc (No windows, it is a dedicated pc for linux).
I installed Ubuntu erasing the entire disk. Operation successful.
Booted the pc with Kali linux live and resized Ubuntu partition with gparted. 
Installed Kali on the remaining free space on the disk. Successful.
Booted again with kali live and again with gparted resized kali partition to make room to another linux distro in the future.

The problem is, when i boot from grub into Ubuntu, Kali is also mounted as a device. I can see the root directory for example. I tried from “gnome-disks” to deactivate automount of Kali and hiding it from the menu bar but if i go to the file manager, Kali is listed again as an external device and i can access the kali files from the file manager ( in a mnt folder, before the operation with gnome-disks was in /media/user(my username, very original).

There is a way to isolate completely Kali from Ubuntu. Thank you and have a good day

---

### Post by TheFu on 2018-02-22
No.  Connected disks that can be read, can be read.  If you don't want them read, either don't connect them or encrypt them.  Any other methods are just superficial solutions.

---

### Post by maffys on 2018-02-22
Ok, thank you. But from kali if i unmount ubuntu the file are not accessible. There is a way to automatically unmount ubuntu. Maybe from fstab?

---

### Post by Morbius1 on 2018-02-22
What version if Ubuntu are you using and what does your listing in /etc/fstab look like for this partition.

In general the way you used to handle this thing is counter-intuative. In order to prevent the mounting of a partition at boot you need to add it to fstab.

I played around with Disks - it's something I think should be removed from the repository - and managed it to get this entry for an ext4 partition that I do not want to automount:
> /dev/disk/by-uuid/551e67cb-a437-4353-b6e8-9404e2e62700 /mnt/551e67cb-a437-4353-b6e8-9404e2e62700 auto nosuid,nodev,nofail,noauto 0 0
Since it's mounted under /mnt it will not display on the side panel of nautilus and noauto will prevent it from mounting at boot time.

You can still mount it if you had a mind to but you would need to do it as sudo in the terminal. Not something you would do by mistake.

I did notice a rather curious bug however - it may have always been there in Disks: If the x-gvfs-show option is listed in fstab it becomes mountable again in Nautilus even though the noauto option is listed and without the user option present.. Must be a systemd thing

---

### Post by maffys on 2018-02-22
I understood quite nothing. I'm a noob at linux but seems i fixed the problem. From ubuntu, via gnome-disks, selected mount options for kali partition, disabled "mount at startup" and "show in user interface". Same procedure from kali, modyfing ubuntu partition. Now finally i can't see the partitions mounted and neither system files from /media or /mnt Maybe all this for someone is not a problem but i wanted 2 os completely isolated each other.

---

### Post by again? on 2018-02-22
Custom mount options made in gnome-disks are written to your fstab file.
Post the contents of /etc/fstab

I use gnome-disks to stop a number of linux installs automounting which works here.

[COLOR="#FF0000"]Edit:[/COLOR] I see you fixed it. 
If used properly gnome disks should work for your purpose.

---

### Post by Morbius1 on 2018-02-22
> disabled "mount at startup" and "show in user interface"
The first one added **noauto** to fstab and the second one removed** x-gvfs-show ;)**

---

### Post by maffys on 2018-02-22
[IMG]https://ibb.co/hnCN8H[/IMG][https://ibb.co/c1spo]("https://ibb.co/c1spoH")

[https://ibb.co/hnCN8H](https://ibb.co/hnCN8H)

Sda1 is the partition with ubuntu and sda6 with kali.

Fstab is from ubuntu

---

### Post by TheFu on 2018-02-22
> **maffys said:**
> I understood quite nothing. I'm a noob at linux but seems i fixed the problem. From ubuntu, via gnome-disks, selected mount options for kali partition, disabled "mount at startup" and "show in user interface". Same procedure from kali, modyfing ubuntu partition. Now finally i can't see the partitions mounted and neither system files from /media or /mnt Maybe all this for someone is not a problem but i wanted 2 os completely isolated each other.

Hiding the partition works and may be sufficient for your desires, but it is still there and still available to anyone for mounting with slight Linux skills. Also someone new using partitioning tools might easily wipe the other OS (or any unused partitions) accidentally. This is fairly common if the person forgets or doesn't understand partitioning and disk layouts.  I've wiped a few partitions accidentally myself - long, long, ago.

It is not "*completely isolated*" in the way a security researcher would need. Security people use different computers for research from their normal desktops almost always to avoid cross contamination issues.  In CTF sessions, attacking others on the same network (the opponents) and messing with their systems happens from time to time.

To simulate the same level of isolation, unplug the disk that isn't being used.  That will bring other complications, however.

_Completely isolated_ is a hard standard to achieve on a single computer.

---

### Post by Dennis N on 2018-02-22
Booting into Ubuntu OS on start up, a dual boot or multiboot system would only automount disk partitions listed in Ubuntu's /etc/fstab file. Other partitions that you could mount from the file manager will display under the "other locations" option in the file manager side pane, but until you click on one of these in the "other locations" window, those are not mounted.

---

### Post by maffys on 2018-02-22
I have nothing on this pc and if accidentally i would format the hd, nothing happens, is only a linux "sandbox". The pc has only 1 partitioned hard disk with the 2 os, so unplugging it would be useless :D
This is not my principal pc. Probably what i've done is enough. Maybe if i would get enough skill i can fix it completely :)
Thank you to all.

---

