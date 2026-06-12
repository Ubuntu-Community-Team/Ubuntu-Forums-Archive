---
title: "No swap file on 22.04"
date: 2022-09-13
forum: General Help
---

### Post by xeddog on 2022-09-13
I a couple of old I7 computers that I have installed Ubuntu 22.04 onto.  They have been running ok (One has some startup/shutdown issues, but runs ok when up) for a couple of weeks, but I haven't really done much with them yet.  Yesterday I was fiddling around and found out that neither has a swap file.  What the heck??

Aside from motherboards and processors, the hardware configurations are similar.  Boot drive is SATA SSD, additional 1TB hard drive in both, 16GB ram, and inexpensive graphics cards.  

Machine A hostname G-Man:
Intel I7-920 processor in a Gigabyte EX58-UD3R motherboard.   Ubuntu 22.04 was installed onto a freshly formatted 120GB Sata SSD, and the installation produced no errors that I could see.  Using gparted, I see that the boot drive is shown as /dev/sdb, the extra hard drive is /dev/sdc, and there is no sign of /dev/sda, and no sign of swap.    

Machine B hostname Stealth:
Intel I7-4770K processor in a ASUS motherboard that would be a nuisance to get the model number for.  Years ago, this machine had a much older version of Ubuntu installed on it, and has been upgraded using the upgrade process since (LTS only).  I know of at least 2 older LTS versions.  It has always had a swap file until this last upgrade unless....  About 2 months ago, this machine's boot drive was a 1TB WD black which I cloned to the 1TB SATA SSD using current copy of clonezilla.  I am fairly sure I specified the parameters correctly, and there is a 16GB space that is now listed as "unassigned" that I assume should have been the swap space.

Now the question is:  how do I get swap space?  I have found some info the internet which I think will work for me on Stealth since there is space already allocated but not used.  But G-Man has no space available to allocate for a swap file.  How do I fix that one?


Thanks,

Wayne

---

### Post by deadflowr on 2022-09-14
Do you mean swap partition?
Ubuntu hasn't created swap partitions during installs for something like 5 years now.
It should create swap files, which are slightly different than swap partitions.
A swap partition is a dedicated partition on a hard drive.
A swap file is a dedicated file within the file system.
what does 
```
free
```
tell you.
If that shows no swap see: [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
on how to add swap.

---

### Post by xeddog on 2022-09-14
Dang.  I guess I really need to start paying more attention to release notes.  I didn't know that swap partitions were a thing of history.

OK, so a swap file is created somewhere.  Where is it, and what is it named??   On the G-Man computer, I found a file simply named "swapfile' located in the root partition.  No such file on Stealth, and a  "sudo find / -mount  -name swapfile" yields no results.

---

### Post by &amp;KyT$0P# on 2022-09-14
To find all active swap, run
```
cat /proc/swaps
```

---

### Post by ne29914 on 2022-09-14
> **xeddog said:**
> Dang.  I guess I really need to start paying more attention to release notes.  I didn't know that swap partitions were a thing of history.


They are NOT a thing of history, just not part of the default install. I have swap partitions on all my 22.04 machines. Easily created during install, kept if present on 20.04 when updating.

---

### Post by xeddog on 2022-09-15
> **halogen2 said:**
> To find all active swap, run
```
cat /proc/swaps
```

This command returns column headings, but no entries.

---

### Post by xeddog on 2022-09-15
> **ne29914 said:**
> They are NOT a thing of history, just not part of the default install. I have swap partitions on all my 22.04 machines. Easily created during install, kept if present on 20.04 when updating.

What are the pros/cons of adding swap partitions???

Wayne

---

### Post by grahammechanical on 2022-09-15
In the past it was recommended that the swap partition be twice the size of RAM. But over the years the default size of RAM supplied has increased because memory became cheaper. With 8 GB RAM does a user really need 16 GB swap partition? With large amounts of memory the need for data to be paged in and out of memory to a swap partition is less likely. Besides, RAM has faster input and output speeds than a spinning hard disc. The speed difference might still be applicable even with Non Volatile Memory Express (NVMe) type of RAM.

Regards

---

### Post by ne29914 on 2022-09-15
> **xeddog said:**
> What are the pros/cons of adding swap partitions???

Wayne

I can't say from a technical point of view, others will chime in.

From useability point of view, I set up swap partitions on my laptops (RAM size + 50%) to be able to hibernate on lid close. This works wonderfully.
Theoretically, this should also be possible with a swapfile, and there are web articles on how to do it. But I've never seen feedback from anyone that ever got it to work. It's a phantom.

Cons: some high-power users who even encrypt their shoe size, there's apparently some security issue with hibernating. I don't use encryption, so I can't say.

---

### Post by #&amp;thj^% on 2022-09-15
I'll be the first here then to report a swapfile of "Swap:           8003         353        7650"
works just fine for my need if I want hibernate.
```
# /dev/nvme0n1p3
UUID=16699e8a-94ea-4003-b7cc-f391b474c998	/         	ext4      	rw,noatime	0 1

# /dev/nvme0n1p1
UUID=0457-7320      	/boot     	vfat      	rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2

# /dev/nvme0n1p3
UUID=16699e8a-94ea-4003-b7cc-f391b474c998	/home     	ext4      	rw,noatime	0 2

# /dev/nvme0n1p2
UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23	none      	swap      	defaults  	0 0


```
FTR: This is not Ubuntu.

---

### Post by ne29914 on 2022-09-15
> **1fallen said:**
> I'll be the first here then to report a swapfile of "Swap:           8003         353        7650"
works just fine for my need if I want hibernate.
```
# /dev/nvme0n1p3
UUID=16699e8a-94ea-4003-b7cc-f391b474c998    /             ext4          rw,noatime    0 1

# /dev/nvme0n1p1
UUID=0457-7320          /boot         vfat          rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro    0 2

# /dev/nvme0n1p3
UUID=16699e8a-94ea-4003-b7cc-f391b474c998    /home         ext4          rw,noatime    0 2

# /dev/nvme0n1p2
UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23    none          swap          defaults      0 0


```
FTR: This is not Ubuntu.

I've no idea what "Swap: 8003 353 7650" means, I can't find it in your CODE section.
But you definitely have a swap _partition_: ```
UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23    none          swap          defaults      0 0
```

---

### Post by #&amp;thj^% on 2022-09-15
> **ne29914 said:**
> I've no idea what "Swap: 8003 353 7650" means, 
Sure you do, you just want to point my wrong.
```
free -m
               total        used        free      shared  buff/cache   available
Mem:            7814        1826        3142          28        2845        5662
Swap:           8003         352        7651


```

> **ne29914 said:**
> 
But you definitely have a swap _partition_: ```
UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23    none          swap          defaults      0 0
```
Yep your right, this system has the swap partition, and not a a swap file, my other install that I'll boot if needed to show a swapfile works with hibernate.
```
swapon --show
NAME           TYPE      SIZE   USED PRIO
/dev/nvme0n1p2 partition 7.8G 352.5M   -2

```

---

### Post by ne29914 on 2022-09-15
> **1fallen said:**
> Sure you do, you just want to point my wrong.
```
free -m
               total        used        free      shared  buff/cache   available
Mem:            7814        1826        3142          28        2845        5662
Swap:           8003         352        7651

```


Yep your right, this system has the swap partition, and not a a swap file, my other install that I'll boot if needed to show a swapfile works with hibernate.
```
swapon --show
NAME           TYPE      SIZE   USED PRIO
/dev/nvme0n1p2 partition 7.8G 352.5M   -2

```
So, the size/usage of your swapfile is the name/ID of your swapfile ("Swap: 8003 353 7650"), the system you're showing has a swap partition, but somewhere you have a different machine where a real swapfile works with hibernate?
Please show, I'd be interested. As said, I've been unsuccessful.

And no, I don't want to show someone's wrong, but that part was not in your first answer.

---

### Post by #&amp;thj^% on 2022-09-15
> **ne29914 said:**
> 
Please show, I'd be interested. As said, I've been unsuccessful.
Might not be today though, as I test for other OS's and have limited time today.
 I thought I booted to a different system, that happens with my senior mind on occasions....LOL
Stay Tuned...

---

### Post by ne29914 on 2022-09-15
> **1fallen said:**
> Might not be today though, as I test for other OS's and have limited time today.
 I thought I booted to a different system, that happens with my senior mind on occasions....LOL
Stay Tuned...
Hey, don't sweat it. I have a working solution. Whenever you have the time.

Cheers.

---

### Post by #&amp;thj^% on 2022-09-15
> **ne29914 said:**
>  **_I have a working solution._** Whenever you have the time.

Cheers.
Yes you do and the golden rule here is "If its not broken Don't fix it"
My method will vary from any instructions based on Ubuntu....Arch Linux is so different in this procedure.
Anyway the Important bits here are:
```
 swapon --show
NAME      TYPE SIZE USED PRIO
/swapfile file  10G   0B   -2


``` 
I have 8 Gigs of Ram in this laptop.
Grub has been altered to show a resume option:
IE:
```
resume=UUID="6b660db4-36b8-49b7-bc9c-1e5d2aac2c23resume_offset=1492992"
```
or as a whole:
```
cat /etc/default/grub
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="EndeavourOS"
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 nowatchdog nvme_load=YES nvidia-drm.modeset=1  apparmor=1 security=apparmor ipv6.disable=1 i2c-hid.polling_mode=1 resume=UUID="6b660db4-36b8-49b7-bc9c-1e5d2aac2c23resume_offset=1492992" quiet"
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Set to 'countdown' or 'hidden' to change timeout behavior,
# press ESC key to display menu.
GRUB_TIMEOUT_STYLE=menu

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
#GRUB_COLOR_NORMAL="light-blue/black"
#GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
#GRUB_BACKGROUND="/path/to/wallpaper"
#GRUB_THEME="/path/to/gfxtheme"
GRUB_THEME=/boot/grub/themes/EndeavourOS/theme.txt

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

# Uncomment to make GRUB remember the last selection. This requires
# setting 'GRUB_DEFAULT=saved' above.
#GRUB_SAVEDEFAULT=true

# Uncomment to disable submenus in boot menu
GRUB_DISABLE_SUBMENU=y

# Probing for other operating systems is disabled for security reasons. Read
# documentation on GRUB_DISABLE_OS_PROBER, if still want to enable this
# functionality install os-prober and uncomment to detect and include other
# operating systems.
#GRUB_DISABLE_OS_PROBER=false

# To enable usage of os-prober, set GRUB_DISABLE_OS_PROBER to 'false'.
# Note: enabling os-prober creates a potential security risk!
# More info: https://www.gnu.org/software/grub/manual/grub/grub.html
GRUB_DISABLE_OS_PROBER=true

```
There was another modifier in **" /etc/mkinitcpio.conf"** to add the "**resume**" and then a rebuild of  "**mkinitcpio**"
as:
```
sudo mkinitcpio -p linux
```
For the OP, You may want/need to create and enable a swap file on your machine.  Many Linux distribution installers will create an extra partition for swap.  However, there are several advantages to simply using a swap file on your root partition (the partition you installed Linux on).  Here's a few:
[list]
    [*]you can increase / decrease it's size much easier than resizing partitions;
    [*]if you use LUKS for encrypting your root partition, then you either have to encrypt your swap partition to maintain security (swap can contain sensitive information that is exploitable) or you can simply use a swapfile on your root partition (which is then encrypted along with everything else on the root partition);
    [*]If you encrypt your root partition AND your swap partition, then you will need to enter two decrypt passphrases (one for root and one for your swap partition) unless you also mount your LUKS swap partition with a keyfile (in which case you'll need to edit /etc/fstab and /etc/cyrpttab) - for a swapfile you don't have to worry about any of that;[/list]
So I don't feel as if I hijacked his thread.. :D

---

### Post by ne29914 on 2022-09-16
I'm not convinced. 
Changing a line in grub from:
resume=UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23     (which is your swap partition)
to:
resume=UUID="6b660db4-36b8-49b7-bc9c-1e5d2aac2c23resume_offset=1492992"
Doesn't create a swapfile and enable hibernation IMO. But I may be wrong.

I'm still waiting for a credible demonstration that a swapfile works for hibernation (not from you personally, but from all over the web).
I can make a video demonstrating my hibernate functionality (using a swap partition), if someone will make one showing hibernation with a swapfile.

But I'm totally with your golden rule of "if it ain't broke, don't fix it". It's my rule as well. :)

---

### Post by #&amp;thj^% on 2022-09-16
> **ne29914 said:**
> I'm not convinced. 

It's not my job to convince you of anything, nor could I.
> **ne29914 said:**
> 
resume=UUID=6b660db4-36b8-49b7-bc9c-1e5d2aac2c23     (which is your swap partition)
to:
resume=UUID="6b660db4-36b8-49b7-bc9c-1e5d2aac2c23resume_offset=1492992"
Doesn't create a swapfile IMO. But I may be wrong.

I'm still waiting for a credible demonstration that a swapfile works for hibernation.


This thread is not the place for me to show how I did/do on Arch....The OP is on Ubuntu "On Topic"
I guess you could fly over and lay your own eye's on it..:P
> **ne29914 said:**
> 
Changing a line in grub from;
Doesn't create a swapfile IMO. But I may be wrong.


No your not wrong, this creates the swapfile:
```
sudo fallocate -l 10G /swap
sudo chmod 600 /swap
sudo mkswap /swap
sudo swapon /swap
```

---

### Post by ne29914 on 2022-09-16
Sorry, I seem to be threadjacking here. Apologies. I have a spare machine, I'll try it out.

Cheers.

---

### Post by #&amp;thj^% on 2022-09-16
> **ne29914 said:**
> Sorry, I seem to be threadjacking here. Apologies. I have a spare machine, I'll try it out.

Cheers.
Thanks, we all get caught up in thread from time to time. ;)
This could help the OP as well as you:[https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html](https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html)

---

### Post by TheFu on 2022-09-16
> **xeddog said:**
> What are the pros/cons of adding swap partitions???

Wayne

There was a long thread in these forums, I think around June 2020 or June 2021 about swap recommendations.  There's no easy answer. Sorry.  It depends on the hardware, workloads and how a system is used.

For desktop installs, I think there is 1 answer for swap - 4.1G.  Period.  This assumes not hibernation.  Standby, which I use all the time, doesn't care about swap size.

For servers, things are more complicated.  The current recommendation is that "some swap" be enabled for performance reasons. The size depends on many factors.  If the system has plenty of RAM that would never be used, perhaps 500MB swap is sufficient.  OTOH, if the server is for web hosting and has 3000+ webdomains and the goal is to over abuse the CPU and RAM to make customers pay for upgraded servers+support, then perhaps having 128GB of RAM with 256GB of swap would be desired to make the customers feel the need to get a faster, more expensive plan.  Just depends on the needs.

I never use swap files.  I use swap partitions or logical volumes for swap.

There are some features that do not work with a swap file. I'll leave that do you for research. It may or may not matter at all.  IDK.

Here's an example on a 22.04 server:
```
$ lsblk 
NAME                MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
vda                 252:0    0   15G  0 disk 
&#9500;&#9472;vda1              252:1    0    1M  0 part 
&#9500;&#9472;vda2              252:2    0  768M  0 part /boot
&#9492;&#9472;vda3              252:3    0 13.2G  0 part 
  &#9500;&#9472;vg--00-lv--0    253:0    0   10G  0 lvm  /
  &#9492;&#9472;vg--00-lv--swap 253:1    0    1G  0 lvm  [SWAP]

```

The /etc/fstab looks like this:
```
/dev/vg-00/lv-0 / ext4 defaults 0 1
/dev/vg-00/lv-swap none swap sw 0 0
UUID=59ab80e1-0dc0-4d67-81f0-b62f14ef50dd /boot ext4 defaults 0 1
```
That system is using LVM.

```
$ swapon -s
Filename                                Type            Size            Used            Priority
/dev/dm-1                               partition       1048572         0               -2

$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       153Mi       1.6Gi       3.0Mi       206Mi       1.6Gi
Swap:          1.0Gi          0B       1.0Gi

```
As you can see, the server has too much RAM assigned for the workload. Looks like the swap is 2x too large as well.  Your system will be different, I'm certain. That is a very minimal server that I use as a toy.  22.04 is too new for production, IMHO.

---

