---
title: "Expand ZFS root pool"
date: 2023-09-08
forum: General Help
---

### Post by SWoodhall on 2023-09-08
Hi there,

Hoping someone can point me in the right direction here. I have Kubuntu installed using ZFS as the root and boot filesystem, rpool and bpool respectively. This is a single SSD.

I want the rpool to use all of the available space, but it's only using  133GB out of the 232GB possible.

NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   314M  1.57G        -         -     0%    16%  1.00x    ONLINE  -
rpool   232G   133G  99.4G        -         -    24%    57%  1.00x    ONLINE  -

fdisk does show that the partition itself is the correct size, it's just difficult to understand how to get ZFS to expand the rpool within in it.

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   2685MB  2147MB  linux-swap(v1)                        swap
 3      2685MB  4833MB  2147MB  zfs
 4      4833MB  256GB   251GB   zfs


Any ZFS gurus out there who can help me along with this?

Thanks

---

### Post by #&amp;thj^% on 2023-09-08
> **SWoodhall said:**
> Hi there,


I want the rpool to use all of the available space, but it's only using  133GB out of the 232GB possible.

NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   314M  1.57G        -         -     0%    16%  1.00x    ONLINE  -
rpool   232G   133G  99.4G        -         -    24%    57%  1.00x    ONLINE  -

fdisk does show that the partition itself is the correct size, it's just difficult to understand how to get ZFS to expand the rpool within in it.


Thanks

Why?
The ZFS developer I work with says whole disk mode will have the two partitions. It's preferred unless you have multi path devices comprising the pool.

What are you trying to accomplish? or what is your goal here?
EDIT:MINE
```
zpool list rpool
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool   232G  46.4G   186G        -         -    16%    19%  1.00x    ONLINE  -

```
```
 zpool list -H -o name,size
bpool	1.88G
rpool	232G

```
```
inxi -p | grep rpool
    logical: rpool/ROOT/ubuntu_d1lsb0
    logical: rpool/USERDATA/me_snfksb
    logical: rpool/USERDATA/root_snfksb
    logical: rpool/ROOT/ubuntu_d1lsb0/srv
    logical: rpool/ROOT/ubuntu_d1lsb0/usr/local
    logical: rpool/ROOT/ubuntu_d1lsb0/var/games
    logical: rpool/ROOT/ubuntu_d1lsb0/var/lib
    fs: zfs logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/AccountsService
    fs: zfs logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/NetworkManager
    logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/apt
    logical: rpool/ROOT/ubuntu_d1lsb0/var/lib/dpkg
    logical: rpool/ROOT/ubuntu_d1lsb0/var/log
    logical: rpool/ROOT/ubuntu_d1lsb0/var/mail
    logical: rpool/ROOT/ubuntu_d1lsb0/var/snap
    logical: rpool/ROOT/ubuntu_d1lsb0/var/spool
    logical: rpool/ROOT/ubuntu_d1lsb0/var/www

```
```
df -hT
Filesystem                                       Type   Size  Used Avail Use% Mounted on
tmpfs                                            tmpfs  1.6G  3.5M  1.6G   1% /run
rpool/ROOT/ubuntu_d1lsb0                         zfs    189G  9.7G  179G   6% /
tmpfs                                            tmpfs  7.8G  516K  7.8G   1% /dev/shm
tmpfs                                            tmpfs  5.0M   16K  5.0M   1% /run/lock
tmpfs                                            tmpfs  7.8G     0  7.8G   0% /run/qemu
rpool/USERDATA/me_snfksb                         zfs    188G  9.5G  179G   6% /home/me
rpool/USERDATA/root_snfksb                       zfs    179G  3.3M  179G   1% /root
rpool/ROOT/ubuntu_d1lsb0/srv                     zfs    179G  128K  179G   1% /srv
rpool/ROOT/ubuntu_d1lsb0/var/games               zfs    179G  128K  179G   1% /var/games
rpool/ROOT/ubuntu_d1lsb0/usr/local               zfs    179G  256K  179G   1% /usr/local
rpool/ROOT/ubuntu_d1lsb0/var/lib                 zfs    189G   11G  179G   6% /var/lib
rpool/ROOT/ubuntu_d1lsb0/var/log                 zfs    179G  120M  179G   1% /var/log
rpool/ROOT/ubuntu_d1lsb0/var/mail                zfs    179G  128K  179G   1% /var/mail
rpool/ROOT/ubuntu_d1lsb0/var/snap                zfs    179G  128K  179G   1% /var/snap
rpool/ROOT/ubuntu_d1lsb0/var/www                 zfs    179G  128K  179G   1% /var/www
rpool/ROOT/ubuntu_d1lsb0/var/spool               zfs    179G  128K  179G   1% /var/spool
bpool/BOOT/ubuntu_d1lsb0                         zfs    926M  468M  458M  51% /boot
/dev/nvme0n1p1                                   vfat   511M   15M  497M   3% /boot/efi
rpool/ROOT/ubuntu_d1lsb0/var/lib/AccountsService zfs    179G  128K  179G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d1lsb0/var/lib/NetworkManager  zfs    179G  256K  179G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d1lsb0/var/lib/dpkg            zfs    179G   72M  179G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_d1lsb0/var/lib/apt             zfs    179G  659M  179G   1% /var/lib/apt
tmpfs                                            tmpfs  1.6G  200K  1.6G   1% /run/user/1000

```
BTW if you use Code Tags it is easier for us to read

---

### Post by aljames2 on 2023-09-08
I am not a zfs guru.  1fallen is, so respond to him and you will learn more!   I am only a budding wannabe at this point.  I’m hear to learn.

All I can add is a question, are you interpreting your size readings correctly?  It appears your rpool is already set to 232G, but you have only used 133G.  99G is still available…I think.

---

### Post by SWoodhall on 2023-09-08
Many thanks for your reply. All noted with the code tags. This is my first post hence my ignorance of that.

Simply put my total available disk space from rpool is 133G (in line with the ALLOC value), yet I know and can see there is a total of 232GB of available space that could be used by that pool on that partition. 

I tried setting autoexpand to on, but that has made no difference. If I try to write files beyond the 99.4GB Free space value it says there is not enough space.

---

### Post by #&amp;thj^% on 2023-09-08
> **SWoodhall said:**
> Many thanks for your reply. All noted with the code tags. This is my first post hence my ignorance of that.

Simply put my total available disk space from rpool is 133G (in line with the ALLOC value), yet I know and can see there is a total of 232GB of available space that could be used by that pool on that partition. 

I tried setting autoexpand to on, but that has made no difference. If I try to write files beyond the 99.4GB Free space value it says there is not enough space.

Understood Thanks.
May I ask the command used to set expand on rpool.
And also please show us this:
```
zpool get autoexpand

```
EDIT: I just had a thought, please show this as well:
```
sudo zfs list -t snapshot

```

---

### Post by SWoodhall on 2023-09-08
Thanks for your assistance

```
NAME   PROPERTY    VALUE   SOURCE
bpool  autoexpand  off     default
rpool  autoexpand  on      local

```

```
sudo zfs list -t snapshot
no datasets available

```

---

### Post by #&amp;thj^% on 2023-09-08
I'm leaving for work, I'll be back and forth here, but for now have a look here user(jakar): [https://serverfault.com/questions/703471/why-isnt-my-zfs-pool-expanding-using-zfs-on-linux](https://serverfault.com/questions/703471/why-isnt-my-zfs-pool-expanding-using-zfs-on-linux)
That will have the exact suggestions I would of given.
> Using zpool set autoexpand=off followed by zpool online -e was required to get the zpool to expand
I'll keep checking in.
I also asked a good friend to watch here too.

---

### Post by SWoodhall on 2023-09-08
Thanks, but I had already come across the same page when trying to research it myself. I have tried with autoexpand on and off, tried partprobe and zpool online -e to attempt to expand. It never seems to change unfortunately.

It's something that is trivially easy do with LVM, so it feels like it can't be that hard to do, but the answer eludes me!

---

### Post by #&amp;thj^% on 2023-09-08
> **SWoodhall said:**
> Thanks, but I had already come across the same page when trying to research it myself. I have tried with autoexpand on and off, tried partprobe and zpool online -e to attempt to expand. It never seems to change unfortunately.

It's something that is trivially easy do with LVM, so it feels like it can't be that hard to do, but the answer eludes me!
It's always good to let us know what you have already tried, so we here don't keep offering the same advice. :)
And has a reboot happened since you have changed what you have said done?
I'm having a tough time recreating your problem.
What I've done is first add a disk I can spare (I won't play with this one current use)
The disk is a 180 Gig Hd (sdc) it was already formatted as btrfs
```
zpool labelclear /dev/sdc
```
Now I'll add it
```
zpool add rpool -f /dev/sdc

```
Bring it online:
```
zpool online -e  rpool /dev/sdc

```
Check 
```
zpool status -v
  pool: bpool
 state: ONLINE
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  18d52db8-9b4c-6d4e-8415-3550bdbfd60c  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:01:00 with 0 errors on Fri Sep  8 12:48:33 2023
config:

	NAME                                    STATE     READ WRITE CKSUM
	[COLOR="#FF0000"]rpool                                   ONLINE       0     0     0
	  d6013007-da4e-134f-b787-50f9b10fb475  ONLINE       0     0     0
	  sdc                                   ONLINE       0     0     0[/COLOR]

```
New drive is high lighted in red.
EDIT:
```
&#57521;*home*&#57521;*me*&#57520;*zpool get autoexpand
NAME   PROPERTY    VALUE   SOURCE
bpool  autoexpand  off     default
rpool  autoexpand  off     default

```
Notice the change From Post#2(rpool	232G):
```
zpool list -H -o name,size
bpool	1.88G
rpool	399G

```
Will you now please run the system-info script in my signature and paste back the link it gives you here, saves me from asking a lot of commands needed to see.

---

### Post by #&amp;thj^% on 2023-09-08
> **aljames2 said:**
> I am not a zfs guru.  1fallen is, so respond to him and you will learn more!   I am only a budding wannabe at this point.  I’m hear to learn.
The Check is in the mail....LOL You flatter me, "No guru just a jack of all master of none"
> **aljames2 said:**
> 
All I can add is a question, are you interpreting your size readings correctly?  It appears your rpool is already set to 232G, but you have only used 133G.  99G is still available…I think.
Good Spot ;) I don't bother to try and read outputs not in "code tags" :KS

---

### Post by MAFoElffen on 2023-09-08
Adding to 1fallen's request, when you run the 'system-info' script, instead of just starting it normally, add a startup option of "--details" to the end of it like this:
```

# ran as a downloaded script
./system-info --details
# ran as package installed
system-info --details

```
That will turn on the detailed file manager reporting.

Additional to that, what would be helpfull is to see the results of these posted without code tgas:
```

sudo zpool list -v
sudo zfs get reservation rpool

```

---

### Post by #&amp;thj^% on 2023-09-08
> **MAFoElffen said:**
> Adding to 1fallen's request, when you run the 'system-info' script, instead of just starting it normally, add a startup option of "--details" to the end of it like this:
```

# ran as a downloaded script
./system-info --details
# ran as package installed
system-info --details

```
That will turn on the detailed file manager reporting.
Dang it forgot, we just need to make that default, we use it more with --details than without.
That way I don't forget...lol
> **MAFoElffen said:**
> This needs to be added
Additional to that, what would be helpfull is to see the results of these posted without code tgas:
```

sudo zpool list -v
sudo zfs get reservation rpool

```

This needs to be added "zfs get reservation rpool" to the script. :)
```
NAME   PROPERTY     VALUE   SOURCE
rpool  reservation  none    default

```

---

### Post by MAFoElffen on 2023-09-08
I could add it easy enough. Most users do not set that, but is a possibility. If you try the command without a pool or pool/dataset name, then it repeats for every single dataset and sub-dataset, like this:
```

mafoelffen@msi-ubuntu:~$ sudo zfs get reservation
[sudo] password for mafoelffen: 
NAME                                            PROPERTY     [COLOR=#ff0000]VALUE[/COLOR]   SOURCE
bpool                                           reservation  [COLOR=#ff0000]none[/COLOR]    default
bpool/BOOT                                      reservation  [COLOR=#ff0000]none[/COLOR]    default
bpool/BOOT/ubuntu_2204                          reservation  [COLOR=#ff0000]none[/COLOR]    default
dpool                                           reservation  [COLOR=#ff0000]none[/COLOR]    default
dpool/DATA                                      reservation  [COLOR=#ff0000]none[/COLOR]    default
dpool/DATA/ubuntu_2204                          reservation  [COLOR=#ff0000]none[/COLOR]    default
hpool                                           reservation  [COLOR=#ff0000]none[/COLOR]    default
hpool/USERDATA                                  reservation  [COLOR=#ff0000]none[/COLOR]    default
hpool/USERDATA/ubuntu_2204                      reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool                                           reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM                                  reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM/ubuntu_2204                      reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM/ubuntu_2204/ISO                  reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM/ubuntu_2204/KVM-VM               reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM/ubuntu_2204/images               reservation  [COLOR=#ff0000]none[/COLOR]    default
kpool/QEMU-KVM/ubuntu_2204/libvirt              reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool                                           reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT                                      reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204                          reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/srv                      reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/usr                      reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/usr/local                reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var                      reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/cache                reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/games                reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib                  reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/AccountsService  reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager   reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/apt              reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/docker           reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/dpkg             reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/lib/nfs              reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/log                  reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/mail                 reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/snap                 reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/spool                reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/tmp                  reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/ROOT/ubuntu_2204/var/www                  reservation  [COLOR=#ff0000]none[/COLOR]    default
rpool/USERDATA                                  reservation [COLOR=#ff0000] none[/COLOR]    default
rpool/USERDATA/root_2204                        reservation  [COLOR=#ff0000]none[/COLOR]    default

```
Shows that there is no reservations for any datasets in that... Which I guess is the right thing to do, because reservations can be set at any level of that, granually. But that generates a lot of output very fast! What I could do, is to check for other than value "none" in that field, and build an array of any dataset names that have a reservation set, or if no members found, indication that there are no reservations set for any. I think that would be the way to handle that in the Report. What do you think?[COLOR=#ff0000][/COLOR]

---

### Post by MAFoElffen on 2023-09-08
Let me back up a bit. I reread the whole thread... Including Post #1.

You are chasing ghosts... If you had posted withing CODE tags, it would ave made your output easier to read, and do the math on that... Let me repost this so you ca see and understand what that "really says" (LOL):
```

NAME   SIZE    ALLOC FREE  CKPOINT EXPANDSZ FRAG CAP  DEDUP HEALTH ALTROOT
bpool  1.88G   314M  1.57G -       -        0%   16%  1.00x ONLINE -
rpool  232G    133G  99.4G -       -        24%  57%  1.00x ONLINE -

```
Lets look at the math of that, shall we?
Alloc is what is used. Size is the total size of the pool. CAP is the percentage used...

Formula is: ((ALLOC * 100) / SIZE = CAP)

Or in your case:
```

(133x100)/232=57.327586207%

```
It is only at 57% capacity (so far)... So why do you think it is not using the pool at it's size?

You want to keep it below about 80% capacity. Let me give you a warning. ZFS has an overhead of about 3.9% of pool size that you need to leave it. So for your rpool, 9.08 GB is overhead. 80% would be 185GB.

You are not full right now and have about 52.6 GB to use until you get to 80% capacity... You go above that (abut 85%) then the underlying formulas go from a performance mode, into a space saving mode. It is possible to go to about 95% capacity, but then you risk locking the filesystem up. What happens it that it is a COW filesystem, meaning that it is copy on write transactions. It needs space to write the transaction before it commits it and actually does it. The risk of being "disk full", is that there might note enough space to delete files, to make room in your pool.

The math for ZFS underpinnings can get complex, but you don't really need to deal with that, unless you are trying to "understand" what it is doing, and how all the pieces work together... For example a formula I put togetherto calculate how much space is taken by metaslab_size of say rpool:
```
 
echo $((2 ** $(sudo zdb -C rpool | awk '/metaslab_shift/ {print $2}') / $((1024 * 1024 * 1024)) )) " GIB"

```
So watching "the capacity" is important to you. Do you need more room? Either clean up your files or add more vdevs.

Reservations... Some people use reservations to limit the space used in a dataset, but what I think is a better use of them is to create a dummy dataset, and say you name it as "reserved" and manually set if to 20% of the size of a pool. It's a safety buffer. Other datasets can only take up so much room until it hits that "reserved" space limit. When the pool gets full, destroy that dataset until you ca do some work on it, then recreate it.

But, snapshots do not respect reservations... So another factor to watch...

What I do, as a practice, is to NOT allocated **all** my "disk" to things, (I purposely reserve unused space) where I can quickly create another slice (partition) to give to something as a vdev.

Does this all make sense to you now?

---

### Post by SWoodhall on 2023-09-09
> **aljames2 said:**
> I am not a zfs guru.  1fallen is, so respond to him and you will learn more!   I am only a budding wannabe at this point.  I’m hear to learn.

All I can add is a question, are you interpreting your size readings correctly?  It appears your rpool is already set to 232G, but you have only used 133G.  99G is still available…I think.


I feel bad now for wasting your time. It didn't even occur to me to check that, as I couldn't have imagined I had used that much disk space up. I ran du to check folder sizes and found a very large game I had installed via Lutris a while back and had forgotten about and that is taking up nearly 100GB on it's own...

Thankyou both so much for your patience and help though.

---

### Post by MAFoElffen on 2023-09-09
[quote=Swoodhall]I ran du to check folder sizes and found a very large game I had installed via Lutris a while back and had forgotten about and that is taking up nearly 100GB on it's own...
[/quote]
Good find. Now you have more storage room free.

You are very welcome.

It is never a waste of time to provide  service and have an opportunity to provide education to a user in need.  It was well worth it. 

You were actually very "timely" with  this... You asked this and now understand how to read that "before" you  actually have a problem, You now know you have  many options to correct that. And how to use/do commands to check where your storage is being used.

There are a few things about ZFS  that you need to understand, in order to use it wisely. People understand them by using it. Things  are easier with it, if you understand how to use it, and know things you  can do with it. Otherwise, it is just sitting there, doing it's job,  and you are only touching about 10% of it's real potential. 

The  biggest thing I like about ZFS as a file manager is that it is so  flexible in what you can do. Most Users do not know what it can do,  until they actually need to. 

You now know of some of those things you can do beforehand.

For  instance, youwere less than 100 GB away from being full. In case there  were ever a problem again in the future... You have never done a snapshot to roll back to.  You have never taken a backup. You have made no disaster recovery plan  for any unforeseen problems.

Or maybe you might want to add more storage  space to your pool. Or separate your Home into it's own pool on a  separate disk. (That would be a very wise upgrade to manage your storage...) You have many options open to grow and prosper. Even for upgrades or to prepare for a new release upgrade.

This may be a time to think about some of those. If they ever do happen, then you will be ready for that.

And you know were to come to for any questions and answers. Even if it is to share what you have learned with others. We do care that you are well and can do what you need and want to do.

You still may want to run the system-info script to keep for yourself. It is not only a tool to help diagnose problems... But to use as an hardware/system inventory of "this is what your system looks like now."

Thank you and good luck.

I guess this means your question is answered and this is solved?

---

