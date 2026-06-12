---
title: "Partition help"
date: 2008-04-29
forum: General Help
---

### Post by Yoguess on 2008-04-29
Switching from XP pro to Hardy
Have 60gb drive, and 1gb RDRAM
I want to have my /Home to be on its own partition, (this is where my personal files and junk is stored and saved, right??)

are all partitions primary?? and are they all ext3?? and does it matter in what order i create them?

sda1, 100 or 200 MB ext3 mounted as /boot (for grub??)
sda2, 10GB ext3 mounted as / (for linux??)
sda3, 48GB ext3 mounted as /home (for my files)
sda4, 1.8GB swap

after the partitions are created do i need to point each one or just click next and everything will work??

big help please, i have tonight off so i would like to do this tonight if possible

---

### Post by tamoneya on 2008-04-29
the order in which you make the partitions do not matter.  In the manual partitioner you will get a place where you can put in the mount point.  If you dont do it in the manual partitioner it can always be done later in fstab

---

### Post by Zorael on 2008-04-29
A harddrive can only have four **primary** partitions, so the only way to have more is to make the fourth primary an **extended** partition, which in turn can contain as many **logical** partitions as you'd ever want. There's likely a limit.

You should make everything Linux-related ext3, yes. "/" mount for the system itself, and "/home" for your personal settings and files. If you're planning on creating a multi-user system you may want to split it up into two partitions; one that's the /home folder and one that's a storage partition that all users can access (mounted under, say, /media/storage, or /mnt/main, or /stuff, or wherever). My current /home/zorael folder eats up about 400mb, and that's with Cedega and Wine installed, so if you're planning on having a whole bunch of users you might want to dedicate a couple of gigabytes to that partition.

And don't dedicate several hundred megabytes to Grub. Think of each kernel build as weighing in on about 15mb, and depending if you set up a graphical grub bootloader you might want to give it 5mb in total. So 50mb will give you room enough for three kernels or so.

I wouldn't say it's as crucial to have a partition dedicated to /boot as it is to have one dedicated for /home.

So in your case I'd do something like the following, assuming you really want a dedicated /boot.
sda1: [primary] 50mb ext3 (/boot)
sda2: [primary] 10gb ext3 (/)
sda3: [primary] 2-3gb ext3 (/home)
sda4: [extended] REST OF SPACE n/a (will contain sda5 and above)
sda5: [logical] REST MINUS SWAP SIZE ext3 (/media/storage or whatever)
sda6: [logical] 1.8gb swap

Of course, if you skip the /boot partition and have it be included in the root one, you'll only get four partitions so you don't need to mess around with extended and logical ones.

---

### Post by Yoguess on 2008-04-29
This is going to be a single use single OS system
so if i didnt create /boot will it be created later on?

---

### Post by Yoguess on 2008-04-29
Solved, Thank You Guys.

---

