---
title: "software raid mystery"
date: 2007-05-10
forum: General Help
---

### Post by agrimstad on 2007-05-10
I'm using software raid (mdadm) with dapper and it sort of works. But it doesn't work right, it seems to me. By contrast, I've installed debian etch with software raid and everything seems to work to perfection. Here are some mdadm issues in dapper.

1. md device numbers have a life of their own. I can create an array with a particular md number and nail the thing with an entry in mdadm.conf. After a reboot, unless I happened to guess the right number, the md device will be renumbered. This doesn't happen with debian etch.

2. /proc/mdstat shows quasi duplicates of some arrays, but with different device numbers.

My hypothesis is that there is an extra active element in the dapper configuration that is trying to help recognize raid arrays and is doing its own thing in parallel with mdadm and its config file /etc/mdadm/mdadm.conf. It's either something in the kernel, the initrd or possibly lvm or evms. I don't use or want to use the latter two items.

Here's some evidence. First my mdadm.conf file:
-------------- mdadm.conf ----------------------
DEVICE partitions

# /var
ARRAY     /dev/md0 devices=/dev/sda6,/dev/sdb6

# /usr
ARRAY     /dev/md1 devices=/dev/sda7,/dev/sdb7

# /home ( /dev/sda8 and /dev/sdb8 )
ARRAY /dev/md5 level=raid1 num-devices=2 UUID=785bde7a:6a97af39:1886a892:740ce780

# /s1  (/dev/sda9 and /dev/sdb9 )
ARRAY /dev/md6 level=raid1 num-devices=2 UUID=2d71900d:429f03d6:87fd2c2f:eb9ed0ca

# /s2 ( /dev/sda10 and /dev/sdb10 )
ARRAY /dev/md7 level=raid1 num-devices=2 UUID=2ad8bf98:881e4859:b241d6c9:a047660d
--------------------------------------------------------------

Before you ask, the UUIDs are correct. And here's what shows up in /proc/mdstat after a reboot:

------------------- /proc/mdstat -----------------------
Personalities : [raid1]
md7 : active raid1 dm-5[1] dm-4[0]
      16000640 blocks [2/2] [UU]

md6 : active raid1 dm-3[1] dm-2[0]
      16000640 blocks [2/2] [UU]

md5 : active raid1 dm-1[1] dm-0[0]
      4000064 blocks [2/2] [UU]

md4 : active raid1 sda10[0] sdb10[1]
      16000640 blocks [2/2] [UU]

md3 : active raid1 sda9[0] sdb9[1]
      16000640 blocks [2/2] [UU]

md2 : active raid1 sda8[0] sdb8[1]
      4000064 blocks [2/2] [UU]

md1 : active raid1 sdb7[0] sda7[1]
      8000256 blocks [2/2] [UU]

md0 : active raid1 sdb6[0] sda6[1]
      995904 blocks [2/2] [UU]

unused devices: <none>
----------------------------------------------

So, what is responsible for identifying partitions as dm-x? The associated array number is that defined in mdadm.conf and mdadm knows about /dev/sd[ab].

And what is responsible for adding information about phantom arrays md2, md3 and md4 which are not mentioned in mdadm.conf? They are, in fact duplicates for arrays md5, md6 and md7.

What I want is complete control of how my arrays are numbered and until I can figure out how to achieve it, I just don't have confidence in dapper and won't proceed to move / and /boot to raid. I'm really considering moving from ubuntu to debian if I can't sort this out.

Any clues would be much appreciated.

---

### Post by snobel on 2007-05-11
dm-x sounds like device mapper stuff. Do the entries appear in /dev/mapper/? Did you try dm-raid at some point, or maybe it was the default array manager in dapper? (I don't think it is wise to use both dm-raid and mdadm arrays at the same time, and from what I've heard, forget about dm-raid) 

It looks like the arrays are assembled consistently if you use device names like /dev/sda6 instead of UUIDs in mdadm.conf. Can't you do that for the other 3 arrays?

Why are you using dapper? Raid-1 with mdadm works perfectly (in my relatively short experience) with edgy and feisty, so if you are going to reinstall you might as well stick with ubuntu.

---

### Post by agrimstad on 2007-05-11
The directory /dev/mapper contains only a file "control" which seems special; I can't cat it.

Also, I didn't use dm-raid. I vaguely recall that it's an older tool superceded by mdadm. I just started with the standard dapper desktop install and then tried to move file systems over to raid via mdadm. One thing I did was to remove a few arrays (via mdadm --stop) and recreate them with new numbers. The ghost that is creating the duplicate arrays may have access to some information that has remained somewhere.)

Regarding the use of UUIDs, I decided to try to use them after I installed debian etch on a server, a process that allowed me to create the raid arrays at install time, and that's the way etch does things. I deduced that it was the better way, without any real evidence, however. I know that the instability in array numbering is characteristic of dapper, as I experienced it before starting to use UUIDs. 

Finally, I'm using dapper because that's the CD I was able to get a while ago and it supposedly has "long term" support. At this stage I'm about 80% happy with dapper, but I find the raid situation troubling. Dapper was my first experience with a debian-type distribution; I've always used slackware in the past. Mostly, I'm going to be building servers and my experience with etch leads me to continue with it. The thing I haven't decided yet is what to do for a desktop distribution. At this stage, it's just not clear to me that ubuntu is the right choice.

---

### Post by snobel on 2007-05-12
> **agrimstad said:**
> Finally, I'm using dapper because that's the CD I was able to get a while ago and it supposedly has "long term" support. At this stage I'm about 80% happy with dapper, but I find the raid situation troubling. Dapper was my first experience with a debian-type distribution; I've always used slackware in the past. Mostly, I'm going to be building servers and my experience with etch leads me to continue with it. The thing I haven't decided yet is what to do for a desktop distribution. At this stage, it's just not clear to me that ubuntu is the right choice.
Fair enough. But you are aware that with the edgy or feisty alternate desktop CD you can set up the arrays at install time, the same way it is done in etch? (Though without support for encryption.)

---

### Post by agrimstad on 2007-05-12
Yes. After I invested a lot of time in adjusting my dapper environment to my needs, I did discover that there is this thing called the alternate CD that does RAID installs. And I suppose it works much like the etch install CD that I tried.

But that's neither here nor there. I know that I can fix this problem by doing a reinstall, either using etch or possibly feisty's alternate installation CD, which, by the way, I've downloaded an image for and even made the CD. What troubles me is that straight mdadm raid seems to be broken in dapper and nobody yet has been able to give me a clue why. Given that, I have no reason to believe one way of the other that feisty may also has some weird design that has multiple things, some hidden, that set up raid arrays. My suspicion currently points to lvm or evms, a couple of complicated things that seem way over the top for a non technical user's distribution such as ubuntu. As an experiment, I chmod'd to -x both in /etc/init.d and my reboot had massive problems. Basically, I'm not comfortable with all this.

---

