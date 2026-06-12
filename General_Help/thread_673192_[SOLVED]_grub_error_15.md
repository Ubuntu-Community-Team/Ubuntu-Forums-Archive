---
title: "[SOLVED] grub error 15"
date: 2008-01-20
forum: General Help
---

### Post by rob1984 on 2008-01-20
HELP!

I keep getting  "error 15: file not found" after choosing ubuntu in grub.

i think it might be because ive just changed my upsplash and done something wrong.  

can anyone help?  i'm not sure what file its referring to.  i have the live cd so is there a way to boot that and fix the problem, or will i have to use it to copy my files to an external drive and format?

cheers

---

### Post by Shazaam on 2008-01-20
Good site for grub error codes....

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by rob1984 on 2008-01-20
thats great but i cant fix the /boot/grub without booting ubuntu, which i cant do.

linux is still pretty new to me, so i really need things spelled out to me at the moment.

if you cold do that it would be great.

---

### Post by capink on 2008-01-20
Try updating menu.lst using the livecd

1. Boot form live cd.
2. Mount your root partition on any mount point you want. I will use /mnt here.

```
sudo mount -t [COLOR="#ff00ff"]ext3[/COLOR] [COLOR="Magenta"]/dev/sdXY[/COLOR] /mnt
```


Replace [COLOR="#ff00ff"]ext3[/COLOR] with your partition type and [COLOR="#ff00ff"]/dev/sdXY[/COLOR] with the device name of your root partition.

3. Chroot into your installation

```
sudo mount -o bind /dev /mnt/dev
```
```
sudo moutn -o bind /proc /mnt/proc
```
```
sudo chroot /mnt
```

While still in chroot, update your menu.lst after backing up the old one:

```
mv -v /boot/grub/menu.lst{,_bak}
```

to update menu.lst run:

```
update-grub
```

If it asks you if you want to create a new menu.lst file, answer yes and press enter.

Check that the new menu.lst is created:

```
ls /boot/grub
```

Exit chroot:

```
exit
```

4. Restart you pc.

---

### Post by rob1984 on 2008-01-21
great!  i'll try that out tonight as soon as i get home from work and let you know how i get on.

cheers!

---

### Post by c0met on 2008-01-21
On the Hermanzone site, you can also find a little program called SuperGRUB. Download the ISO of this and burn to a disk so that you can boot from it. I have often used this to restore GRUB. It mostly works (not 100% of the time, though). It's very easy use and doesn't involve code. Then SuperGRUB doesn't work, that's when I get into the code.

SuperGRUB is at...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

At worst, SuperGRUB should allow you to boot into Ubuntu and you can edit the menu.lst from there.  If you need extra information on GRUB, about 1/3 of the way down the below webpage is a guide to reinstalling the program.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by rob1984 on 2008-01-21
thanks! thats great too.

i think ill try the code first because, like i said i'm new to linux and i'd like to learn all this stuff.

i'll definitely download the program and check it out too!

thanks again

---

### Post by rob1984 on 2008-01-21
the code worked a treat (after supergrub reminded me that my partition was ext2 not ext3.)

i got a new problem now though.

"kernel panic - not syncing: VFS: unable to mount root fs on unknown block"

either of you guys know what this means?  i'm assuming that if my kernel is broken then its gunna be a re-install job?

---

### Post by c0met on 2008-01-21
Sorry Rob,

I'm a relatively new user myself and I haven't had that problem, yet. One of the reasons that I have a separate /home partition is because I have learned that it's if you ever need to reinstall, /home is kept intact if it's on a separate partition.

---

### Post by capink on 2008-01-21
I am not sure this is going to work, try it anyway:

Chroot into you system from the live cd as in the previous post, only this time change the command:

```
sudo chroot /mnt
```

with

```
LANG= sudo chroot /mnt
```


While in chroot find out the version number of your kernel by typing:

```
ls /boot
```

the ouput should conatain one file looking like this:

> vmlinuz-[COLOR="Magenta"]version-number[/COLOR]

Now perform the following command in chroot:

```
dpkg-reconfigure linux-image-[COLOR="Magenta"]version-number[/COLOR]
```

Replacing [COLOR="Magenta"]version-number[/COLOR] with your kernel version number.

If that did not work try reinstalling the kernel.

---

### Post by rob1984 on 2008-01-22
cheers capink, i'll give that a try and if it doesnt work, i'll just format and start from scratch.

if i do, i will definitely put /home on a seperate partition.

can either of you guys suggest a good size for my / partition?

---

### Post by capink on 2008-01-22
My / partition is 10 GB and it is more than enough for me. My /home partition is 3 GB, and again it is enough for me as I use it only for user settings. 

I store all my personal files and data on FAT32 partition, this gives me two advantages:

1. Can access form both linux and windows out of box.
2. On linux, I mount FAT32 partition with the options: (defaults,utf8,umask=007,gid=[COLOR="#2e8b57"]1002[/COLOR])

So any user can access the data on the partition as long as he is member of the group I created  called home ( this group id is [COLOR="SeaGreen"]1002[/COLOR] ). This means that if userX downloaded a file it can be viewed immediately by userY without needing to change permissions, provided that both users are members of the group home.

I don't have Gutsy as I am using Debian now, But I think it can read and write NTFS out of box. So you can use NTFS instead of FAT32 if you want.

---

### Post by c0met on 2008-01-22
Have 3 partions.

/ is 28 gigs (ext3)

/swap is 2 gigs

/home is just under 50 gigs (ext3)

I chose to have a relatively large / because I like installing lots of software. Gutsy 7.10 reads and writes comfortably on NTFS so I can still use my Windows drives if need be. I originally had a FAT 32 parition. i discovered it was not the most efficient at storing files. That didn't really bother me, but I also found out that it had a maximum file size (for a single file) of 4 gigs. This was no good because it would have meant that I could not have burnt DVD ISO's to disk.

---

### Post by hangfire on 2008-01-22
See

[http://ubuntuforums.org/showthread.php?t=644773](http://ubuntuforums.org/showthread.php?t=644773)

Unfortunately, on ubuntuforums.org, searching for "grub error 15" returns no threads, even though there have been many on the subject.

-HF

---

### Post by rob1984 on 2008-01-22
yey! it worked.

thanks capink! you truly are the code king!

---

