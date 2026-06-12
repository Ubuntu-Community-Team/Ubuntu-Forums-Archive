---
title: "Address or reference for a partition that will remain constant after reboot?"
date: 2017-05-14
forum: General Help
---

### Post by ra7411 on 2017-05-14
[COLOR=#000000][FONT=Arial] I'm using Ubuntu 16.04.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]How do you create an address or reference for a partition that will remain constant after reboot? [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Using Chrome out of sda1, I like to use a tab for viewing videos that I have in sdb1. I do It by dropping the path to sdb1 into the URL bar in Chrome. If the address remained constant, I could make it a Chrome bookmark, which would be handy.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here’s an example of a path I’m using. These paths never work after a reboot. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]file:///media/ra/1tb%20Movies-video/3%20TC%20dvd%20vids/Main/1%20A%20Visual%20Guide%20to%20the%20Universe%20with%20the%20Smithsonian/A%20Visual%20Guide%20to%20the%20Universe%20with%20the%20Smithsonian.mp4[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Is there any way to make this bookmark thing work?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-05-14
Is the partition on an external drive which automounts?

If you give the partition a Label with, for example, gparted, it will always mount to /media/username/Label.
If the partition is on an internal disk that is therefore always present at boot you will need to edit /etc/fstab to give the partition a known mountpoint.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by ra7411 on 2017-05-14
> **ajgreeny said:**
> Is the partition on an external drive which automounts?

If you give the partition a Label with, for example, gparted, it will always mount to /media/username/Label.
If the partition is on an internal disk that is therefore always present at boot you will need to edit /etc/fstab to give the partition a known mountpoint.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
> 
Is the partition on an external drive which automounts?

No, it's an internal HD that's always present at bootup.

> If the partition is on an internal disk that is therefore always present at boot you will need to edit /etc/fstab to give the partition a known mountpoint.

OK, I was guessing it would be something like that. 
I'm a little uneasy about messing things up and having to dig out from a screw up.

Here's the blkid from the machine - is it possible to get a specific terminal input to get a fixed mount point? It's sdb1 that I'm trying to be able to bookmark in Chrome.
```


/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/sda1: UUID="a37c8db6-2d79-42ab-92e1-cd0d735b9004" TYPE="ext4" PARTUUID="39beeb72-01"
/dev/sda5: UUID="6ea266ce-a91d-498d-bef3-927e08e9bc3d" TYPE="swap" PARTUUID="39beeb72-05"
/dev/sda6: LABEL="/home" UUID="c08464b4-5917-46c8-b595-b6a6533863b2" TYPE="ext4" PARTUUID="39beeb72-06"


/dev/sdb1: LABEL="1tb Movies-video" UUID="25bb9f4d-7f2c-45b9-8034-63c5d0e7de0d" TYPE="ext4" PARTUUID="0001f779-01"


/dev/sdc1: LABEL="Grsync" UUID="86ac87af-c9a2-4f3a-bdfa-99d6fdd9fd26" TYPE="ext4" PARTUUID="5e9ccc05-01"
/dev/sdc2: LABEL="IMG-sda" UUID="7699bb21-cd70-405a-a64a-ac8b6bc9278a" TYPE="ext4" PARTUUID="5e9ccc05-02"
/dev/sdc3: LABEL="IMG-sda1" UUID="3ba37c5a-ef52-4e9f-8143-9f6b7f180998" TYPE="ext4" PARTUUID="5e9ccc05-03"
/dev/sdc5: LABEL="1604o/s" UUID="871a0f8f-65be-4a85-bfca-16a1616e7fcb" TYPE="ext4" PARTUUID="5e9ccc05-05"
/dev/sdc6: UUID="773c1ae7-7f43-428e-bd7e-c2d64c969102" TYPE="swap" PARTUUID="5e9ccc05-06"
/dev/sdc7: LABEL="/home" UUID="24310085-a25e-45bf-a6ee-98555fadbb75" TYPE="ext4" PARTUUID="5e9ccc05-07"
```

xxx Thanks

---

### Post by again? on 2017-05-15
May also be helpful to post the contents of your **/etc/fstab** file.

Use code tags to wrap pasted in text. [noparse]```
[/noparse]**Your pasted info**[noparse]
```[/noparse].
Highlight your pasted info with left mouse then hit the code button (#)
So it looks like.
```
**Your pasted info**
```

You can use disks to automount a partition. Search disks in the dash.
Disks will create an fstab entry instead of you manually having to do it.
[https://askubuntu.com/questions/783061/automount-in-16-04](https://askubuntu.com/questions/783061/automount-in-16-04)
[http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/)

Pic of my ext4 "Data" mount in disks.
[ATTACH=CONFIG]275121[/ATTACH]

---

### Post by ajgreeny on 2017-05-15
OK. 
I am sure that would work but I have never used **disks** to make such changes and prefer to do it manually; it also should give you a far better understanding of what is happening, and has been done.

First create a mountpoint for the partition; I suggest /mnt/Movies but you can call it whatever you want but avoid spaces in file and folder names for ease of use, and change the owner of the partition to you as user.
```
sudo mkdir /mnt/Movies
sudo chown -R $USER;$USER /mnt/Movies
```
Now with command ```
sudo -H gedit /etc/fstab
```add a couple of lines to fstab 
```
#sdb1 Movies added manually on (date)
UUID=25bb9f4d-7f2c-45b9-8034-63c5d0e7de0d /mnt/Movies ext4 defaults 0 2
```and save it.
Finally unmount the partition if it already mounted and run command ```
sudo mount -a
```to test the change.
If there is no output from that command the partition has mounted successfully and should do so from now on at every boot.

---

### Post by oldfred on 2017-05-15
I would also suggest not using spaces with anything you create with Linux, labels, folders, etc. You movie name may still end up with the spaces, but best to avoid spaces where possible.
If you want longer names use CamelCase, under_score or onelongname.

---

