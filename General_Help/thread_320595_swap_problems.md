---
title: "swap problems"
date: 2006-12-17
forum: General Help
---

### Post by sdhoigt on 2006-12-17
I have an 80GB hard drive with one 20GB partition (/dev/hda1) followed by a 1GB extended partition containing a swap partition (/dev/hda5).

While booted in a live CD, I deleted the extended/swap partition, grew the 20GB partition to 78GB, and added back and grew the extended/swap partition (still /dev/hda5) to 2GB.

When I booted (Kubuntu Edgy), the swap no longer mounted.  I took a look at fstab and noticed this line for the swap mount:
[FONT="Courier New"]UUID=f957f278-1813-448b-8612-246487279ea1 none swap sw 0 0[/FONT]

So I figure I just need to determine what the UUID is now for the newly relocated swap.  This command accomplishes that:
[FONT="Courier New"]$ ls /dev/disk/by-uuid -al
...
5eda3f56-38f7-4cab-872a-1b1aff4e9554 -> ../../hda5
...[/FONT]

Ok, so I copy this UUID over the old UUID in fstab, reboot and the 'free' command now shows the swap's available space again.  I'm happy.  :D 

:-? However, it's been a few weeks, and I checked 'free' just now, and the swap isn't being mounted again.  I double-check the UUID (ls command above) and compare it w/the fstab entry, but they are in sync.

Here's some system info:
[FONT="Courier New"]$ free
...
Swap:            0          0          0

$ sudo fdisk -l
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9599    77103936   83  Linux
/dev/hda2            9600        9729     1044225    5  Extended
/dev/hda5            9600        9729     1044193+  82  Linux swap / Solaris

$ ls /dev/disk/by-uuid -al
total 0
drwxr-xr-x 2 root root 100 2006-12-17 12:56 .
drwxr-xr-x 5 root root 100 2006-12-17 12:56 ..
lrwxrwxrwx 1 root root  10 2006-12-17 12:56 5eda3f56-38f7-4cab-872a-1b1aff4e9554 -> ../../hda5
lrwxrwxrwx 1 root root  10 2006-12-17 12:56 76522cf2-9060-41ae-9f9a-2e91b1c34bef -> ../../hda1
lrwxrwxrwx 1 root root  10 2006-12-17 12:56 fb07e3d5-d988-4ea4-b435-e087994ec09f -> ../../hdb1

$ cat /etc/fstab | grep swap
# /dev/hda5       none            swap    sw              0       0
#UUID=f957f278-1813-448b-8612-246487279ea1 none swap sw 0 0
UUID=5eda3f56-38f7-4cab-872a-1b1aff4e9554 none swap sw 0 0[/FONT]

Thanks for any ideas.
SD

---

### Post by taurus on 2006-12-17
Edit your /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and remove the old entry for your swap
```
UUID=5eda3f56-38f7-4cab-872a-1b1aff4e9554 none swap sw 0 0
```
and replace it with the new one.
```
/dev/hda5   none   swap   sw   0   0
```
Reboot and see what happens.
```
free
```

---

### Post by chalex on 2006-12-17
what does `sudo swapon -s` tell you?  `sudo swapon /dev/hda5`?

I guess you don't need to use the UUID; you can just specify /dev/hda5 like taurus says, but it'd be nice to know why it's not working.

---

