---
title: "root on ZFS &amp; Mirroring"
date: 2023-07-15
forum: General Help
---

### Post by aljames2 on 2023-07-15
In getting my notes together for a root install that I want to try, using the OpenZFS manual setup, I have 3 questions to clarify some things.
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html)

There will be 2 NVMe's - each 1 TB.  the 2nd will be a Mirror of the 1st.

On the Primary NVMe will be a root install, per the openzfs setup, plus an additional partition & pool for data.

#1 - I read in various places that you "should" give ZFS the full disk, and other resources that say do not.  My inclination is before starting anything, to set up a GPT partition table with a single large partition spanning say 97% of the disk, as an example, and then starting the installations on this "part1".  Is this necessary?  I also have read that when you do give ZFS the full disk, that zfs will take care creating a starting and ending point on the disk.  Not sure which way to go here.

#2 - The setup talks about creating the same set of partitions (bpool, rpool, swap, etc) on $DISK2, as well as the primary disk.  I thought creating the Mirror relationship between the 2 disks would handle everything on DISK2.   If when a disk fails, you replace it, doesn't the resilvering process recreate everything on the new disk?  If so, why would the installation require manual partitioning on DISK2 (the mirror)?

#3 - I want to add a data partition & pool on the same NVMe. Is it best to complete the root setup first, then create the data partition & pool?

---

### Post by MAFoElffen on 2023-07-16
#1... No, do not give ZFS, LVM, BTRFS, mdadm a full raw disk. It is possible, but not a smart thing to do. You do not want to have an unbound container, which you can't be certain of it's size and the limits of that boundary. 

If you create your pool inside of a partition you have complete control of where the outer container is, the size it is going to be, and how to refer to it. Especially since you say you are doing RAIDz members.Check your notes against these notes, which are for installing 22.04: [https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#step-5-grub-installation](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#step-5-grub-installation)

Set the partition as you vdev. The pool will reside within it... I use sgdisk, which is the cli interface to gdisk. Easy to script things using that. I usually type everything (all my commands) into text document, as "my recipe", beforehand, so I can work out the plan previous to the install. 

During the install, I just cut and paste. Then do the same, pasting the output of what it said, into that doc, so i have a record... Or if something went wrong, I have the error, so I can work it out. That is handy, especially when working out the unique ID name's of the partitions, UUID's, etc, and finishing all the mountpoints and fstab entries.

#2... Which leads into your second question. Your specify, in your pool create command which vdev devices are members of that pool, and what they act like (spanned, mirrored, or raid). 

The first thing I do, when I get a disk, is create a new GPT partition table. That is my outer boundary. Then I plan out what partitions and of what size and type they will be.

For most systems, I usually setup a root disk with EFI, BOOT, ROOT, HOME, DATA partitions. If I am setting up raid members or want to have more portability, then The first disk may just be EFI, BOOT, SWAP, ROOT or even just EFI, BOOT & SWAP... Then separate other members. When you think of the outer boundary of a vdev as being a partition, then it doesn't matter if that vdev exists on the same disk or not.

The pool will mirror. The partitions exist outside of that, so you needs to define those yourself. Even if we were talking about mdadm... If you put mdadm RAID1 as a whole raw disk, then what is inside that container will mirror, if you have a partition, then LVM, all those things within that container will mirror... But then you only have one whole large container on that disk, that is unbound, and taking up full space on that disk. Where are your boot files, and the definition of that raid array going to reside (inside of the initramfs)? Sort of a chicken before the egg kind of affair, right? At the least, I have an EFI, BOOT and BPOOL on that root disk.

Many times, if I have large disks, I may not have a plan for all the space yet, at the start. I may give out partitions of x size to a certain pool in pieces. Then add more vdev's to that pool later, from my unallocated reserve... Creating a new slice (partition), and add it to a pool, to add more space to that pool. Even sometimes, if I need to add space to something temporarily...

A few things about ZFS terms... Scrubbing, Trimming, and Resilvering. ZFS is a volume manager that has it's own filesystem type inside it. It is not like LVM, where it has another filesystem of an external type, inside it's volume containers. Think of a Scrub job, as being the same a fsck is to "ext" filesystems. Do this every so often, to check and repair you filesystems. If you install with the scripts, you will find a monthly cron job that runs a scrub job on every 2d Sunday night of the month, and a trim job, every 1st Sunday of the month. Those jobs assume that the User's system is running on those days and times, for it to do that... I do a scrub on my pools once a week.

"Trim" in ZFS Zpools initiates an immediate on-demand TRIM operation for all of the free space in a pool. This operation informs the underlying storage devices of all blocks in the pool which are no longer allocated and allows thinly provisioned devices to reclaim the space.

Resilver moves data and rewrites it... It is an operation to rebuild parity across a pool due to either a degraded device (for instance, a disk may temporarily disappear and need to 'catch up') or a newly replaced device.

The only way to resdistribute data evenly acrow disk, or to defrag data on the disks, is to take a snapshot or backup, delete the data inside of the pool, and restore it to write the data fresh. ZFS write to free sectors, it can't do that if something is already there. That make sense?

 
***
Currently, I am testing something new. There was a drive type-- "Dell Fusion-io io-Drives" that I used to work with on Dell PowerEdge Servers, which are just a PCIe card, with internal PCIe SSD storage devices behind a RAID controller... The storage controller of them divides the SSD silicon storage behind it into raid members (all on that same card)... So I have been testing using partition vdevs on larger NVMe drives as RAIDz members.The limitations that exist with spun drives, with the numbers of heads, and that physical mechanism do not exist on silicon storage devices. The tests, so far, seem to be showing some very good results, and benchmarks. 

I already use separate vdevs as SLOG and L2Arc caches on NVMe...

I know., you would think that it shouldn't really be able to work, but we do it all the time on Virtual Hosts. It 'does' work on physical silicon storage. I just need to figure out the implications of that. Most of the time in a failure of silicone storage, you lose a partition, (because you get a bad sector) so this approach seems to have sound logic so far. And with ZFS, it checks, and verifies a write, before it completes the commit (COW), so RAIDz is thought , as being self-healing. Expected life-cycle of current gen silicon storage is 10 years, versus 2-3 years of large enterprise spun SATA disks.  But if you lose a whole NVMe, then you lose it all. But that is true if you loose an io-Drive device... That is why you do backups...

---

### Post by aljames2 on 2023-07-17
Great post, clears up a lot for me!

When would I know if the SLOG & L2Arc partitions are needed?  I think these go on a separate disk.  Are these the ones that can kill an SSD in a few months.

The scripts that automatically set up the trip & scrub, is that the Bootmenu script.  That is the only one I think I have seen so far.

---

### Post by MAFoElffen on 2023-07-17
SLOG (write cache) and L2ARC (read cache) are disk caches for RAIDZ arrays. I use on them NVMe partitions for SSD and SATA membered Arrays, where the cache is on faster media than the disk type. You have mentioned only NVMe and pools, nothing about any other disk types
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
[sudo] password for mafoelffen: 
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:15:22 with 0 errors on Sun Jul  9 00:39:23 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

```
I believe that the cron jobs /etc/cron.d/zfsutils-linux  are installed as part of package 'zfsutils-linux'. Contents is
```

mafoelffen@Mikes-B460M:~$ grep . /etc/cron.d/zfsutils-linux
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# TRIM the first Sunday of every month.
24 0 1-7 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/trim ]; then /usr/lib/zfs-linux/trim; fi
# Scrub the second Sunday of every month.
24 0 8-14 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/scrub ]; then /usr/lib/zfs-linux/scrub; fi

```
My Samsung EVO 870's are warrantied for 5 years or 1,200 TB TBW. That is a lot of written data.

What scripts are you referring to that you say can kill an SSD in months? Biggest thing that can kill a SSD is heat.

I did have a problem where I had to turn off NCQ to prevent a problem I was having that was causing intermittent errors in my SSD Arrays. Once I did that, that problem disappeared.

---

### Post by aljames2 on 2023-09-02
I could use an understanding check on this part of the manual install steps at OpenZFS for root on zfs:

```
zfs create -o canmount=off -o mountpoint=/ \
    rpool/USERDATA
zfs create -o com.ubuntu.zsys:bootfs-datasets=rpool/ROOT/ubuntu_$UUID \
    -o canmount=on -o mountpoint=/root \
    rpool/USERDATA/root_$UUID
```

I understand the 1st command is creating the dataset filesystem: rpool/USERDATA
I am trying to understand why the canmount & mountpoint is needed in the 1st command because I see that as just establishing a container, while the 2nd command would create what is to be mounted on this rpool/USERDATA filesystem. I suppose I am wrong about this?

BTW... Is this zsys business needed if not interested in auto-snapshotting?  We can script zfs snapshots without zsys right?  I know the manual command at least.

I would also like to do something similar to the above for home but use a separate pool: hpool
I would imagine that to look something like this:

```

zfs create -o canmount=off -o mountpoint=none \
    hpool/USERDATA
zfs create -o mountpoint=/home \
    hpool/USERDATA/home_$UUID

```

---

### Post by aljames2 on 2023-09-05
Bump for my most recent question above..

Zsys included in the dataset creation command is my main question.  Is it needed for Ubuntu root on zfs?  I do not see it being used with other distros.  I understand zfs can be used without it but what is lost in doing so?  It appears to be providing a boot menu environment & other utilities such as auto-snapshotting which I would trim down to 2-3 weeks at most, possibly would script my own snapshots.

Sorry if I appear lost on the topic, just been doing a lot of reading & writing my own notes on the topic.  Fun stuff

Would like to see Linux + zfs mature as an option out of the box with some custom pool/dataset options.  BSD is totally married to zfs, if you want to use it. My pfSense box is on BSD/zfs.  I think we’ll get there.

My attraction to this for root is for a 24/7 “on” system.  I live in an area accustomed to power outages.  I have a nice battery backup where i get alerts & can ssh in to nicely shut things down until I get home.  I don’t have a whole house generator…yet. I trust the integrity of the data on zfs even if the plug is pulled.  I have backups but the zfs would be nice for this particular box.

---

### Post by #&amp;thj^% on 2023-09-05
> **aljames2 said:**
> 
BTW... Is this zsys business needed if not interested in auto-snapshotting?  We can script zfs snapshots without zsys right?  I know the manual command at least.

Then it's not needed, I'm not sure I would want it on a Server there is better ways for back-ups/snapshots. 

> **aljames2 said:**
> Bump for my most recent question above..

Zsys included in the dataset creation command is my main question.  Is it needed for Ubuntu root on zfs?  

Would like to see Linux + zfs mature as an option out of the box with some custom pool/dataset options.  BSD is totally married to zfs, if you want to use it. My pfSense box is on BSD/zfs.  I think we&#8217;ll get there.

My attraction to this for root is for a 24/7 &#8220;on&#8221; system.  I live in an area accustomed to power outages.  I have a nice battery backup where i get alerts & can ssh in to nicely shut things down until I get home.  I don&#8217;t have a whole house generator&#8230;yet. I trust the integrity of the data on zfs even if the plug is pulled.  I have backups but the zfs would be nice for this particular box.
Same as above "Not Needed"

---

### Post by MAFoElffen on 2023-09-05
I wanted to backup a few posts back, so this does not get skipped unanswered, so things are clear, for clarification... 

Think of it like Russian Nested Dolls. Containers, inside of other container, that have other containers. Think of your storage areas as those containers. As per the methods that we referred you to at OpenZFS: First you create a pool, then a base dataset in that pool, then sub-datasets. Then of those as directories and sub-directories. In reality all you need is pool/dataset. Setting pool/base_dataset/sub_dastaset lets you get creative and organize thing a little better... For taking a snapshots of a dataset instead of a pool (or the complete pool), and placing (mounting) those sub_datasets wherever you want in that filesystem. Just some added granularity.

If you look at $UUID in those instructions, I replace that with the release number I am using. You can always change the names with zfs rename later. Not a biggy. Just saying that is not a reuirement is not that important. I make it mean something to "me".

As for backups, For years I had been doing them manually. Snapshots, Send/Receive to a backup server or Backup Pool. I have been testing  those for myself. If you Google them, it is overwhelming what comes back. I wet to the FREEBSD Forum and read lots of posts, reviews and threads. The one that seemed to be the most recommended was sanoid & syncoid. I installed both and am very happy with them. Sanoid creates the snapshots and syncoid replicates (Sends/Receives) them to local or remote stores.

---

### Post by aljames2 on 2023-09-06
Thank you both!  I understand better now the terminology, layout, and what the setup commands are doing.  It’s clicking now :)

---

### Post by MAFoElffen on 2023-09-06
LOL. Once you "do it" and start using it for a bit (hands on), these conversations are going to click and you can look back and say "oh yes, that is how that works..."

I think people need that "understanding" to get through things and it makes things easier in the long run.

I am sure that in no time, that it will be second nature to you, and you will be telling other users how to do this and that in your own words. LOL

---

### Post by aljames2 on 2023-10-04
> **MAFoElffen said:**
> LOL. Once you "do it" and start using it for a bit (hands on), these conversations are going to click and you can look back and say "oh yes, that is how that works..."

I think people need that "understanding" to get through things and it makes things easier in the long run.

I am sure that in no time, that it will be second nature to you, and you will be telling other users how to do this and that in your own words. LOL

I have my first Ubuntu Desktop root on ZFS install working, & booting ok.  I’ll post some command outputs tonight after work to show what I have so far.

I have a punch-list of small things to sort out.  1 big one seems to be that the distribution install did not populate my /home user directory, it is empty.  The username appears on boot-up & I can log into it, but /home/aljms is empty.  Perhaps because I set up home on its own pool, which is a deviation from the OpenZFS manual steps, & I suspect that pool was not seen during the install.

---

### Post by MAFoElffen on 2023-10-04
Hmmm... I setup mine during my installs, and have had no problems. I'm sure we'll see that in the mountpoints... Or in which/who's instructions you followed. If the one's from OpenZFS, then search on "create a user account" and below that you will see this part, which populates the user folder:
```

cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username

```

---

### Post by #&amp;thj^% on 2023-10-04
> **MAFoElffen said:**
> Hmmm... I setup mine during my installs, and have had no problems. I'm sure we'll see that in the mountpoints... Or in which/who's instructions you followed. If the one's from OpenZFS, then search on "create a user account" and below that you will see this part, which populates the user folder:
```

cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username

```

+1
> **MAFoElffen said:**
> 
Or in which/who's instructions you followed. If the one's from OpenZFS, then search on "create a user account" and below that you will see this part, which populates the user folder:

I'm glad you asked I was also confused, nothing you or I recommended.

---

### Post by aljames2 on 2023-10-04
I did follow the OpenZFS setup for 22.04 with some edits to include a separate pool for /home.  I also left out the zsys portions of some commands.  I notated my plan before starting and took good notes along the way.  This is a new system w/no production use yet so I can start over at some point if needed. I probably will do a tear-down and redo later to test my plan after some revisions.

**After the grub installation section**, I did my first reboot.  However, the last thing I did prior to that reboot was
zpool export -a  (This returned a: cannot export, 'rpool' busy).  I rebooted anyway, then at the initramfs prompt, I did this:
```
zpool import -f rpool
zpool export rpool
reboot
```
...and it seemed to boot normally and allowed me to login as root.

At this point I had no network connection (I'm no longer on the Live USB), so I made an adjustment in  /etc/netplan/01-netcfg.yaml  to temporarily set dhcp4: true & rebooted again, and my network connected worked.

Then I ssh'd in and continued with the "After First Boot" steps, which included:

```

dpkg-reconfigure grub-efi-amd64  (because I am doing mirror topology)
username=aljms
UUID=2204

zpool create \
    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/home -R /mnt \
    hpool mirror \
    ${DISK1}-part5 \
    ${DISK2}-part5

zfs create -o canmount=off -o mountpoint=none hpool/USERDATA

zfs create -o canmount=on -o mountpoint=/home/$username \
    hpool/USERDATA/ubuntu_$UUID

adduser $username
cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username

apt dist-upgrade --yes
```

Here are some current outputs from various commands:
```
aljms@b550a-rzn:~$ zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  2.75G   264M  2.49G        -         -     0%     9%  1.00x    ONLINE  -
hpool  59.5G  1.27M  59.5G        -         -     0%     0%  1.00x    ONLINE  -
rpool  99.5G  3.83G  95.7G        -         -     0%     3%  1.00x    ONLINE  -
```

```
aljms@b550a-rzn:~$ zpool status
  pool: bpool
 state: ONLINE
status: One or more features are enabled on the pool despite not being
    requested by the 'compatibility' property.
action: Consider setting 'compatibility' to an appropriate value, or
    adding needed features to the relevant file in
    /etc/zfs/compatibility.d or /usr/share/zfs/compatibility.d.
config:

    NAME                                                     STATE     READ WRITE CKSUM
    bpool                                                    ONLINE       0     0     0
      mirror-0                                               ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNM0W701966L-part3  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNS0W517316H-part3  ONLINE       0     0     0

errors: No known data errors

  pool: hpool
 state: ONLINE
config:

    NAME                                                     STATE     READ WRITE CKSUM
    hpool                                                    ONLINE       0     0     0
      mirror-0                                               ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNM0W701966L-part5  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNS0W517316H-part5  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
config:

    NAME                                                     STATE     READ WRITE CKSUM
    rpool                                                    ONLINE       0     0     0
      mirror-0                                               ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNM0W701966L-part4  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_500GB_S6PXNS0W517316H-part4  ONLINE       0     0     0

errors: No known data errors
```


```
aljms@b550a-rzn:~$ zfs list
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            264M  2.37G       96K  /boot
bpool/BOOT                                       258M  2.37G       96K  none
bpool/BOOT/ubuntu_2204                           258M  2.37G      258M  /boot
bpool/grub                                      5.42M  2.37G     5.42M  /boot/grub
hpool                                           1.27M  57.7G       96K  /home
hpool/USERDATA                                   192K  57.7G       96K  none
hpool/USERDATA/ubuntu_2204                        96K  57.7G       96K  /home/aljms
rpool                                           3.83G  92.6G       96K  /
rpool/ROOT                                      3.83G  92.6G       96K  none
rpool/ROOT/ubuntu_2204                          3.83G  92.6G     2.68G  /
rpool/ROOT/ubuntu_2204/srv                        96K  92.6G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                       192K  92.6G      192K  /tmp
rpool/ROOT/ubuntu_2204/usr                       248K  92.6G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 152K  92.6G      152K  /usr/local
rpool/ROOT/ubuntu_2204/var                      1.14G  92.6G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                 139M  92.6G      139M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                  96K  92.6G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  1013M  92.6G      899M  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService    96K  92.6G       96K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    132K  92.6G      132K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt              78.7M  92.6G     78.7M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/dpkg             35.0M  92.6G     35.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                96K  92.6G       96K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  14.4M  92.6G     14.4M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                   96K  92.6G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                  160K  92.6G      160K  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 128K  92.6G      128K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                   152K  92.6G      152K  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                    96K  92.6G       96K  /var/www
rpool/USERDATA                                   236K  92.6G       96K  /
rpool/USERDATA/root_2204                         140K  92.6G      140K  /root
```

```
aljms@b550a-rzn:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0     7:0    0     4K  1 loop  /snap/bare/5
loop1     7:1    0  73.9M  1 loop  /snap/core22/864
loop2     7:2    0 240.5M  1 loop  /snap/firefox/3206
loop3     7:3    0   497M  1 loop  /snap/gnome-42-2204/141
loop4     7:4    0  91.7M  1 loop  /snap/gtk-common-themes/1535
loop5     7:5    0  40.8M  1 loop  /snap/snapd/20092
sda       8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1    8:1    0   750M  0 part  /boot/efi
&#9500;&#9472;sda2    8:2    0     4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0     4G  0 raid1 [SWAP]
&#9500;&#9472;sda3    8:3    0     3G  0 part  
&#9500;&#9472;sda4    8:4    0   100G  0 part  
&#9492;&#9472;sda5    8:5    0    60G  0 part  
sdb       8:16   0 465.8G  0 disk  
&#9500;&#9472;sdb1    8:17   0   750M  0 part  
&#9500;&#9472;sdb2    8:18   0     4G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0     4G  0 raid1 [SWAP]
&#9500;&#9472;sdb3    8:19   0     3G  0 part  
&#9500;&#9472;sdb4    8:20   0   100G  0 part  
&#9492;&#9472;sdb5    8:21   0    60G  0 part  
nvme1n1 259:0    0 931.5G  0 disk  
nvme0n1 259:1    0 931.5G  0 disk  

```

```
aljms@b550a-rzn:~$ df -Th
Filesystem                                     Type   Size  Used Avail Use% Mounted on
tmpfs                                          tmpfs  3.2G  1.9M  3.2G   1% /run
rpool/ROOT/ubuntu_2204                         zfs     96G  2.7G   93G   3% /
rpool/ROOT/ubuntu_2204/srv                     zfs     93G  128K   93G   1% /srv
rpool/ROOT/ubuntu_2204/tmp                     zfs     93G  256K   93G   1% /tmp
rpool/ROOT/ubuntu_2204/usr/local               zfs     93G  256K   93G   1% /usr/local
rpool/ROOT/ubuntu_2204/var/cache               zfs     93G  140M   93G   1% /var/cache
rpool/ROOT/ubuntu_2204/var/games               zfs     93G  128K   93G   1% /var/games
rpool/ROOT/ubuntu_2204/var/lib                 zfs     94G  899M   93G   1% /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService zfs     93G  128K   93G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager  zfs     93G  256K   93G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt             zfs     93G   79M   93G   1% /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/dpkg            zfs     93G   36M   93G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs             zfs     93G  128K   93G   1% /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                 zfs     93G   15M   93G   1% /var/log
rpool/ROOT/ubuntu_2204/var/mail                zfs     93G  128K   93G   1% /var/mail
rpool/ROOT/ubuntu_2204/var/snap                zfs     93G  256K   93G   1% /var/snap
rpool/ROOT/ubuntu_2204/var/spool               zfs     93G  128K   93G   1% /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                 zfs     93G  256K   93G   1% /var/tmp
rpool/ROOT/ubuntu_2204/var/www                 zfs     93G  128K   93G   1% /var/www
tmpfs                                          tmpfs   16G     0   16G   0% /dev/shm
tmpfs                                          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
rpool/USERDATA/root_2204                       zfs     93G  256K   93G   1% /root
bpool/BOOT/ubuntu_2204                         zfs    2.7G  258M  2.4G  10% /boot
/dev/sda1                                      vfat   739M  6.1M  733M   1% /boot/efi
bpool/grub                                     zfs    2.4G  5.5M  2.4G   1% /boot/grub
hpool/USERDATA/ubuntu_2204                     zfs     58G  128K   58G   1% /home/aljms
tmpfs                                          tmpfs  3.2G  124K  3.2G   1% /run/user/1000

```

---

### Post by MAFoElffen on 2023-10-05
The only thing difference I can see, when I create a separate home pool it this:
```

zfs create -o canmount=on -o mountpoint=/home/$username \
    hpool/USERDATA/ubuntu_$UUID

```
Which caused this
```

hpool                                           1.27M  57.7G       96K  /home
hpool/USERDATA                                   192K  57.7G       96K  none
hpool/USERDATA/ubuntu_2204                        96K  57.7G       96K  /home/aljms

```
I mount that dataset to /home, like this
```

hpool                                                                                      56.6G   327G       96K  /home
hpool/USERDATA                                                                             56.5G   327G       96K  none
hpool/USERDATA/root_2204                                                                   2.86G   327G     2.86G  /root
hpool/USERDATA/ubuntu_2204                                                                 53.7G   327G     53.7G  /home

```
On yours, that would be fine, until, someday, if you decided to create another user... The system will try to create another user folder in /home, which is still mounted just as hpool, but not within a dataset...

In mine, since mounted further up the branch of /home (at /home), all the user folders are within the dataset hpool/USERDATA/ubuntu_2204.

What is the output of 
```

grep 'aljms' /etc/passwd
ls -lah /home/aljms

```
EDIT: On the first command, you can edit the output with X'es to mask your long name for privacy here.

---

### Post by aljames2 on 2023-10-05
> **MAFoElffen said:**
> 
In mine, since mounted further up the branch of /home (at /home), all the user folders are within the dataset hpool/USERDATA/ubuntu_2204.

I was trying to set mine up so that new users could be created in this dataset as you show here.

I need to get clear on where a dataset begins & ends.  For example:

I know clearly the pool, in this case is:  hpool    (mounted at /home).

Is this a dataset?  hpool/USERDATA
              (not mounted, but why?, perhaps because data is not stored here, but only to act as a parent to give configuration inheritances?)

Is this also a dataset?  hpool/USERDATA/ubuntu_2204
              (mounted at /home also?)

-------------------
```
aljms@b550a-rzn:~$ grep 'aljms' /etc/passwd
aljms:x:1000:1000:,,,:/home/aljms:/bin/bash
```

I entered past, leaving blank, the questions about me, when setting up the first user in the useradd step.

```
aljms@b550a-rzn:~$ ls -lah /home/aljms
total 2.0K
drwxr-xr-x 2 root root 2 Oct  3 21:27 .
drwxr-xr-x 3 root root 3 Oct  2 22:47 ..

```

---

### Post by MAFoElffen on 2023-10-06
Yes, hpool/USERDATA, is a dataset and is not mounted because it is a grouping placeholder. New users, as it is mounted presently, will not be created in dataseta /hpool/USERDATE/ubuntu_2204 because it is mounted at /home/aljms. A pool and a dataset can have the same mountpoint.

So the way to fix that, so it works as you want, just like I described that mine works... Is very easy. All is take is to re-set the mountpoint... 

*** BUT BEFORE THAT, create a ~/aljms folder inside the existing dataset and move all your files & folders from your User Folder into that subdirectory. The reason for that, is that remounting the dataset one level lower, the files, if not done like that, would end up in /home/ without your user folder. 

After doing that... Then remount the dataset like this like this:
```

sudo zfs set -o mountpoint=/home  hpool/USERDATA/ubuntu_2204

```
And that dataset will mount at /home, and inside that will be you /home/aljms folder that you just created, with it's files & folders, where you moved them (into the right place.).

Did I explain that in a way you understand those instructions?

---

### Post by aljames2 on 2023-10-06
> **MAFoElffen said:**
> Did I explain that in a way you understand those instructions?

Superbly!  It's fixed, and I understand it better.  Thanks!!  :)

Once I changed the mountpoint to the correct place, I then had to do these commands and reboot to populate a normal /home user.

```
cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username
```

```
aljms@b550a-rzn:~$ zfs list
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            264M  2.37G       96K  /boot
bpool/BOOT                                       258M  2.37G       96K  none
bpool/BOOT/ubuntu_2204                           258M  2.37G      258M  /boot
bpool/grub                                      5.41M  2.37G     5.41M  /boot/grub
hpool                                           4.45M  57.7G       96K  /home
hpool/USERDATA                                  1.92M  57.7G       96K  none
hpool/USERDATA/ubuntu_2204                      1.83M  57.7G     1.83M  /home
rpool                                           3.85G  92.6G       96K  /
rpool/ROOT                                      3.84G  92.6G       96K  none
rpool/ROOT/ubuntu_2204                          3.84G  92.6G     2.68G  /
rpool/ROOT/ubuntu_2204/srv                        96K  92.6G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                       176K  92.6G      176K  /tmp
rpool/ROOT/ubuntu_2204/usr                       248K  92.6G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 152K  92.6G      152K  /usr/local
rpool/ROOT/ubuntu_2204/var                      1.16G  92.6G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                 139M  92.6G      139M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                  96K  92.6G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  1013M  92.6G      899M  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService    96K  92.6G       96K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    132K  92.6G      132K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt              79.0M  92.6G     79.0M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/dpkg             35.0M  92.6G     35.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                96K  92.6G       96K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  30.4M  92.6G     30.4M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                   96K  92.6G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                  160K  92.6G      160K  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 128K  92.6G      128K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                   152K  92.6G      152K  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                    96K  92.6G       96K  /var/www
rpool/USERDATA                                   236K  92.6G       96K  /
rpool/USERDATA/root_2204                         140K  92.6G      140K  /root

```

```
aljms@b550a-rzn:~$ df -Th
Filesystem                                     Type   Size  Used Avail Use% Mounted on
tmpfs                                          tmpfs  3.2G  1.9M  3.2G   1% /run
rpool/ROOT/ubuntu_2204                         zfs     96G  2.7G   93G   3% /
rpool/ROOT/ubuntu_2204/srv                     zfs     93G  128K   93G   1% /srv
rpool/ROOT/ubuntu_2204/tmp                     zfs     93G  256K   93G   1% /tmp
rpool/ROOT/ubuntu_2204/usr/local               zfs     93G  256K   93G   1% /usr/local
rpool/ROOT/ubuntu_2204/var/cache               zfs     93G  140M   93G   1% /var/cache
rpool/ROOT/ubuntu_2204/var/games               zfs     93G  128K   93G   1% /var/games
rpool/ROOT/ubuntu_2204/var/lib                 zfs     94G  899M   93G   1% /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService zfs     93G  128K   93G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager  zfs     93G  256K   93G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt             zfs     93G   80M   93G   1% /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/dpkg            zfs     93G   36M   93G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs             zfs     93G  128K   93G   1% /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                 zfs     93G   31M   93G   1% /var/log
rpool/ROOT/ubuntu_2204/var/mail                zfs     93G  128K   93G   1% /var/mail
rpool/ROOT/ubuntu_2204/var/snap                zfs     93G  256K   93G   1% /var/snap
rpool/ROOT/ubuntu_2204/var/spool               zfs     93G  128K   93G   1% /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                 zfs     93G  256K   93G   1% /var/tmp
rpool/ROOT/ubuntu_2204/var/www                 zfs     93G  128K   93G   1% /var/www
tmpfs                                          tmpfs   16G     0   16G   0% /dev/shm
tmpfs                                          tmpfs  5.0M  4.0K  5.0M   1% /run/lock
rpool/USERDATA/root_2204                       zfs     93G  256K   93G   1% /root
bpool/BOOT/ubuntu_2204                         zfs    2.7G  258M  2.4G  10% /boot
/dev/sda1                                      vfat   739M  6.1M  733M   1% /boot/efi
bpool/grub                                     zfs    2.4G  5.5M  2.4G   1% /boot/grub
hpool/USERDATA/ubuntu_2204                     zfs     58G  1.9M   58G   1% /home
tmpfs                                          tmpfs  3.2G   92K  3.2G   1% /run/user/1000

```

Only thing left on my to-do is figure out why I might be seeing this startup dependency output:

```
 
[DEPEND] Dependency failed for SSSD NSS...
[DEPEND] Dependency failed for SSSD Auto...
[DEPEND] Dependency failed for SSSD PAC...
[DEPEND] Dependency failed for SSSD PAM...
[DEPEND] Dependency failed for SSSD SSH...
[DEPEND] Dependency failed for SSSD Sudo...
```

---

### Post by aljames2 on 2023-10-06
I did find this solution to correct the dependencies.
[https://askubuntu.com/questions/1474588/dependency-failed-for-sssd-service-responder-socket](https://askubuntu.com/questions/1474588/dependency-failed-for-sssd-service-responder-socket)

This worked, I guess it was just some loose ends from a manual install.

I think I'm good for now. Will work next on setting up an NMVe for another data pool. Then on to getting sanoid/syncoid set up for snapshots.

I also need to test how to recover should one of the root drives in the mirror fails.

---

### Post by MAFoElffen on 2023-10-06
I had that same boot message on two if my machines, and found that somehow package sssd was installed. My solution was to remove it. 

That conf file is installed whe sssd is installed. I am not joinig those two machines to a Windows Domain, so... Not needed.
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo grep sssd /var/log/syslog | grep 'Sep 22'
Sep 22 22:23:47 Mikes-ThinkPad-T520 apparmor.systemd[3453]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:23:47 Mikes-ThinkPad-T520 apparmor.systemd[3453]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:23:47 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 apparmor.systemd[3435]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:25:24 Mikes-ThinkPad-T520 apparmor.systemd[3435]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:25:24 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 apparmor.systemd[3369]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:27:42 Mikes-ThinkPad-T520 apparmor.systemd[3369]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:27:42 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 apparmor.systemd[3382]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:31:06 Mikes-ThinkPad-T520 apparmor.systemd[3382]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:31:06 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 apparmor.systemd[3313]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:32:56 Mikes-ThinkPad-T520 apparmor.systemd[3313]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:32:56 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 apparmor.systemd[3316]: Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Sep 22 22:34:50 Mikes-ThinkPad-T520 apparmor.systemd[3316]: Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-autofs.socket: Job sssd-autofs.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-pac.socket: Job sssd-pac.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-pam.socket: Job sssd-pam.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-ssh.socket: Job sssd-ssh.socket/start failed with result 'dependency'.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Bound to unit sssd.service, but unit isn't active.
Sep 22 22:34:50 Mikes-ThinkPad-T520 systemd[1]: sssd-sudo.socket: Job sssd-sudo.socket/start failed with result 'dependency'.

```
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list sssd
Listing... Done
sssd/jammy-updates,now 2.6.3-1ubuntu3.2 amd64 [installed,automatic]
sssd/jammy-updates 2.6.3-1ubuntu3.2 i386

```
Upon further invetigation, 
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list krb5* --installed
Listing... Done
krb5-locales/jammy-updates,jammy-updates,now 1.19.2-2ubuntu0.2 all [installed,automatic]
N: There are 2 additional versions. Please use the '-a' switch to see them.
mafoelffen@Mikes-ThinkPad-T520:~$ apt list ldap* --installed
Listing... Done
ldap-utils/jammy-updates,now 2.5.16+dfsg-0ubuntu0.22.04.1 amd64 [installed,automatic]
N: There are 2 additional versions. Please use the '-a' switch to see them.

```
But notice they were marked as "installed, automatic"... Not manually installed by the user. So they were installed by something, previous to 2022-10-27. Becauseon that date, they got an update. My apt logs go back to 2022-07-28, and I cannot see when they were originally installed.
 
I removed/purged all 3 packages. There are not enough packages there to fuction as either a client nor server for ssd, openldap, slapd, and kerberos.

---

