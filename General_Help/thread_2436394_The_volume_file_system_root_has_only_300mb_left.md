---
title: "The volume file system root has only 300mb left"
date: 2020-02-05
forum: General Help
---

### Post by dorpapst on 2020-02-05
Hello friends,
I know that this has been discussed a few times before, but I have not got any clue about it yet. It is my first ubuntu installation.
I have installed Ubuntu (18.04) on a 128 GB usb drive such that I can take it with me and boot on different places.

I gave the system 16 GB of space and the general partition took the rest (there is also a swap partition of 4 GB).

Now I was running into the error:
"The volume file system root has only 300mb left"

I have been installing a few necessary programs  (including IntelliJ, Telegram, Java and LaTeX), but not much.

Is there any way I could possibly resize the two main partitions in favour of the 16gb partitions without destroying my entire installation? (for sure I would need to do this from another PC)

I really don't want to reinstall all of this again.

The output of the commands
```
df -h
df -i
```
is
```
Filesystem      Size  Used Avail Use% Mounted on
udev            7,8G     0  7,8G   0% /dev
tmpfs           1,6G  2,1M  1,6G   1% /run
/dev/sdb2        15G   14G  319M  98% /
tmpfs           7,8G  318M  7,5G   4% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/sda1       197M   31M  167M  16% /boot/efi
/dev/sdb3        94G  274M   89G   1% /home
tmpfs           1,6G   28K  1,6G   1% /run/user/121
/dev/loop0       89M   89M     0 100% /snap/core/7270
tmpfs           1,6G   64K  1,6G   1% /run/user/1000
/dev/loop1       55M   55M     0 100% /snap/core18/1066
/dev/loop2       43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop3      150M  150M     0 100% /snap/gnome-3-28-1804/67
/dev/loop4      4,2M  4,2M     0 100% /snap/gnome-calculator/406
/dev/loop5       15M   15M     0 100% /snap/gnome-characters/296
/dev/loop6      1,0M  1,0M     0 100% /snap/gnome-logs/61
/dev/loop7      3,8M  3,8M     0 100% /snap/gnome-system-monitor/100
/dev/loop8       68M   68M     0 100% /snap/sublime-text/85
/dev/loop9      132M  132M     0 100% /snap/telegram-desktop/1038

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev           2031512    587 2030925    1% /dev
tmpfs          2037331   1086 2036245    1% /run
/dev/sdb2      1001712 372141  629571   38% /
tmpfs          2037331     92 2037239    1% /dev/shm
tmpfs          2037331      5 2037326    1% /run/lock
tmpfs          2037331     18 2037313    1% /sys/fs/cgroup
/dev/sda1            0      0       0     - /boot/efi
/dev/sdb3      6266880   5199 6261681    1% /home
tmpfs          2037331     27 2037304    1% /run/user/121
/dev/loop0       12823  12823       0  100% /snap/core/7270
tmpfs          2037331     47 2037284    1% /run/user/1000
/dev/loop1       10041  10041       0  100% /snap/core18/1066
/dev/loop2       39455  39455       0  100% /snap/gtk-common-themes/1313
/dev/loop3       27707  27707       0  100% /snap/gnome-3-28-1804/67
/dev/loop4        1550   1550       0  100% /snap/gnome-calculator/406
/dev/loop5         271    271       0  100% /snap/gnome-characters/296
/dev/loop6         354    354       0  100% /snap/gnome-logs/61
/dev/loop7         734    734       0  100% /snap/gnome-system-monitor/100
/dev/loop8       14689  14689       0  100% /snap/sublime-text/85
/dev/loop9       24873  24873       0  100% /snap/telegram-desktop/1038
```

I am running this on a MacBook if this information is relevant. 

Thanks in advance for any help! :)

---

### Post by TheFu on 2020-02-05
If you plan to do Java development, you'll need much more storage to deal with Java's bloat.
25G for the OS.
50G+ for /home
and depending on the amount of RAM, you'll probably want a much larger swap file.  If you choose to use LVM during the install, there are ways to increase the LV size, create a new LV for /home and another LV for swap. You didn't choose LVM with the install above, BTW.

**lsblk** will show some handy data.  A few aliases for storage stuff:
```
alias lsblk='lsblk -o name,size,type,fstype,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
Those show interesting information and don't show junk like loop devices.  


Java development will suck using USB storage. You really want a fast NVMe SSD.

There really isn't any viable solution for your needs, except larger, faster, storage.

If you have good backups and techniques, moving to different storage is about 30 minutes of effort.  Unfortunately, if you are new to Unix administration, it is unlikely to work the first time.

USB is slow and often has queueing issues which don't matter for accessing data or backups, but do matter greatly when running an OS. 

Oh - and avoid snap packages. They waste storage, among some other bad behaviors which a developer would want to avoid.

---

### Post by dorpapst on 2020-02-05
Hey, thank you very much for your answer! Thanks also for your advices. I think you have overestimated a Bit what I am going to do with my Ubuntu installation. I might start it one time every two weeks, macOS is going to stay my main system. Sometimes, I need to deal with some tools which do not run very good on macOS due to stupid Apple restrictions, that&#8217;s the only reason of the Ubuntu system&#8216;s existence. I have never developed a Java project being bigger than 5 classes at the same time.
I think under this circumstances it might be ok to stay like this.

is there any way of resizing the USB device from another installation? Or well, the question is more: Does it force problems on my Ubuntu if I am going to resize my partitions from another PC? 

I have no idea what snap packages are, but I am going to research it, thank you for telling me about it.

many greetings

---

### Post by CatKiller on 2020-02-05
> **dorpapst said:**
> is there any way of resizing the USB device from another installation? Or well, the question is more: Does it force problems on my Ubuntu if I am going to resize my partitions from another PC? 

It should be fine. Resizing standard partitions *shouldn't*, AFAIK, change the partitions' UUIDs, so you won't have to mess with your fstab. Just use GPartEd or whichever tool you like that can handle Linux filesystems. You're right that you'd need to do it from somewhere other than that environment: you can't fiddle with a partition that's mounted.

If you're running it on machines with plenty of RAM you might consider using tmpfs for things like /var/log to limit the number of writes. Thumb drives don't last forever. All flash media has a finite number of writes, and they don't overprovision thumb drives like they do with SSDs.

---

### Post by yancek on 2020-02-05
If sdb2 and sdb3 are contiguous (this is not shown with df) then you should be able to move sdb3 to the right and when that is finished you will have space after sdb2 and before sdb3 and can move sdb2 there.  This requires moving the data on sdb3 which is minimal per your output posted above.

---

### Post by TheFu on 2020-02-05
Without seeing output from **sudo fdisk -l** we just don't know what is possible.  I would boot from a "Try Ubuntu" flash drive, run gparted, and see what was possible.  Shifting data is much longer than backing up and restoring to newly setup partitions.  OTOH, you'll need some Linux chops to fix the /etc/fstab and UUIDs so it will boot. That is a risk for any partition modifications.  Total data loss is another, real, risk, especially for someone not used to doing partition work.

For OSX, isn't there something called brew?

---

### Post by dorpapst on 2020-02-06
Hello Friends,
I have decided to reinstall it on a SSD this morning, the argument of CatKiller was a fair point. Thanks everybody for answering here.
I was running into a weird problem installing it there, but this is covered in another topic such that other people reading this some time later, having the same problem do not get confused.
Many thanks!

---

