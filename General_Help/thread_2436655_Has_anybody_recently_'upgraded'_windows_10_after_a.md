---
title: "Has anybody recently 'upgraded' windows 10 after a reboot back to xubuntu?"
date: 2020-02-10
forum: General Help
---

### Post by makem2 on 2020-02-10
I ran, emphasis on the 'ran' a dual boot windows and xubuntu for years, avoiding upgrading windows as I use IE for 10 minutes and then get out as quick as I can.

In the past I have 'upgraded' windows to my cost and had to spend ages getting advice and then fixing grub, so...................I keep away from any updates.

This time, I did not have a choice, windows  got started with it's update as soon as I rebooted from it back to xubuntu, but this time, windows is corrupt! Jeez, why have we been tied to this for what seems like a lifetime?

Anyway, as grub still works I can choose to boot windows at which point I am allowed to log in and then faced with a white screen on which I see:

Welcome
Basics
Network
Account
Services

Do more with you voice

Below this is a scrollable box with a tiny button below.

To cut a long story short, I can only use ctrl alt delete to get out of that screen at which point I can lock, switch user,sign out,change password, go to task manager, or cancel.

 The only other way to do anything useful there is to choose from four icons at the bottom right hand corner allowing language, two other icons and a reboot/shutdown option.

Rebooting brings me back to the white screen. So, windows 10 is not unavailable. Ive, had 'blue screen of death', but now they have changed the colour!!!

I know this is a windows problem but I ask here in the hope somebody has followed this 'upgrade' and found how to sort it. I really really don't want to install windows again from scratch!

```

makem@ssdTOSH:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  3.0M  1.6G   1% /run
/dev/sda2      ext4       19G   13G  4.9G  73% /
tmpfs          tmpfs     7.8G  100M  7.7G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop1     squashfs   45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop2     squashfs   45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop0     squashfs   55M   55M     0 100% /snap/core18/1650
/dev/loop3     squashfs   90M   90M     0 100% /snap/core/8213
/dev/loop4     squashfs   55M   55M     0 100% /snap/core18/1668
/dev/loop6     squashfs  157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop5     squashfs  132M  132M     0 100% /snap/telegram-desktop/1034
/dev/loop7     squashfs  161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop8     squashfs   90M   90M     0 100% /snap/core/8268
/dev/loop9     squashfs  132M  132M     0 100% /snap/telegram-desktop/1038
none           tmpfs     1.0G   68K  1.0G   1% /media/ramdisk
/dev/sda1      vfat      234M  6.1M  228M   3% /boot/efi
/dev/sda3      ext4      199G   43G  147G  23% /home
/dev/sdb7      ext4       24G   23G  1.4M 100% /media/testing
/dev/sdb6      fuseblk   810G  620G  191G  77% /media/WinData
tmpfs          tmpfs     1.6G   16K  1.6G   1% /run/user/1000
makem@ssdTOSH:~$

```

My partition table is gpt.

All partitions seem intact, but, as it does boot to 'something' then the 'boot part must be correct. It's what happens when it gets to bliddy windows.

As it's late here, tomorrow, I will attempt to get help from a windows forum but have little confidence I will.

Note: I cannot use a virtual PC, it will not work with a chinese security dongle.

---

