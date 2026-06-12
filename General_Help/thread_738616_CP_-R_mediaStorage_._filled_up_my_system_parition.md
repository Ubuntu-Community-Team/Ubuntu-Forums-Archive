---
title: "CP -R /media/Storage ./ filled up my system parition"
date: 2008-03-28
forum: General Help
---

### Post by DaveTheAve on 2008-03-28
When in /media/Nupot I entered the command:

sudo cp -R /media/Storage ./

and then my system partition completely filled up. (User accounts are also included in the system partition.)

Any thoughts on how to fix this?

---

### Post by init1 on 2008-03-28
Is there a reason why you can't just delete it with rm? I don't quite understand the issue.

---

### Post by mvan83 on 2008-03-29
Copy here the output of 
```
df -h
```

---

### Post by DaveTheAve on 2008-03-29
```

david@devlon:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              28G   28G  235M 100% /
varrun                503M  256K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
procbususb            503M  120K  503M   1% /proc/bus/usb
udev                  503M  120K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   14M  490M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb4              27G   22G  4.7G  83% /media/Vista_x32
/dev/sdb1              16G  2.1G   14G  14% /media/WinXPx64
/dev/sda1             466G  290G  177G  63% /media/Storage
/dev/sdd1             466G  303G  163G  66% /media/Nupot

```

And the reason i'm asking is because when I ran the command it was to copy to a different hard drive yet it filled up my system partition, not the other hard drive and I can't figure out where the files are on the system partition to delete them and gain back my space.

edit: and incase your wondering... I have 5 hard drives, 10 partitions and three of them are AES encrypted with SHA256 and mounted via dm-crypt.

---

### Post by mvan83 on 2008-03-29
> **DaveTheAve said:**
> ```

david@devlon:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              28G   28G  235M 100% /
varrun                503M  256K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
procbususb            503M  120K  503M   1% /proc/bus/usb
udev                  503M  120K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   14M  490M   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb4              27G   22G  4.7G  83% /media/Vista_x32
/dev/sdb1              16G  2.1G   14G  14% /media/WinXPx64
/dev/sda1             466G  290G  177G  63% /media/Storage
/dev/sdd1             466G  303G  163G  66% /media/Nupot

```

And the reason i'm asking is because when I ran the command it was to copy to a different hard drive yet it filled up my system partition, not the other hard drive and I can't figure out where the files are on the system partition to delete them and gain back my space.

edit: and incase your wondering... I have 5 hard drives, 10 partitions and three of them are AES encrypted with SHA256 and mounted via dm-crypt.
Ok, well obviously your root partition is basically full. Are you sure you typed:
```
sudo cp -R /media/Storage ./
```
and not:
```
sudo cp -R /media/Storage /
```
?
If not, are you sure you were in the directory /media/Nupot when you ran that command?

Should your root partition be taking up 28GB? If you usually don't keep many large files on there, you probably accidentally copied large files to that partition. You can see which directory on / contains large amounts of data by running:
```
sudo du -chs --exclude=/dev --exclude=/proc --exclude=/media /*
```
Here's what that gives me on my system:
```

4.7M    /bin
18M     /boot
0       /cdrom
12M     /etc
25G     /home
4.0K    /initrd
0       /initrd.img
163M    /lib
16K     /lost+found
8.0K    /media
4.0K    /mnt
4.0K    /opt
8.4M    /root
6.3M    /sbin
4.0K    /srv
4.0K    /storage
0       /sys
360K    /tmp
2.7G    /usr
158G    /var
0       /vmlinuz
185G    total

```
If I didn't expect /var to be taking up 158GB, I would know I need to investigate that directory further. I would cd into that directory and then run du -chs * and it will show me how much space each subdirectory is using.

Hope this helps.

---

### Post by DaveTheAve on 2008-03-29
This is what doesn't make sense...

```

5.9M    /bin
18M     /boot
0       /cdrom
11M     /etc
15G     /home
0       /initrd
0       /initrd.img
165M    /lib
3.1M    /lib32
0       /lib64
0       /mnt
206M    /opt
422K    /root
7.5M    /sbin
0       /srv
0       /sys
69K     /tmp
3.7G    /usr
1.1G    /var
0       /vmlinuz
20G     total

```

But this partition is 30gig and all that seems hunky-dory.

---

### Post by mvan83 on 2008-03-29
Do you have other directories in /media besides the mountpoints that show up in df? And if so, do they have anything in them?

---

### Post by DaveTheAve on 2008-03-29
Yes:
```

david@devlon:/media$ ls -A
cdrom   .directory  floppy   .hal-mtab       .hidden   Nupot    Vista_x32
cdrom0  encrypted   floppy0  .hal-mtab-lock  isoImage  Storage  WinXPx64

```

i'm doing your sudo du -chs to them now but there is over 1TB of hard drives to scan.

---

### Post by mvan83 on 2008-03-29
> **DaveTheAve said:**
> Yes:
```

david@devlon:/media$ ls -A
cdrom   .directory  floppy   .hal-mtab       .hidden   Nupot    Vista_x32
cdrom0  encrypted   floppy0  .hal-mtab-lock  isoImage  Storage  WinXPx64

```

i'm doing your sudo du -chs to them now but there is over 1TB of hard drives to scan.

Use the --exclude option to skip over Nupot, Storage, Vista_x32, and WinXPx64. We don't care about those, and like you said, it will take a LONG time to scan over them :)

---

### Post by DaveTheAve on 2008-03-29
```

david@devlon:~$ sudo du -chs /media/*
0       /media/cdrom
0       /media/cdrom0
70G     /media/encrypted
0       /media/floppy
0       /media/floppy0
0       /media/isoImage
302G    /media/Nupot
289G    /media/Storage
22G     /media/Vista_x32
2.0G    /media/WinXPx64
683G    total

```

See what I mean... This isn't making any sense but my 30gig system partition is full when it says it has 20gig in use.

---

### Post by mvan83 on 2008-03-29
That's very strange. What disk is /media/encrypted on? It says it's taking up 70GB, but it can't possibly do that and be on your root partition.

---

### Post by DaveTheAve on 2008-03-29
encrypted is a 300gig ATA. my root parition is on a 80gig SATA.

I have two 500 SATA, two 80 SATA and one 300 ATA.

---

### Post by DaveTheAve on 2008-04-05
Any ideas?

---

