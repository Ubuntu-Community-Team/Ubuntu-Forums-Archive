---
title: "Oh no!!"
date: 2007-08-03
forum: General Help
---

### Post by joshier on 2007-08-03
Hello

Wubi was totally fine up until very recently. I booted into it, and it gets about 1/12th of the way into the loading bar, then stops.

I would happily reinstall it and that;s that, but the partition (loopmount) how ti works I am unable to access it :(

Thing is, I cannot just re-install it because I have important files within the loopmount partition file.

I can boot into wnidows fine like I am now, but is there any way I am able to mount the partition virtually.. or even use the live ubuntu cd or anything?


Thanks

---

### Post by bernied on 2007-08-03
I'm not a wubi user, but the name of the file makes me think that you need to do something like:

- get a linux live-cd (like ubuntu)
- open a terminal as root user ('sudo su' in ubuntu live-cd)
- create a mountpoint
```
mkdir /mnt/wubitemp
```
- find the loopmount file, to do this you need to mount the windows filesystem. Your live cd might do this for you, if you can click on a desktop icon and get access to the files then you just need to find out where ubuntu has put them. Try:
```
mount
```(this should give you a list of mounted filesystems and where they are mounted, one of them should be the windows partition, it is probably /dev/hda1 or /dev/sda1)

- navigate to the loopmount file using cd (change directory) and ls
- mount the file as a filesystem
```
mount -o loop loopmount /mnt/wubitemp
```
- go to the mountpoint and see if your files are there
```
cd /mnt/wubitemp
ls
```
- copy the important files to somewhere safe (cd-rom, flash stick, etc)

I hope this helps. If things don't work, post all of the output from what you tried above here.

---

### Post by joshier on 2007-08-03
Awesome reply.. although I was unable to 'mount -o loop loopmount /mnt/wubitemp' because it said it did not exist.. - I wasn't sure where to put the 'home.virtual.disk' within the command.

Anyway, got onto windows and I'm now copying all of the disk images.

Thanks again for your help. (this should be stickier or put in the help file)

---

### Post by bernied on 2007-08-03
Just replace the word loopmount with the name of the file. You were talking about the loopmount file, so I thought that was its name. I don't know wubi, so not really sure how it works, but figured this would just be a filesystem within a file, just like a cd .iso file, so this command might work.

---

### Post by tuxcantfly on 2007-08-03
> Awesome reply.. although I was unable to 'mount -o loop loopmount /mnt/wubitemp' because it said it did not exist.. - I wasn't sure where to put the 'home.virtual.disk' within the command.

Boot the livecd and create mountpoints:

```
sudo mkdir /media/windows
sudo mkdir /media/wubi
```

With the livecd's kernel-based ntfs driver, you'll only be able to get read-only access, so I'd suggest installing ntfs-3g (you'll need a ubuntu 7.04 livecd to do this, though, the earlier versions don't have ntfs-3g in the repos):

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

Then, assuming that your Windows drive is /dev/sda1 (adjust line accordingly, you can use sudo fdisk -l to find it out; see whichever one says HPFS/NTFS on the type line):

```
sudo ntfs-3g /dev/sda1 /media/windows
sudo mount -o loop /media/windows/wubi/disks/system.virtual.disk /media/wubi
sudo mount -o loop /media/windows/wubi/disks/home.virtual.disk /media/wubi/home
```

Now you'll be able to access your wubi filesystem in /media/wubi read-write; your home dir will be in /media/wubi/home, and /media/wubi for the wubi root filesystem. You'll probably need to have root access to modify some files, so to open the filemanger with root privs:

```
gksudo nautilus /media/wubi
```

Optionally, if you need to do something like an apt-get to fix something, you can chroot in:

```
sudo chroot /media/wubi
```

And just run the commands you need to repair your install from there

---

### Post by tuxcantfly on 2007-08-03
> this should be stickier or put in the help file

I've added it to the WubiGuide at [https://wiki.ubuntu.com/WubiGuide?action=show#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide?action=show#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

---

