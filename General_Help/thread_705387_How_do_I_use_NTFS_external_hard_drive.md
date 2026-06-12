---
title: "How do I use NTFS external hard drive?"
date: 2008-02-23
forum: General Help
---

### Post by the lemming on 2008-02-23
Hello

I have an external USB hard drive which I would like to use and transfer some data off and onto my Ubunto desktop.

I have downloaded the NTFS config tool along with anything else that I could find relating to NTFS and I also ran the NTFS config tool but I still can't mount the Hard Drive.

Any help or advice would be most appreciated.

Cheers

---

### Post by taurus on 2008-02-23
Assuming your external drive is /dev/sdb1, run

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
And if you need to unplug it, unmount it first with

```
sudo umount /media/sdb1
df -h
```

---

### Post by the lemming on 2008-02-23
Hello

I tried to follow your instructions as requested and I got the following response.

danny@danny-desktop:~$ sudo mkdir /media/sdb1
[sudo] password for danny:
danny@danny-desktop:~$ danny
bash: danny: command not found
danny@danny-desktop:~$ sudo mkdir /media/sdb1
[sudo] password for danny:
danny@danny-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0
danny@danny-desktop:~$ df -hsudo umount /media/sdb1
df: invalid option -- s
Try `df --help' for more information.
danny@danny-desktop:~$ df -hdf --help
df: invalid option -- d
Try `df --help' for more information.
danny@danny-desktop:~$ df  --help
Usage: df [OPTION]... [FILE]...
Show information about the file system on which each FILE resides,
or all file systems by default.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all             include dummy file systems
  -B, --block-size=SIZE use SIZE-byte blocks
  -h, --human-readable  print sizes in human readable format (e.g., 1K 234M 2G)
  -H, --si              likewise, but use powers of 1000 not 1024
  -i, --inodes          list inode information instead of block usage
  -k                    like --block-size=1K
  -l, --local           limit listing to local file systems
      --no-sync         do not invoke sync before getting usage info (default)
  -P, --portability     use the POSIX output format
      --sync            invoke sync before getting usage info
  -t, --type=TYPE       limit listing to file systems of type TYPE
  -T, --print-type      print file system type
  -x, --exclude-type=TYPE   limit listing to file systems not of type TYPE
  -v                    (ignored)
      --help     display this help and exit
      --version  output version information and exit

SIZE may be (or may be an integer optionally followed by) one of following:
kB 1000, K 1024, MB 1000*1000, M 1024*1024, and so on for G, T, P, E, Z, Y.

Report bugs to <bug-coreutils@gnu.org>.
danny@danny-desktop:~$ 








Have I done something wrong?

---

### Post by taurus on 2008-02-23
As you can see from the error message, you have a problem with your USB drive.  I guess the last time you used it in windows, you just unplugged it instead of unmounted it first before you unplug it.  So you have two options:

1.  Connect that harddrive to a windows machine and unmount or eject it first before you unplug it.

or

2.  You can use the force option to mount it under Ubuntu.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by ftwda on 2008-02-23
it should be force instead of option

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

(note that you should take the responsibility before using this option)

---

### Post by the lemming on 2008-02-23
Before I continue I do have a few questions.

It may help the situation if I explain that I have installed Ubuntu onto a free-bee computer donated by a friend and at the moment the only OS on it is Ubuntu which is the way it will stay seeing as I do not have a legit XP to put on it.

With this in mind, do I still need to plug the USB Hard Drive into an XP operating system before ejecting it?

And if I force the mount could I destroy all the data on the USB Hard drive?


I don't have much experience of Ubuntu because unfortunately it will not install onto my own PC which has meant that I have been using another distro (PClinuxOS).  In that distro I was shown how to mess around with the fstab file which allowed me to mount the NTFS drives.  I know that Ubuntu is different and as such I haven't tried anything apart from your suggestions in case I bugger up the system.

Cheers

---

### Post by taurus on 2008-02-23
Use the force option only if you must.  But using it every single time you want to mount your USB is not a good idea because sooner or later, your drive will be corrupted you won't be able to recover your files on it.  So, it's up to you if you want to find windows machine and safely unmount your drive first.  And even if you use it in Ubuntu, you still need to unmount it first before you unplug it.  Unplugging it without unmount it will cause problems later too.

---

### Post by the lemming on 2008-02-23
Its good to know that forcing the mount can damage the data on my drive because I use this drive for all my photos and music which means that I would cry if it got corrupted.

I'll boot into a windows OS and unmount the drive before popping it into UBuntu next.

Cheers

---

### Post by the lemming on 2008-02-24
> **taurus said:**
> As you can see from the error message, you have a problem with your USB drive.  I guess the last time you used it in windows, you just unplugged it instead of unmounted it first before you unplug it.  So you have two options:



```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```



As suggested I plugged my drive into XP and unmounted it, which I do with both of my Extermal drives, and this time it worked with ubuntu.

Thank you for all your help.

Cheers

---

