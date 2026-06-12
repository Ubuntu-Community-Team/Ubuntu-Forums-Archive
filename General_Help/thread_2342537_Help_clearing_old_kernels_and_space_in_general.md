---
title: "Help clearing old kernels and space in general"
date: 2016-11-07
forum: General Help
---

### Post by thomas62 on 2016-11-07
Hi guys!

I recently cleaned a lot of old crap off my Ubuntu installation and managed to upgrade.

However I suddenly have no space in my home folder and I am struggling to locate what's going on.

I am committed to using Linux after a couple of years however I need to know how to resolve this problem.

Things I have done.

1) Run bit bleech
2) Uninstalled old applications I no longer use
3) Run sudo apt-get clean
4) Tried to compact thunderbird folders
5) I am unable to auto remove kernels ATM (may be because eI just opened Synaptic

Q - I have installed [B]synaptic

Is this a safe thing to do



Any other tips?[/B]

---

### Post by jerome1232 on 2016-11-07
There's a convenient script to purge old kernels, though they don't take up much space.
```
sudo purge-old-kernels
```

Pop open disk usage analyzer and have it scan your /home to determine what's using so much space. Do you have separate root partitions and /home partitions?

If you like you could post the output of these commands, it would help determine where your space has gone

```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by thomas62 on 2016-11-08
Hi

TY for replying. Output below. FYI first command did not work.

Re disk usgae.

I have spent some time inspecting this in the past. I need the VMs etc for dev environment. I feel Thunderbird is causing issues. I tries to "compact folder" without much luck (not enough space). I am unsure if boot and home are on seperate partiations, but I think they are (it;s been sometime since I set this up - dual booting.

TY again for taking a look., I REALLY appreciate it. 

As I said I had recently cleared a bunch of space. This is a new / recent issue since upgrading to latest ubuntu (perhaps the old image is there?)

Still curious to see if anyone can help with the image above re Synatpic manager.

---

### Post by alexjpowell on 2016-11-08
Looks like your /home/ partition is only 8GB and you have more than 3GB of emails stored

---

### Post by thomas62 on 2016-11-08
> **alexjpowell said:**
> Looks like your /home/ partition is only 8GB and you have more than 3GB of emails stored

Yeah, I am trying to remove emails in Thunderbird / compact folders and delete things. It's not going so well.

Can I safely use something like gpatred to increase the space used by Home?

---

### Post by Impavidus on 2016-11-08
You have upgraded to xenial and are running the 4.4 kernel. You can safely remove all 3.16 kernels.

But those are not the cause of your problem. You have a separate /home partition and that's full. The old kernels are in your / partition, which has room to spare. You have to try and remove some stuff from your /home partition. I see you have 3GB of email stuff. But 8GB is really small for a /home partition. I suggest you try and make /home larger, or merge it into your / partition, which has 26GB free space, and not use a /home partition at all.

Your 4.5GB in /root, which is the home directory of the root user, is a bit strange too.

---

### Post by jerome1232 on 2016-11-08
1st, I'm not sure why your installation doesn't have that purge-old-kernels script... I didn't *think* I installed it extra I guess I must have.

2nd, although this isn't an actual problem, as Impavidus says it's weird for you to have anything in /root . If you have opened nautilus as root and have been deleting things those things will have been moved to roots trash, that's my first guess as to why you have so much data in /root. (That's just a guess, it's the most common reason I've seen for lots of data being there)

> **thomas62 said:**
> 
Can I safely use something like gparted to increase the space used by Home?

It's something I'd highly recommend if you have more disk space to spare, 8 gb's is incredibly lean.

That depends on how you define "safely" and how your partitions are currently arranged. Yes you should be able do it from a live cd, and 99% of the time it goes just fine, but just in case... make sure you have good working backups of any precious data before you go murking with partitions, there's always that chance that something could go wrong and you don't want to lose irreplaceable data. Could you provide a screenshot of your partition layout? (via gparted or the "disks" utility)

---

### Post by thomas62 on 2016-11-08
> **Impavidus said:**
> You have upgraded to xenial and are running the 4.4 kernel. You can safely remove all 3.16 kernels.

But those are not the cause of your problem. You have a separate /home partition and that's full. The old kernels are in your / partition, which has room to spare. You have to try and remove some stuff from your /home partition. I see you have 3GB of email stuff. But 8GB is really small for a /home partition. I suggest you try and make /home larger, or merge it into your / partition, which has 26GB free space, and not use a /home partition at all.

Your 4.5GB in /root, which is the home directory of the root user, is a bit strange too.

TY for taking the time to reply.

I am working to try and reduce the amount of space Thunder is making up (compacting folders did not work but I tried doing something to my profile and fingers crossed, it seems to be working)

I think I said I am dual booting, but I doubt that's got anything to do with the 4.5GB in root you mentioned.

In your opinion, is it safer to merge home into my / partition or make /home larger?

Ty again.

> **jerome1232 said:**
> 1st, I'm not sure why your installation doesn't have that purge-old-kernels script... I didn't *think* I installed it extra I guess I must have.

2nd, although this isn't an actual problem, as Impavidus says it's weird for you to have anything in /root . If you have opened nautilus as root and have been deleting things those things will have been moved to roots trash, that's my first guess as to why you have so much data in /root. (That's just a guess, it's the most common reason I've seen for lots of data being there)


It's something I'd highly recommend if you have more disk space to spare, 8 gb's is incredibly lean.

That depends on how you define "safely" and how your partitions are currently arranged. Yes you should be able do it from a live cd, and 99% of the time it goes just fine, but just in case... make sure you have good working backups of any precious data before you go murking with partitions, there's always that chance that something could go wrong and you don't want to lose irreplaceable data. Could you provide a screenshot of your partition layout? (via gparted or the "disks" utility)

Thanks again for your help. Here is gparted output.

Is there somewhere I can easily take space from?

I had[ a read of this]("http://askubuntu.com/questions/657923/how-to-increase-home-folder-size-in-ubuntu-14-04-lts") just to do some of my own research.

Can I modify with gParted or much better to use live CD?

---

### Post by ian-weisser on 2016-11-08
There is no magic bullet. Your space issue is due to your housekeeping and your admin decision to maintain a separate /home.
Impavidus is right - accumulation of old kernels is a red herring, and not the cause of your problem. (And it's fixed in 16.04 anyway)

I agree that you should merge /home into /. I think it's your best option.
Repartitioning always has a some risk of data loss. This is also a good time to make a backup of your data.

---

### Post by deadflowr on 2016-11-08
> **jerome1232 said:**
> 1st, I'm not sure why your installation doesn't have that purge-old-kernels script... I didn't *think* I installed it extra I guess I must have.

purge-old-kernels was included in bikeshed prior to 16.04.
In 16.04 it's included in byobu.

---

### Post by thomas62 on 2016-11-08
> **ian-weisser said:**
> There is no magic bullet. Your space issue is due to your housekeeping and your admin decision to maintain a separate /home.
Impavidus is right - accumulation of old kernels is a red herring, and not the cause of your problem. (And it's fixed in 16.04 anyway)

I agree that you should merge /home into /. I think it's your best option.
Repartitioning always has a some risk of data loss. This is also a good time to make a backup of your data.


Thanks Ian W

Can you please link m to some quality instructions / a guide on how to perform the merge?

PS all I have in the folder ATM is Thunderbird (trying to compress folders sans space is proving difficult, I am separately working on that) along with a couple VMs (I don;t think I need two need to work out which one I can drop) and a couple repos that amounts to less than 100mb.

---

### Post by ian-weisser on 2016-11-08
Step 0 - Backup your data
Step 1 - Edit /etc/fstab to remove the separate /home partition
Step 2 - Unmount the /home partition, and remount someplace else (like /tmp/home or /media/home)
Step 3 - Copy the contents of (old) /tmp/home to the (new) /home
Step 4 - Use parted/gparted to delete the old home partition and expand the remaining

---

### Post by jerome1232 on 2016-11-08
You don't have much you can take from, like everyone else, I think it'd be easiest to boot a live cd, copy everything out of /home partition into a /home folder on your root partition, then delete the /home partition and grow your root partition to fill in the space left by your /home partition.

I would do that like this

Boot live cd

make a dir at /mnt/root and mount /dev/sda4 to it

```
sudo mkdir /mnt/root
sudo mount /dev/sda4 /mnt/root
```

make a dir at /mnt/home and mount /dev/sda5 to it
```
sudo mkdir /mnt/home
sudo mount /dev/sda5 /mnt/home
```

Then I would rsync the home partition to your root partition
```
sudo rsync -av /mnt/home /mnt/root/home
```

Then I'd comment out the mounting of /dev/sda5 to /home in fstab to test booting in the modified environment. In nano you hit ctrl+o to save, ctrl+x to exit.
```
sudo nano /mnt/root/etc/fstab
```
look for a line that mentions /home as the mount point, don't delete the line just put a # in front of it to comment out. That way you can revert your changes easily. Like in my example here I've migrated my /home partition before on this machine (I don't remember why) The blue line is an example of commenting out a line. 

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=6a0907e1-7026-4155-b30e-f8869029b9d6 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/ubuntu--vg-home /home ext4 defaults 0 2
[COLOR="#0000CD"]#/dev/mapper/ubuntu--vg-steamBackup /home ext4 defaults 0 0[/COLOR]
/home/jeremy/Videos /export/Videos none bind 0 0

```

Once that is done reboot to test everything out, if it doesn't work for some reason you can boot back into a live cd edit fstab and undo the comment to restore your previous setup. If it's successful we could move on to deleting you old /home partition and growing your / partition.

---

### Post by thomas62 on 2016-11-09
> **jerome1232 said:**
> You don't have much you can take from, like everyone else, I think it'd be easiest to boot a live cd, copy everything out of /home partition into a /home folder on your root partition, then delete the /home partition and grow your root partition to fill in the space left by your /home partition.

I would do that like this

Boot live cd

make a dir at /mnt/root and mount /dev/sda4 to it

```
sudo mkdir /mnt/root
sudo mount /dev/sda4 /mnt/root
```

make a dir at /mnt/home and mount /dev/sda5 to it
```
sudo mkdir /mnt/home
sudo mount /dev/sda5 /mnt/home
```

Then I would rsync the home partition to your root partition
```
sudo rsync -av /mnt/home /mnt/root/home
```

Then I'd comment out the mounting of /dev/sda5 to /home in fstab to test booting in the modified environment. In nano you hit ctrl+o to save, ctrl+x to exit.
```
sudo nano /etc/fstab
```
look for a line that mentions /home as the mount point, don't delete the line just put a # in front of it to comment out. That way you can revert your changes easily. Like in my example here I've migrated my /home partition before on this machine (I don't remember why) The blue line is an example of commenting out a line. 

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=6a0907e1-7026-4155-b30e-f8869029b9d6 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/ubuntu--vg-home /home ext4 defaults 0 2
[COLOR=#0000CD]#/dev/mapper/ubuntu--vg-steamBackup /home ext4 defaults 0 0[/COLOR]
/home/jeremy/Videos /export/Videos none bind 0 0

```

Once that is done reboot to test everything out, if it doesn't work for some reason you can boot back into a live cd edit fstab and undo the comment to restore your previous setup. If it's successful we could move on to deleting you old /home partition and growing your / partition.

Hi - again, thanks. This is a lot of effort top type, I apperciate it and will go do some more command line tutes to get better in general.

FYI, I removed and reinstalled Thunderbird and could compact folders (in Thunderbird). This gave me some space but has not solved my issue 100%. As I will run into this problem again, and I need this OS to work so I better repair!

I'll make a Live CD soon and do as instructed.

Just a noob question - I was checking out folder / drive called "computer" and noticed I could not make a new folder here. Is this where I will merge into (I believe it is root and the "/" is at the top.

Also can u pls link any good articles on general ubuntu folder / partition structure. I tend to do "just enough" to get me out of trouble but I increasingly realise putting the effort in to fully understand pays dividends. For example, with Git:).

> **thomas62 said:**
> Thanks Ian W

Can you please link m to some quality instructions / a guide on how to perform the merge?

PS all I have in the folder ATM is Thunderbird (trying to compress folders sans space is proving difficult, I am separately working on that) along with a couple VMs (I don;t think I need two need to work out which one I can drop) and a couple repos that amounts to less than 100mb.

Ty, I am going to try live disc method, wish me luck!

> **jerome1232 said:**
>  In nano you hit ctrl+o to save, ctrl+x to exit.



Hehe yes Nano is cool and worth getting my head around.

---

### Post by Impavidus on 2016-11-09
[COLOR=#00ff00]***Fixed!***[/COLOR]
[s]Excellent description, but for one thing:[/s]> **jerome1232 said:**
> 
Then I'd comment out the mounting of /dev/sda5 to /home in fstab to test booting in the modified environment. In nano you hit ctrl+o to save, ctrl+x to exit.
```
sudo nano /etc/fstab
```
look for a line that mentions /home as the mount point, don't delete the line just put a # in front of it to comment out.

But you have to use the fstab of the installed system, not of the live session. So that is```
sudo nano /mnt/root/etc/fstab
```

---

### Post by jerome1232 on 2016-11-09
> **Impavidus said:**
> Excellent description, but for one thing:

But you have to use the fstab of the installed system, not of the live session. So that is```
sudo nano /mnt/root/etc/fstab
```

Whooops! I forgot that it was from a live system. Thanks for the catch, I edited the post.

---

