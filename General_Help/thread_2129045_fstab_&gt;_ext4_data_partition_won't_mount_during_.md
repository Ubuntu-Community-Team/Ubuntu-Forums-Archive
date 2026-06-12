---
title: "fstab &gt; ext4 data partition won't mount during boot"
date: 2013-03-25
forum: General Help
---

### Post by Tom C on 2013-03-25
I have several distros set up on my desktop PC, so I use a separate ext4 partition labelled Data so I can save and access files across distros. In each distro, I have created a directory under my Home directory (/home/tom/Data), which I use as the mount point for this. This works with no problems when I mount the partition manually from bash:

```

sudo mount /dev/sda12 ~/Data
```

Being a lazy sort, however, I want the partition to mount automatically on bootup. I've edited my fstab file to try to do this, but the directory /home/tom/Data still appears as empty when I boot into Ubuntu (or any distro) until I manually mount the partition.

I've tried various things. Following advice in other threads, I edited fstab manually, adding the line:

```
/dev/sda12 /home/tom/Data ext4 defaults,user 0 0
```

I understand that the options **defaults** and **user** should do what I'm after, and I made sure that fstab ended with a return. 

When this didn't work after repeated reboots and checking the file, I tried again using the Mount Manager GUI to help me edit fstab. My fstab for Ubuntu now looks like this:

```
UUID=**106761fa-49e3-40a0-a30c-b5940b32bdd9** /home/tom/Data ext4 defaults,user 0 0
UUID=d7be7924-909c-4f19-ba74-326e74a69112 / ext4 defaults 0 0
```

As you can see, the GUI has replaced the reference to the partition with its UUID, which I have confirmed is correct by running **blkid**:

```

/dev/sda1: LABEL="SYSTEM RESERVED" UUID="46748DDD748DD05B" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="94D28F74D28F58FE" TYPE="ntfs" 
/dev/sda4: LABEL="Windows 8 RP" UUID="642B628E16F1E88A" TYPE="ntfs" 
/dev/sda6: LABEL="Ubuntu" UUID="d7be7924-909c-4f19-ba74-326e74a69112" TYPE="ext4" 
/dev/sda7: LABEL="Fedora /boot" UUID="c7747221-b553-4049-97fa-b9172d8258e5" TYPE="ext4" 
/dev/sda8: LABEL="Fedora ?" UUID="60a823b5-1d44UUID="106761fa-49e3-40a0-a30c-b5940b32bdd9"-4bbb-9e4e-99f4f155afe8" TYPE="ext4" 
/dev/sda9: LABEL="_Fedora-17-x86_6" UUID="8e5efc8a-3958-49e2-8f31-0f6bd21f1b30" TYPE="ext4" 
/dev/sda10: LABEL="LFS" UUID="1753758c-6573-4945-b238-6610c74b5238" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Debian" UUID="f62609ea-c363-4ba2-943c-b5a888fa8e0b" TYPE="ext4" 
/dev/sda12: LABEL="Data" **UUID="106761fa-49e3-40a0-a30c-b5940b32bdd9"** TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="a2e447ae-ada6-4ce9-b8a6-5fd16bb124d0" TYPE="swap" 

```

All of the threads I've found about this sort of issue are specific to problems mounting NTFS partitions. The reslutions to these are to do with Samba credentials, so don't apply in this case. It seems that what I'm trying to do *should* be quite simple. Is there some other config I need to change to permit fstab to execute at boot time or something like that?

Any ideas gratefully received!

Tom

---

### Post by Morbius1 on 2013-03-25
You might want to run blkid this way:
```
sudo blkid -c /dev/null
```
Then see if you still get this rather odd listing which also contains the UUID number of your /sda12 partition:
> 
/dev/sda8: LABEL="Fedora ?" UUID="60a823b5-1d44[COLOR=#0000cd]**UUID="106761fa-49e3-40a0-a30c-b5940b32bdd9"**[/COLOR]-4bbb-9e4e-99f4f155afe8" TYPE="ext4" 

---

### Post by Cheesemill on 2013-03-25
You aren't using an encrypted home directory by any chance are you?

---

### Post by Tom C on 2013-03-25
Thanks for taking the time to have a look at this guys.

Morbius1 - The error was with my copy and pasting rather than the original output from blkid.

Cheesemill - Thanks for pointing me in the right direction. My home partition *is *encrypted, and of course it can't be mounted at boot as it doesn't get decryped until login. 

I've now got this working by:

1. Adding a new directory outside of home as the mount point (/mnt/Data), and editing the line in my fstab like so:

```
UUID=106761fa-49e3-40a0-a30c-b5940b32bdd9 /mnt/Data ext4 defaults,user 0 0
```

2. Removing the mount point from my home directory and replacing it with a symlink to the new mount point.

I've just rebooted and could access my files via my new symlink without needing to mount manually.

Thanks for your help guys - much appreciated!

---

