---
title: "Setting Write Permissions On Ext4 for New computer"
date: 2020-09-27
forum: General Help
---

### Post by johnsmoke on 2020-09-27
I just got a new computer pre-loaded with Ubuntu 20.04. I can't drag my backed up files over to the desktop or anything. I need to set write permissions. I followed instructions I found on a website... but still am having issues. 

I identified my drive as SDA5, found my UUID:

/dev/sda5: UUID="0da43e18-2c6f-4329-b070-eb8330d6ef85" TYPE="ext4" PARTUUID="482e2b8c-05"

When I enter ll /media/$USER to find where it's mounted I get this:

total 12
drwxr-x---+ 3 root          root          4096 Sep 27 12:24 ./
drwxr-xr-x  4 root          root          4096 Sep 27 12:24 ../
drwxrwxrwx  1 psychtrailmix psychtrailmix 4096 Sep 24 08:51 2B93D4A333F3948F/

So my UUID doesn't even pop up here.

I am trying to continue the process with:

sudo chgrp adm /media/psychtrailmix/0da43e18-2c6f-4329-b070-eb8330d6ef85

But I just get the below message:

chgrp: cannot access '/media/psychtrailmix/0da43e18-2c6f-4329-b070-eb8330d6ef85': No such file or directory


Any help is appreciated.

---

### Post by deadflowr on 2020-09-27
Look at blkid to determine what UUIDs exists and for which Partitions.
```
sudo blkid
```

---

### Post by johnsmoke on 2020-09-27
> **deadflowr said:**
> Look at blkid to determine what UUIDs exists and for which Partitions.
```
sudo blkid
```

I already did that and get below:

/dev/sda1: UUID="95E5-8111" TYPE="vfat" PARTUUID="482e2b8c-01"
/dev/sda5: UUID="0da43e18-2c6f-4329-b070-eb8330d6ef85" TYPE="ext4" PARTUUID="482e2b8c-05"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"

I already determined my UUID is 0da43e18-2c6f-4329-b070-eb8330d6ef85 from the above output.

I just don't know where to go from here.

---

### Post by deadflowr on 2020-09-27
Could it be that the device is mounting at the  2B93D4A333F3948F/ location
which might be an existing directory name.
look at 
```
mount
```
or try grepping it to something like either
```
mount | grep /dev/sd
or
mount | grep /media
```

---

### Post by The Cog on 2020-09-27
Or **[FONT=Courier New]lsblk[/FONT]** will probably also show what you need to know.
```
lsblk | grep -v snap
```

---

### Post by johnsmoke on 2020-09-27
I get this with mount CMD for the drive:

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)

---

### Post by johnsmoke on 2020-09-27
I get this with lsblk:

loop0    7:0    0    55M  1 loop /snap/core18/1880
loop1    7:1    0 255.6M  1 loop /snap/gnome-3-34-1804/36
loop2    7:2    0  55.3M  1 loop /snap/core18/1885
loop3    7:3    0  29.9M  1 loop /snap/snapd/8790
loop4    7:4    0  30.3M  1 loop /snap/snapd/9279
loop5    7:5    0  62.1M  1 loop /snap/gtk-common-themes/1506
loop6    7:6    0  49.8M  1 loop /snap/snap-store/467
loop7    7:7    0  97.1M  1 loop /snap/core/9993
loop8    7:8    0 114.9M  1 loop /snap/audacity/699
loop9    7:9    0   140K  1 loop /snap/gtk2-common-themes/13
loop10   7:10   0  21.1M  1 loop /snap/deluge-lukewh/13
loop11   7:11   0 125.7M  1 loop /snap/deadbeef-vs/5
loop12   7:12   0  66.7M  1 loop /snap/kompozer/4
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   931G  0 part /
sr0     11:0    1  1024M  0 rom

---

### Post by deadflowr on 2020-09-27
Oh, it's the root filesystem, that's why it's not in /media.

---

### Post by johnsmoke on 2020-09-27
Weird.... I can't copy to desktop... but I can copy to Downloads folder...

---

### Post by The Cog on 2020-09-27
> **johnsmoke said:**
> I get this with mount CMD for the drive:

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)

Eh? So where are your backed up files (what is the path to them)? 
sda5 is your root filesystem. Are the files "backed up" to somewhere else on the same drive?

---

### Post by johnsmoke on 2020-09-27
Well, I guess the drive does have write permissions. But I just can't copy directly to my desktop. If I open a file browser window, navigate to desktop from there, I can copy to that folder. I guess I just need to figure how to set permissions so I can just drag folders directly onto my desktop.

---

### Post by johnsmoke on 2020-09-27
> **The Cog said:**
> Eh? So where are your backed up files (what is the path to them)? 
sda5 is your root filesystem. Are the files "backed up" to somewhere else on the same drive?

I just got a new computer. I'm popping in a flash drive with the items I need on my desktop, I'm just trying to drag them from the USB drive to the desktop, it won't allow me to do this unless I open a file browser window, then navigate to desktop folder from there.

---

### Post by deadflowr on 2020-09-27
Oh, oh oh oh.
It's not you, it's the desktop.
They broke it on purpose and removed the ability to drag and drop.
You can place files in the Desktop folder to show on the desktop.

The old desktop used the file manager to handle it, but they removed that function and replaced it with a gnome-shell extension, which is not very refined.

A fix to get the old function back would be to install and setup nemo to handle the desktop.
Something like here: [https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04]("https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04")

---

### Post by johnsmoke on 2020-09-27
> **deadflowr said:**
> Oh, oh oh oh.
It's not you, it's the desktop.
They broke it on purpose and removed the ability to drag and drop.
You can place files in the Desktop folder to show on the desktop.

The old desktop used the file manager to handle it, but they removed that function and replaced it with a gnome-shell extension, which is not very refined.

A fix to get the old function back would be to install and setup nemo to handle the desktop.
Something like here: [https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04](https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04)

Ahhh gotcha! Well, a minor inconvenience I guess. I don't have a problem placing things in Desktop folder to get them to show up there. So I'm good right now. THANK you very much!

---

### Post by johnsmoke on 2020-09-27
A side note, in older Ubuntu I was able to completely hide the sidebar, launch doc whatever you call it. To where I move the mouse to the left and it shows up when I do that. Is there any way to do this in 20.04?

---

### Post by johnsmoke on 2020-09-27
I moved launcher to bottom, seems to work just as well, so I'm good.

---

### Post by deadflowr on 2020-09-28
> **johnsmoke said:**
> A side note, in older Ubuntu I was able to completely hide the sidebar, launch doc whatever you call it. To where I move the mouse to the left and it shows up when I do that. Is there any way to do this in 20.04?

> **johnsmoke said:**
> I moved launcher to bottom, seems to work just as well, so I'm good.

The dock is called ubuntu-dock and is based on a popular gnome extension called dash-to-dock.
There are some extra settings builtin but hidden which can be set or changed in dconf editor at 
org > gnome > shell > extensions > dash-to-dock.

Also gnome shell's extension system allows for completely overhauling extensions and replacing them with ones you want.
In some user cases they actually switch out (or disable) ubuntu-dock with another popular extension called dash-to-panel.

You can find a whole big bunch of extensions over at [https://extensions.gnome.org/]("https://extensions.gnome.org/")
Extensions can be directly installed from there but you need a package in Ubuntu installed called chrome-gnome-shell. It's in Ubuntu repositories.
(chrome-gnome-shell allows installing extensions through a browser, it works in both chromium-based and firefox browsers)

Ubuntu also pre-packages a few extensions that can be installed through the package manager.
You find them either through synaptic if installed or using apt search like
```
apt search gnome-shell-extension
```

---

