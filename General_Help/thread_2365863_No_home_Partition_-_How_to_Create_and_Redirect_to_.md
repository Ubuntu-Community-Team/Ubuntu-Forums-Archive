---
title: "No /home Partition - How to Create and Redirect to HDD?"
date: 2017-07-11
forum: General Help
---

### Post by Naturally-Simple on 2017-07-11
Hi there, I've done some reading on this already, but I suppose everyone has their own unique setups and preferred methods of doing things, and I don't want to stitch together a bunch of separate instructions/advice from those different setups and preferences, so here is my setup and preference:

I have a 20GB SSD installation of Ubuntu 16.04, ext4, no partitions. A second drive is 1TB HDD, also ext4, and ready for all my personal files. I would like the 1TB to house my home partition, but I currently don't have any partitions on the SSD. The 1TB HDD currently is just there to mount manually when I need it to. I also don't have swap, so can I have swap and home partitions on the 1TB HDD? My RAM is 16BG, so maybe I don't need a swap partition. The only reason I bring up swap in this thread is because it seems like I'm going to have to make a separate home partition anyway, so maybe it's a good opportunity to look into a swap partition as well.

With my home files and folders I don't want to see separate mounts on Nautilus, I just want to click on "Documents" or "Videos" and have them stored and pulled from the 1TB HDD.

There are two users on my system, and these files (especially music and videos) need to be shared across our home network.

Here is some output for you to chew on. First, output of fdisk -lu:
```

kevin@slab:~$ sudo fdisk -lu
[sudo] password for kevin: 
Disk /dev/sda: 18.7 GiB, 20014718976 bytes, 39091248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdc377ace

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 39090175 39088128 18.7G 83 Linux


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc02daef6

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G 83 Linux

```

Now, sudo blkid -c /dev/null -o list:
```

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              a09ac85c-f559-4f19-9e53-a5d3051458c7
/dev/sdb1  ext4             (not mounted)  7375567c-fc0d-4553-94e9-a2fae1292f5c

```

And mount command:
```

kevin@slab:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8133832k,nr_inodes=2033458,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1631036k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13622)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1631036k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

```

And last but not least, cat /etc/fstab:
```

kevin@slab:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a09ac85c-f559-4f19-9e53-a5d3051458c7 /               ext4    errors=remount-ro 0       1

```

I got these commands from oldfred on this thread: [https://ubuntuforums.org/showthread.php?t=1811198](https://ubuntuforums.org/showthread.php?t=1811198) which was similar, but not exactly what I think I want, unless I just wasn't understanding it all. As I've mentioned, I've read a lot about these issues, but they all seem to be unique to a certain user's system setup or their preference of how to mount. I'm very new to partitioning and mounting/symlinking, so this is all feeling rather out of my comfort zone. I feel as though my situation is pretty simple, and yet I can't find a basic step-by-step guide on creating a home partition from my existing installation and making sure all of those home files/folders are in the HDD in a seamless background setup.

It is very likely that I just don't understand highly technical jargon, so if you do give me some instructions, I'll need things explained in the least amount of jargon as possible, please. Thank you so much for your help!

---

### Post by oldfred on 2017-07-11
For a new user using Something Else and just creating & installing /home is easier. You can do that during install. But I normally use gparted to create partitions in advance and then in Something Else choose (change button) to choose which partition is / & which is /home.
That then adds the mount into fstab, and gives you ownership & permissions of your /home.
I still like to have more than one partition so some data is in one or the other. Makes repairs easier if needed. Backups of all data still required.

Do not know much about a second user & best way to share some folders. My wife & I just have one sign on for simplicity, but then each can see everything the other does.

The link above you refer to, has the instructions you can use if you want a separate /mnt/data partition and link folders back into /home so data is really in the data partition but seems like it is in /home directly.
But you have to manually create a partition on sdb, give yourself ownership & permissions to use it, mount it in fstab, and link all your folders into /home. 

If interested in two users & various configurations of permissions & ownership.
 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

If you have already installed & want /home on sdb.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Naturally-Simple on 2017-07-11
Thank you for your quick response, oldfred! I think I'll just leave the shared folder thing for now and worry about that at a later time.

It sounds to me like I can do the following steps (let me know if I'm right or wrong here):

1) Use the Ubuntu Startup Disc to boot; go into Gparted and re-partition the installation SSD so it has a /home partition (split evenly with 10GB for / and 10GB for /home?)
2) Create separate partition on 1TB HDD; still using Gparted, make a /mnt/data partition that takes up the majority of the drive.
3) Reboot, and boot back into regular Ubuntu; follow instructions found in the link previously mentioned.

Alternatively, would it make more sense for me to reinstall Ubuntu onto my SSD with my startup disc, and then make the partitions from scratch?

Questions regarding those instructions: 
1) Is this creating the mnt/data directory on my SSD or the HDD?
2) It's a choice of mine for either using "sudo chmod 766 /mnt/data" or "sudo chmod -R a+rwX /mnt/data"? What's the difference besides the big X making the non-executable files remain as non-executable? Is there a worry that doing it the other way will make non-executable files into executable files?
3) Do I need to do any moving/copying folders (ie. Music to oldMusic), since right now all my personal files are not even stored on this computer? (It's all been saved on an external, waiting to get everything set up first before I copy all my data).

Thanks again!

---

### Post by oldfred on 2017-07-11
I use 25 GB for / (root) and have /home inside it when using a separate data partition at /mnt/data.
If using gparted on new system I created several new 25GB partitions on my SSD, one current long term and one next (or now is last LTS version). And on HDD I create several 25 GB partitions for / of test installs and a large ext4 partition to use as data partition.
I just find it easier to use gparted than installer, but that is more a personal preference.

Some users that really understand permissions say to not use the octal notation.
See where mobius1 corrected me. He also prefers to separately mount each folder in home, where I use links. Have seen both used by others.
[https://ubuntuforums.org/showthread.php?t=1795369](https://ubuntuforums.org/showthread.php?t=1795369)

If UEFI make sure to use gpt, and I prefer gpt even if BIOS.
 Oldfred's current partitions Dec 2015 SSD & HDD, not much different now other than test installs all are different & different labels.
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

On a new clean install the first thing I do is delete the standard folders and link to the data in my /mnt/data partition. But you have to have the data in the data partition before you can link to those folders.

---

### Post by Naturally-Simple on 2017-07-11
Ah, ok, so if I can just keep my current SSD as is, and understand that /home is mixed in there, I can still use links to go from those home directories/files to my 1TB. Is that what you're saying I can do? That's likely the easiest for me to do at the moment, and then I don't have to mess around with re-partitioning (never mind re-installing).

I read your thread about the chmod, and will do the "sudo chmod -R a+rwX /mnt/data" option.

I still have yet to change anything on my system, so here's my understanding of the new list of what to do:

1) For the sake of having some data to link, I will copy/paste a handful of documents, downloads, music, pictures, and videos to my /home.
2) Then follow instructions according to what you posted on the link I listed above with creating /mnt/data and so on.

To be clear: I am creating this /mnt/data partition on the HDD or SSD? Is it a partition or a folder/directory or both?

---

### Post by oldfred on 2017-07-11
You create a partition like sdb1 on HDD.

You can manually mount before automount with fstab or not.
You need folders in sdb1 like music, documents and then can have any data you want in all those folders.
You then go thru setting up mount point /mnt/data, you then either manually mount to immediately use or add to fstab per example using your UUID & mount point like /mnt/data (it can be anything).
Always do this which remounts fstab entries. If not errors your /mnt/data should be mounted.
sudo mount -a

But without links the only way to get to it via naulitus is thru computer, file system, mnt and then you should see data.
To be able to copy data into /mnt/data you need to give yourself ownership & permissions.
Then create folder(s) and add data. And link just that one folder to know it works. I did the manual links one by one for several installs, then scripted it, then converted script to the one line script to find all folders & link all of them.

showing only part of folders that now are linked. Note d as first char means directory
```
fred@Asusz97:/mnt/data$ sudo chmod -R a+rwX /mnt/data
[sudo] password for fred: 
fred@Asusz97:/mnt/data$ ls -l
total 88
drwxrwxrwx  5 fred fred  4096 Aug 26  2016 Calibre_Library
drwxrwxrwx 21 fred fred 12288 Jul 11 15:45 Documents
drwxrwxrwx  9 fred fred 20480 Jul 10 12:48 Downloads
drwxrwxrwx 11 fred fred  4096 Dec 29  2016 grampsdb

```

Then in /home, a couple of the linked folders. I have 12 folders that are linked, note l as first char means linked folder
```
lrwxrwxrwx 1 root root     19 Apr 17  2016 Documents -> /mnt/data/Documents
lrwxrwxrwx 1 root root     19 Apr 17  2016 Downloads -> /mnt/data/Downloads

```

---

### Post by Naturally-Simple on 2017-07-12
Ok, I've already got the sdb1 partition in my HDD, so I don't need to create anything new there, correct?

> You can manually mount before automount with fstab or not. Do you mean test it out with manual mounting before choosing to write it into fstab for automount?

> You then go thru setting up mount point /mnt/data You mean doing "sudo mkdir /mnt/data" on my SSD or my HDD?

Then, the rest, I assume is following the instructions you listed on the site I gave earlier, which goes like this:
> sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

You can delete oldMusic after you confirm everything is ok.

Sorry to ask for so many clarifications, I've just been struggling with getting this computer back up and running for nearly a month, and I don't want to make more mistakes at this point of the game, especially after I paid a professional to install the OS. If only he had created the /home partition like I had wanted, and connected it to the HDD. So that's why I'm doing all this now, and it's very unfamiliar territory for me.

I really appreciate your help and will definitely donate to Ubuntu or your chosen fund after this is all up and running.

---

### Post by oldfred on 2017-07-12
When you mkdir, it does not know nor care where or what is to eventually be there. It just is creating a location/directly to be used. You can have many mounts, but a partition can only be mounted once.

I typically manually mount to give myself permissions & ownership initially, but after first time with new install, just add to fstab & remount.

I do not use gksudo anymore. They want to obsolete that. And you are not to use sudo with graphical applications. 
But gedit is easier to use than nano which I now use. Nano requires more arrow keys & keyboard commands.
sudo nano /etc/fstab

---

### Post by Naturally-Simple on 2017-07-12
I think I did it, oldfred!

I see, for example, the files I had moved into the 1TB HDD and now see them in Nautilus when I click on Downloads in the side panel.

Second last question: Aside from seeing this, how can I tell that the files are actually located in sdb1 on my HDD? Mostly out of curiosity's sake, but also to refer to later.

Last question: When/if I upgrade to next LTS, how do I preserve /home since it's not a separate partition?

---

### Post by Naturally-Simple on 2017-07-12
Never mind, while I don't know how to see that my 1TB sdb1 partition is now automatically feeding into Nautilus' Home folders (Documents, Downloads, Music, Pictures, Videos), I can see that whatever large files I've been copying over into those home folders are taking away space from the HDD, not the SSD.

I wish I understood a little more about how this actually works. It was the /mnt/data point that had me confused.

Hats off to you, oldfred! Marking as solved. Hope this helps another one in the future.

---

### Post by oldfred on 2017-07-12
Glad you got it working. :)

I use rsync to back up both /home which for me is tiny and /mnt/data. But do not follow links in backup of /home as I am separately backing up my data partition.
But most of /home is my user settings and I use a script to recreate some of those or use new defaults. So often do not restore /home's settings. But I also move some hidden folders with lots of data like the Firefox & Thunderbird profiles, but do not use links, but edit profile.ini. 

Some tools show data as linked, I have seen my old 60GB SSD as 300GB, but it was totaling all the links. Have not checked recently with my newer larger SSDs.
Others do not follow links and see data on drive where it really is. Gparted has always seen it correctly.

---

