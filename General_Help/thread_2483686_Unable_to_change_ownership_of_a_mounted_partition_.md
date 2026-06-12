---
title: "Unable to change ownership of a mounted partition from 'root' to admin 'user'"
date: 2023-02-06
forum: General Help
---

### Post by xanizen on 2023-02-06
The partition in question is unencrypted and was created with Windows 7 to NTFS format.

While installing Ubuntu I designated the partition to the mount point of /sdd1. 

I can manually copy and paste files to it, but application installed through Snap like SMPlayer and OnlyOffice are unable to save files (screenshots) or open documents from that location.

I tried to use the following to change the permission, but it would still display the owner as root or plugdev
```
sudo chown -R vhen:vhen /sdd1
```

I also tried to do it from the gui with 'sudo nautilus', and the drop down menu in the 'Permissions tab' would change back from my username to root.

This is the output of ls-l
```

vhen@vhen-az80:/sdd1$ ls -l
total 40
drwxrwx--- 1 root plugdev     0 Aug 19  2021 '$RECYCLE.BIN'
drwxrwx--- 1 root plugdev     0 Oct  5 23:56  Audio
drwxrwx--- 1 root plugdev  4096 Feb  4 18:52  Downloads
drwxrwx--- 1 root plugdev 12288 Jan  4 12:35 Documents
drwxrwx--- 1 root plugdev 12288 Dec 30 17:21  Software
drwxrwx--- 1 root plugdev     0 Aug 19  2021 'System Volume Information'
drwxrwx--- 1 root plugdev 12288 Aug 19  2021  Videos

```

I followed the suggestion of this '[Stack Exchange]("https://superuser.com/a/657978")' post, and unmounted the drive, before setting the permissions. plugdev no longer appears, instead root is in its place.
```

vhen@vhen-az80:~$ ls -l /sdd1/
total 40
drwxrwxrwx 1 root root     0 Aug 19  2021 '$RECYCLE.BIN'
drwxrwxrwx 1 root root     0 Oct  5 23:56  Audio
drwxrwxrwx 1 root root  4096 Feb  4 18:52  Downloads
drwxrwxrwx 1 root root 12288 Jan  4 12:35 Documents
drwxrwxrwx 1 root root 12288 Dec 30 17:21  Software
drwxrwxrwx 1 root root     0 Aug 19  2021 'System Volume Information'
drwxrwxrwx 1 root root 12288 Aug 19  2021  Videos

```

This is the output of lsblk. I physically removed a drive from the system, hence why sdd is now sdc.
```

sda              8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1           8:1    0   285M  0 part /boot/efi
&#9500;&#9472;sda2           8:2    0 137.3G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                        /
&#9492;&#9472;sda3           8:3    0   7.6G  0 part [SWAP]
sdb              8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1           8:17   0 931.5G  0 part 
  &#9492;&#9472;veracrypt3 253:2    0 931.5G  0 dm   /media/veracrypt3
sdc              8:32   0 931.5G  0 disk 
&#9500;&#9472;sdc1           8:33   0 439.5G  0 part /sdd1
&#9492;&#9472;sdc2           8:34   0 492.1G  0 part 
  &#9492;&#9472;veracrypt1 253:0    0 492.1G  0 dm   /media/veracrypt1
sdd              8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1           8:49   0   1.8T  0 part 
  &#9492;&#9472;veracrypt2 253:1    0   1.8T  0 dm   /media/veracrypt2
sde              8:64   0 238.5G  0 disk 
&#9492;&#9472;sde1           8:65   0   128G  0 part 
  &#9492;&#9472;veracrypt4 253:3    0   128G  0 dm   /media/veracrypt4
sdf              8:80   1  57.8G  0 disk 
&#9492;&#9472;sdf1           8:81   1  57.8G  0 part /media/vhen/Xfer USB

```

---

### Post by ne29914 on 2023-02-06
AFAIK, NTFS does not support rights/ownership like Linux filesystems. You'll probably need to change to ext4 to get this to work.

---

### Post by xanizen on 2023-02-06
I followed the instruction here, and managed to get change the ownership to myself instead of root. Unfotunately said/specific/individual program installed with Snap refuses to save file to that partition (SMPlayer) or recognize the partition at all (OnlyOffice).

[https://askubuntu.com/a/1111551/834778](https://askubuntu.com/a/1111551/834778)

```

sudo mount -o rw,user,uid=1000,dmask=007,fmask=117 /dev/sdxn /mnt/sd1  # general syntax
sudo mount -o rw,user,uid=1000,dmask=007,fmask=117 /dev/sdb1 /mnt/sd1  # modify to
```

So yeah, this 'solution' may be a 'placebo' for all we know.

---

### Post by coffeecat on 2023-02-06
Of course it isn't a "placebo". You are encountering two entirely and different issues that you have conflated.

First, as ne29914 says, NTFS, a Microsoft filesystem, doesn't support Linux permissions and ownership. You have assigned yourself ownership by means of mount options. A perfectly reasonable strategy when dealing with NTFS - hardly a placebo.

Second - the app you are having difficulty with is a snap. By default snaps can only access your home folder. If you want a snap app to access a filesystem outside of your home and mounted to /mnt, you will have to do some configuration. Here's a link that will start you off: [https://askubuntu.com/questions/1228899/how-to-access-files-outside-of-home-in-snap-apps](https://askubuntu.com/questions/1228899/how-to-access-files-outside-of-home-in-snap-apps)

---

