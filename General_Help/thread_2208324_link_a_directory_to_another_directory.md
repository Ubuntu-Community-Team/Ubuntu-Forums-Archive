---
title: "link a directory to another directory?"
date: 2014-02-27
forum: General Help
---

### Post by sdowney717 on 2014-02-27
I have a directory at

/media/scott/0C3655E6635050E4/movies  

I would like the files to show at 
/mnt/vhs movies 

How can I do this exactly?

---

### Post by Dave_L on 2014-02-27
Create a symbolic link (symlink):

```
sudo ln -s /media/scott/0C3655E6635050E4/movies /mnt/'vhs movies'
```

Reference: [http://manpages.ubuntu.com/manpages/precise/en/man1/ln.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/ln.1.html)

---

### Post by sdowney717 on 2014-02-27
Thanks, that works, but is there a way for it to show up directly in the folder with all the names.
This way you click and it says 'movies' with an arrow.

Anyway the idea is to create a link for mythtv to follow.
I will test it out with mythtv.

---

### Post by sdowney717 on 2014-02-27
kinda interesting, but not what I was hoping
click vhs movies and it shows a screen of 101 dalmations.
click again and it shows all the vhs movies

I was hoping one click to take straight to vhs movies

---

### Post by sdowney717 on 2014-02-27
I rebooted and the got an error saying could not mount the drive.

Now I have a 'dead link'

What to do?

link cant survive a boot.
This drive is an ntfs drive attached to my computer.

I was able to make the link work by clicking in nautilus and then the drive gets mounted.
hmm, maybe the drive should be setup in fstab and forget about linking.

Can I mount the drive in fstab, then

Can I mount the movie folder from that drive at /mnt/vhs movies?

---

### Post by Dave_L on 2014-02-27
With the drive mounted, use the "mount" command without parameters, or look at /etc/mtab, to see the mount parameters for the drive.  Then use that information to add a line to /etc/fstab for mounting the drive automatically at the desired mount point (/mnt/vhs_movies).

---

### Post by sdowney717 on 2014-02-27
```
/dev/sda1 on /media/scott/0C3655E6635050E4 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

Thing is there are 10 folders there and I am only interested in linking the 'movies' folder to use with mythtv

If I mount to /mnt/vhs movies, mythtv will see all that stuff.

I think should mount in fstab to someplace, then do the link you sent me to /mnt/vhs movies

---

### Post by sdowney717 on 2014-02-27
```
/dev/sda1 /media/scott/500gbNTFS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

for some reason mount does not like this

it does like this, I thought to change a little to see what it would do
> /dev/sda1 /media/scott/0C3655E6635050E4 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

---

### Post by Dave_L on 2014-02-27
You can't place that line directly into /etc/fstab. You have to use it as a reference for making a properly formatted entry in /etc/fstab.

See [http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/fstab.5.html) for the details.

---

### Post by sdowney717 on 2014-02-27
Interesting I wrecked the old mount point, 

this no longer works
/dev/sda1 /media/scott/0C3655E6635050E4 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

now it is this
/dev/sda1 /media/scott/0C3655E6635050E41 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

so of course the original link is dead.

---

### Post by sdowney717 on 2014-02-27
deleted old link and added a 1 to the name location and link works again

```
sudo ln -s /media/scott/0C3655E6635050E41/movies /mnt/'vhs movies'
```


what exactly is this string?
0C3655E6635050E41

---

### Post by sdowney717 on 2014-02-27
my /media/scott folder now has 2 additional items.

Can I just delete those two?

0C3655E6635050E4 -- original 500gb designation
500gbNTFS -- from when I made a defective entry

---

### Post by steeldriver on 2014-02-27
You could use a *bind mount* in your fstab - however you'd probably need to also mount the whole drive in fstab as well (rather than relying on the udisks/fuse automount under /media, which may not be present until after boot time) - something like

```

# mount external drive
/dev/sda1    /storage    ext4    defaults    0    2

# bind mount VHS movies subdir
/storage/movies    /mnt/vhs\040movies    none    bind    0    0

```


For reference, here's a similar setup that I use for my mythtv setup (except it has an internal RAID volume instead of an external drive, and I bind it direct to mythtv's default storage location at /var/lib/mythtv)

```

# added RAID1 LV for mythtv media storage
/dev/mapper/vg0-lv0     /storage/mythtv xfs defaults,noatime,allocsize=512m,logbufs=8 0 2

# bind mount the mythtv storage volume
/storage/mythtv         /var/lib/mythtv none    bind    0       0

```

---

### Post by sdowney717 on 2014-02-28
so bind mount would get rid of need for the link

and then the vhs movies would directly appear at /mnt/vhs movies?

can i mount the ntfs drive in fstab with

/dev/sda1 /media/scott/0C3655E6635050E41 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

then do a bind mount with

# bind mount VHS movies subdir
/media/scott/0C3655E6635050E41/movies     /mnt/vhs\040movies    none    bind    0    0

or some other parameters, you mentioned fuse earlier

---

### Post by steeldriver on 2014-02-28
If it's an ntfs drive you'd mount it in /etc/fstab like

```

UUID=0C3655E6635050E41    /storage    ntfs    defaults,nofail 0 0

```

where the mount point /storage is arbitrary - although I'd suggest not using a location like /media/scott/xxxx because (as you've observed) that's the location that the 'fuse' system uses to mount removable media for non-privileged users.

---

