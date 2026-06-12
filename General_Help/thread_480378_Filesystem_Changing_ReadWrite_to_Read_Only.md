---
title: "Filesystem Changing Read/Write to Read Only"
date: 2007-06-21
forum: General Help
---

### Post by psychomonkey on 2007-06-21
Hello,

I've recently started having this problem with Filesystem Access. 

I have a small home server running 5.10 which I used to store files (mp3's, movies, etc). I have 2 drives set up as RAID 1 which I mount locally on the server in a** /download/e** folder. I use Samba to share these files between a Windows XP laptop and a Kubuntu 7.04 desktop. For the Kubuntu desktop, I use 

```
sudo mount -t smbfs //10.0.0.10/e /mnt
```

to mount it so I can listen to music and move files back and forth. I has been working fine for awhile, but recently it seems that the share will still be accessable, but I won't be able to move files or delete any files.
I get the error "Access Denied". My only guess is that the drive changes from read/write to read only access. If I unmount the share on the server end from the** /download/e** folder and then remount it, it will work, but there must be some reason why this started happening.

Any assitance would be greatly appreciated.

---

### Post by DugieHowsa on 2007-06-27
From some recent research myself and lots of help from the good people on this forum, I have found that cifs is a much better alternative to smbfs when it comes to mounting Windows shares.  The following post serves as an excellent guide line for configuring cifs shares:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

From your code entry, it doesn't appear that you are too concerned with user authentication.  You also may not want to mount the root of the /mnt folder to the share, as that is a common place for other filesystems to mount.

Try out the following snippet and see if this gives you what you want:

Code:

sudo mkdir /mnt/download
sudo mount -t cifs //10.0.0.10/e /mnt/download -o guest,rw,noperm,file_mode=0777,dir_mode=0777

---

### Post by psychomonkey on 2007-06-29
I thank you for the reply. I seem to have some additional information that sheds some new light on the problem.

On the my home server, which is running Ubuntu 5.10, I have 1 80G IDE drive that the O/S is running on and I have 2 drives set up as RAID 1 which I mount locally on the server in a /download/e folder. When I try to copy a file from the 80G drive (a text file for example) to the mounted RAID (such as /downloads/e/folder 1), I get the error "Read Only Filesystem". It appears that the issues is not with using Sambe to mount the share over a network, but just mounting the drive locally. What's odd is if I unmount it, wait for a period of time, then remount the drive, it will work fine. After an undetermined time (1-2 days), I will start to experience the issue again and have to repeat the mount/unmount funtion. 

Can anyone tell me where I might be able to look to see what the issue might be?

---

