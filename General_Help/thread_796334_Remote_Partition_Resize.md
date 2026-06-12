---
title: "Remote Partition Resize"
date: 2008-05-16
forum: General Help
---

### Post by tobydeh on 2008-05-16
Hi Guys,

I have a web server with 1and1 and today i did a fresh install of 6.06 (which they support) and then upgraded to 8.04 (which they dont support)

For some reason my partitions look like this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             950M  391M  512M  44% /
varrun                2.0G   72K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   32K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/sda5             4.7G  570M  4.1G  12% /usr
/dev/sda6             4.7G  1.2G  3.6G  25% /var
/dev/sda7             361G  4.6M  361G   1% /home
none                  2.0G   36K  2.0G   1% /tmp
```

Why is all the space allocated to /home ?? i don't use home :(

Preferably i would like just two partitions "root" and swap.

How can i give some space to /var, /usr and / because it wont last long!

can someone please help me fix this?

Many thanks.

---

### Post by tobydeh on 2008-05-16
BUMP!!


Can someone PLEASE Help me this is seriously urgent.

---

### Post by jpietari on 2008-05-16
I don't know why you have so many partitions.  Have you tried using 'gparted' (apt-get install gparted) to change your partitions?

---

### Post by az on 2008-05-16
You can copy all the folders into your home partition and then turn it into "/".

Make sure you edit fstab as well as reconfigure the bootloader to look to sda7 for root instead of sda1.

Since you are not on site, this is risky if you make a mistake.  

Once you do that, forget about the other partitions.  You cannot resize mounted partitions anyway, so you wil not be able to grow the filesystem on sda7.

---

### Post by tobydeh on 2008-05-16
Hi az,

Could you give me an example / walkthrough of moving them all into one partition?

Is it possible to do this without loosing data?

What would happen to the configuration of things like apache / mysql?

How long would the server go down for whilst i did this?

Thanks for your help

---

### Post by tobydeh on 2008-05-19
bump

---

### Post by pallavis11 on 2008-05-19
See the info below:

[http://a2zhowto](http://a2zhowto) .blogspot.com/

[http://learnphpwithme](http://learnphpwithme) .blogspot.com/

---

### Post by tobydeh on 2008-05-19
Are you being serious? 

Those links bare no relation to this topic.

---

### Post by fyo on 2008-05-19
> **tobydeh said:**
> Could you give me an example / walkthrough of moving them all into one partition?

Is it possible to do this without loosing data?

GParted is a version of Parted with a GUI. It's much simpler to use than the textual interface, but I don't know what kind of access you have to your remote server.

GParted (and Parted) allows you to resize your partitions, without affecting the contents of the DESTINATION partition. It also allows you to MOVE partitions around on the disk, without affecting their contents.

In your case, you could fire up GParted, and mark e.g. the /home/ partition for deletion and then increase the size of a partition next to it (so if you wanted to increase your root partition, you would probably need to move things around first).

Specifically in your case, I would suggest COPYING your data to your root partition (including your apache install etc) and then deleting ALL your partitions except the root one... and then resizing your root partition to take up most of the space and then creating a new partition for swap.

The only problem is that you need to UNMOUNT all the partitions you are working on. On a local system, I would recommend just firing up a LiveCD install of Ubuntu (or another distro). I'm not sure what would be possible for your remotely.

> How long would the server go down for whilst i did this?

That depends on the disk size, speed and exactly what operations you need done. Think intelligently and plan ahead... so don't move a bunch of partitions that are just going to be deleted anyway, for example.

One last thing: If it's a new install of 8.04, you might want to consider just reinstalling. If you have all the files locally on your server, you should be able to do a fresh install pretty quickly.

---

### Post by tobydeh on 2008-05-19
i am fully aware of what gparted is.

which part of "Remote Partition Resize" did you have trouble understanding?

this is a live server and a very serious issue.

I just need someone to tell me how to merge all partitions into sda1

---

### Post by tobydeh on 2008-05-19
bump

---

### Post by tobydeh on 2008-05-19
once again a fantastic lack of help on the ubuntu forums.

---

### Post by fyo on 2008-05-19
> **tobydeh said:**
> once again a fantastic lack of help on the ubuntu forums.

I provided complete instructions. Copy your crap, run parted, delete partitions, resize remaining partition. You *will* have to unmount your primary partition at some point.

Maybe if you stopped acting like a 2-year-old and explained exactly what your problem was, you would get more (and better) answers.

---

### Post by tobydeh on 2008-05-20
The instructions you left were of no help to me what so ever.

I am not very familiar with linux and telling me to copy stuff and resize a partition doesn't really help.

---

### Post by russell.h on 2008-05-20
If you want to use GParted remotely, use the -X option with ssh:

ssh -X yourname@yourhost

Then you can run graphical programs remotely, assuming you have X installed locally (ie, on a Mac you will need the X11 package, on most Linux desktops you shouldn't need to do anything). So just type 'gparted', and you will be able to use the GUI as though you were sitting at your server (might need to 'aptitude install gparted' first, which might or might not require installing various dependencies including gtk).

---

### Post by tobydeh on 2008-05-20
Hi Russell

I tried the ssh -X but when i run gparted i get the following error:

(gparted:5814): Gtk-WARNING **: cannot open display:

---

### Post by prshah on 2008-05-21
> **tobydeh said:**
> i am fully aware of what gparted is.
which part of "Remote Partition Resize" did you have trouble understanding?
this is a live server and a very serious issue.
I just need someone to tell me how to merge all partitions into sda1

You can't "merge" partitions. That being said; what kind of remote access do you have? ssh? 

If it's a command line remote access then you can use the CLI versions of parted and resize2fs.

If you are bent on "merging" them and not resizing them then you have to budget for downtime. 

Once the server is down, boot with a live CD (how, remotely?, no idea; how did you install it?) copy the contents of the "/usr", "/var". etc using "cp -a" to a third directory "/home/something" (since /home has the most space and you don't plan on using much of it); then umount the partitions contain /usr /var etc. Delete or/and resize the partitions to free up space, extend "/" into the freed space and then again use "cp -a" to copy the files back from the third partition to the root partition.

CAVEAT: This is a _suggestion_, I haven't done this anywhere and am only suggesting a logical course. You do this at your own risk.

---

### Post by cmsj on 2008-05-29
Hi tobydeh

I got a new 1and1 Root server (the cheapest version of it) about 5 weeks ago and did exactly what you are asking about.

However, I do have to warn you that yesterday when one of my users was grabbing a file via ftp from the server, it OOPSed (ie the kernel crashed and the machine had to be rebooted).
I noticed that their 6.06 install has a weird custom kernel, so maybe there are some odd hardware issues here.

If you do want to press ahead with getting rid of their insane partitioning. I had a slight advantage over you though - mine was a new machine so it was basically blank and all I had to do was reboot into the rescue image and copy everything from their /home, /usr and /var partitions to the / partition. I then edited the etc/fstab to not mount the other drives (which I notice were partitioned with the insane xfs filesystem - I strongly suspect they have some overkeen sysadmins who think they are making a super tweaked setup).
After doing that I unmounted all the partitions, deleted the /home, /usr and /var partitions and then changed the / partition to use up all of the spare space, and ran ext2resize to make the filesystem fill the partition.

I'm not sure that giving you detailed instructions via a forum is particularly wise, because it looks like your setup is slightly different to mine (e.g. mine has two disks, so I also set up software raid1) and I don't want to leave you with a broken setup.

Definitely back up everything first, then make sure you only have as much data as will fit into the existing / partition. The tools you will need are basically just fdisk, fsck and ext2resize.

Please feel free to email me (cmsj atsymbol tenshu dotsymbol net) if you have any more questions (I don't check the forums very often).

---

### Post by cmsj on 2008-05-29
actually one thing you could do that would be very helpful would be to grab /proc/config.gz if it exists, I don't have a copy of the kernel they had on the machine with dapper, I'm just running the normal hardy kernel now.

Also, their serial console is useful, but sadly they are using cheap non-server hardware so you have to set up the serial console yourself, which you can do with this in /boot/grub/menu.lst (they probably have lilo installed, which also has serial console options, but I switched to grub):

# kopt=root=blahblahblah ro console=ttyS0,57600

(blahblahblah will vary depending on which machine you have, so don't change that bit, just add "console=ttyS0,5700" to the line).
if you are using grub then you can also make it display on the serial console with:

serial --unit=0 --speed=57600
terminal --timeout=2 serial console

near the top of your /boot/grub/menu.lst

---

