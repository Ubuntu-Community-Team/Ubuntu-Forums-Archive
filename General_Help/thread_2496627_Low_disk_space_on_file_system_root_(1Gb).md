---
title: "Low disk space on file system root (1Gb)"
date: 2024-04-05
forum: General Help
---

### Post by Panawe on 2024-04-05
Hi,
I'm getting this message regularly. What can I do about it?
TIA
Phil

---

### Post by #&amp;thj^% on 2024-04-05
Loaded question here.
have you checked your /boot space?
```
 df -Th | grep /boot

```
Or just show 
```
df -Th
```

---

### Post by dragonfly41 on 2024-04-05
Today I was experimenting with screencasting in kazam and noticed later that my available diskspace had dropped dramatically. I applied disk usage and found that a test screencast (video) had continued growing in size and had gobbled up 300GB or so. Any errant background processes running? I use Stacer as resource monitoring tool.

---

### Post by #&amp;thj^% on 2024-04-05
> **dragonfly41 said:**
> Today I was experimenting with screencasting in kazam and noticed later that my available diskspace had dropped dramatically. I applied disk usage and found that a test screencast (video) had continued growing in size and had gobbled up 300GB or so. Any errant background processes running? I use Stacer as resource monitoring tool.

I've seen users with Audacious and Record set auto On do the same. It dose grab your attention though :)

---

### Post by Panawe on 2024-04-05
Hi,

> Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     1.4G  2.2M  1.4G   1% /run
/dev/nvme0n1p5 ext4      480G  455G  1.1G 100% /
tmpfs          tmpfs     6.8G     0  6.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
efivarfs       efivarfs  128K   14K  110K  11% /sys/firmware/efi/efivars
/dev/nvme0n1p1 vfat       96M   35M   62M  36% /boot/efi
tmpfs          tmpfs     1.4G  136K  1.4G   1% /run/user/1000
/dev/sdb1      ntfs3     3.7T  456G  3.2T  13% /media/phil/My Passport
/dev/nvme1n1p1 ntfs3     932G  489G  443G  53% /media/phil/Godown1



Does this help?
P

---

### Post by #&amp;thj^% on 2024-04-05
This is better:
```
Filesystem Type Size Used Avail Use% Mounted on
tmpfs tmpfs 1.4G 2.2M 1.4G 1% /run
/dev/nvme0n1p5 ext4 480G 455G 1.1G 100% /
tmpfs tmpfs 6.8G 0 6.8G 0% /dev/shm
tmpfs tmpfs 5.0M 4.0K 5.0M 1% /run/lock
efivarfs efivarfs 128K 14K 110K 11% /sys/firmware/efi/efivars
/dev/nvme0n1p1 vfat 96M 35M 62M 36% /boot/efi
tmpfs tmpfs 1.4G 136K 1.4G 1% /run/user/1000
/dev/sdb1 ntfs3 3.7T 456G 3.2T 13% /media/phil/My Passport
/dev/nvme1n1p1 ntfs3 932G 489G 443G 53% /media/phil/Godown1
```

Your problem is "/dev/nvme0n1p5 ext4 480G 455G 1.1G 100% /" you need to remove some un-needed stuff.

---

### Post by dragonfly41 on 2024-04-05
> [COLOR=#000000][I]/dev/nvme0n1p5 ext4 480G 455G 1.1G 100% /

The 100% level grabs my attention.[/I][/COLOR]

---

### Post by Dennis N on 2024-04-05
Have you checked the size of the journal recently? Removing old entries can recover a GB or more of space, depending on how long they have been accumulating.
**sudo journalctl --vacuum-size=20M**
retains the most recent 20MB and deletes the rest.

---

### Post by MAFoElffen on 2024-04-05
Just me but... Your second 1 TB M.2 drive...

If it were me, I would shrink that NTFS partition to 500GB for Windows storage and add a Linux partition to mgrate your home to.

Just an idea for shifting the resources you already have. An easy fix. I would probably use a Volume Manager such as LVM or ZFS... so that if that later runs into space issues, you could then add more disk, and grow it live, with ease.

But then again, that's just me, and what I would do.

If you had some money, then migrate to larger m.2 cards. 2 TB M.2 is as cheaper now those those 1 TB drives probably were when they were new. For a bit more, 4 TB cards. Then there is always adding SSD's...

This old Lenovo Thinkpad has 6TB of SSD storage... I can currently max out at 10 TB internally. 18 TB (2 x 8TB drives + 2TB mSATA) if I won the Lotto. 8 TB SSD's are around $500 currently. 

Again, if you have or add a Volume Manager, adding storage becomes much more easy.

---

### Post by yancek on 2024-04-06
Unless you have installed massive amount of software, you have likely been mucking about with system files and have massive log files so in addition to the suggestions above, go to the /var/log directory and check the size of various log files.  You can use the commands below to get sizes using a terminal with the first command size in kb and the second mb.:

```
ls -lh /var/log
ls -l /var/log --block-size=M

```

---

### Post by Panawe on 2024-04-06
Thanks. Much to think on.
P

---

### Post by dragonfly41 on 2024-04-06
Final tip.
Recently I  had to get rid of unwanted file (see post #3) and I found that Disk Usage Analyser (go to Activities in top bar and search Disk Usage Analyser) gave a helicopter graphic view of disk usage.

---

### Post by Panawe on 2024-04-07
Have cleared away some space, principally photos.
> Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     1.4G  2.2M  1.4G   1% /run
/dev/nvme0n1p5 ext4      480G  376G   80G  83% /
tmpfs          tmpfs     6.8G     0  6.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
efivarfs       efivarfs  128K   14K  110K  11% /sys/firmware/efi/efivars
/dev/nvme0n1p1 vfat       96M   35M   62M  36% /boot/efi
tmpfs          tmpfs     1.4G  152K  1.4G   1% /run/user/1000
/dev/sdb1      ntfs3     3.7T  457G  3.2T  13% /media/phil/My Passport

Looks better now.

P

---

### Post by yancek on 2024-04-07
My / and /home partitions combined on Ubuntu 20.04 which I have been using for nearly 4 years are a total of 120GB and I have used 70GB so 376GB seems large to me but then I don't know what you use the computer for.  Did you review the /var/log directory?

---

### Post by Tadaen_Sylvermane on 2024-04-07
```

/dev/nvme0n1p5 ext4 480G 455G 1.1G 100% /
```

Am I the only one seeing 24gigs missing here? Should have 24+ free space. not 1.1. And either way it wouldn't show 100%. The math is off.

---

### Post by Impavidus on 2024-04-08
5% is reserved for root, so not used, but not available either. You can change that (read **man tune2fs** for details), but I don't think you'll gain a lot. After you filled the first 95%, it will take less than 5% extra time to fill the final 5%, so you don't gain a lot of time. And on a nearly full drive, fragmentation becomes an issue on spinning drives and SSDs can't use their wear levelling as effectively.

---

### Post by Panawe on 2024-04-08
Hi,
Okay, here's what I saw...
> alternatives.log        bootstrap.log    lastlog
alternatives.log.1      btmp             openvpn
alternatives.log.10.gz  btmp.1           private
alternatives.log.11.gz  cups             speech-dispatcher
alternatives.log.12.gz  dist-upgrade     sssd
alternatives.log.2.gz   dmesg            syslog
alternatives.log.3.gz   dmesg.0          syslog.1
alternatives.log.4.gz   dmesg.1.gz       syslog.2.gz
alternatives.log.5.gz   dmesg.2.gz       syslog.3.gz
alternatives.log.6.gz   dmesg.3.gz       syslog.4.gz
alternatives.log.7.gz   dmesg.4.gz       syslog.6.gz
alternatives.log.8.gz   dpkg.log         syslog.7.gz
alternatives.log.9.gz   dpkg.log.1       ubuntu-advantage-license-check.log
apport.log              dpkg.log.10.gz   ubuntu-advantage.log
apport.log.1            dpkg.log.11.gz   ubuntu-advantage.log.1
apport.log.2.gz         dpkg.log.12.gz   ubuntu-advantage.log.2.gz
apport.log.3.gz         dpkg.log.2.gz    ubuntu-advantage.log.3.gz
apport.log.4.gz         dpkg.log.3.gz    ubuntu-advantage.log.4.gz
apport.log.5.gz         dpkg.log.4.gz    ubuntu-advantage.log.5.gz
apport.log.6.gz         dpkg.log.5.gz    ubuntu-advantage.log.6.gz
apport.log.7.gz         dpkg.log.6.gz    ubuntu-advantage-timer.log
apt                     dpkg.log.7.gz    ubuntu-advantage-timer.log.1
auth.log                dpkg.log.8.gz    ubuntu-advantage-timer.log.2.gz
auth.log.1              dpkg.log.9.gz    ubuntu-advantage-timer.log.3.gz
auth.log.2.gz           faillog          ubuntu-advantage-timer.log.4.gz
auth.log.3.gz           fontconfig.log   ubuntu-advantage-timer.log.5.gz
auth.log.4.gz           gdm3             ubuntu-advantage-timer.log.6.gz
boot.log                gpu-manager.log  unattended-upgrades
boot.log.1              hp               upgrade
boot.log.2              installer        wtmp
boot.log.3              journal          wtmp.1
boot.log.4              kern.log         Xorg.0.log
boot.log.5              kern.log.1       Xorg.0.log.old
boot.log.6              kern.log.2.gz    Xorg.1.log
boot.log.7              kern.log.3.gz
boot-repair             kern.log.4.gz



How do I get rid of unwanted stuff and will it free up much space?

TIA,

P

---

### Post by #&amp;thj^% on 2024-04-08
First show us this:
```
journalctl --disk-usage

```
I could be wrong but that won't free up much space, but lets look at it anyway.

I keep mine to a minimum:
```
sudo journalctl --vacuum-time=2days
Vacuuming done, freed 0B of archived journals from /run/log/journal.
Vacuuming done, freed 0B of archived journals from /run/log/journal/5f12c73bd21a42279c3811f11d1ce4b0.

```
Lets see that before moving on to other stuff.

EDIT: Please use Code Tags instead of Quote Tags much easier to read.
[noparse]```
your copied text here
```[/noparse]

---

### Post by Panawe on 2024-04-08
Hi,

> Archived and active journals take up 64.0M in the file system.

Doesn't look like very much if I'm understanding it right.
P

---

### Post by Panawe on 2024-04-08
Hi,

> Vacuuming done, freed 0B of archived journals from /var/log/journal.
Deleted archived journal /var/log/journal/1ab3cf13bd0b4a85bf97e6d64bdb84ad/user-1000@b72f7dcde81d42228135022bc39b9a38-00000000006632e5-0006155aabe09971.journal (16.0M).
Deleted archived journal /var/log/journal/1ab3cf13bd0b4a85bf97e6d64bdb84ad/system@0006155ef58c767d-d2a3417b5eae88c3.journal~ (8.0M).
Deleted archived journal /var/log/journal/1ab3cf13bd0b4a85bf97e6d64bdb84ad/system@68cb26ee16b34537b6141cea3990066e-0000000000000001-0006155ef58ac2f2.journal (24.0M).
Vacuuming done, freed 48.0M of archived journals from /var/log/journal/1ab3cf13bd0b4a85bf97e6d64bdb84ad.
Vacuuming done, freed 0B of archived journals from /run/log/journal.

P

---

### Post by #&amp;thj^% on 2024-04-08
That's what I thought....
Now we look in your home directory:
```
find -type f -exec du -Sh {} + | sort -rh | head -n 10

```

---

### Post by Panawe on 2024-04-08
Hi,

I am thinking of getting a 2Tb SSD to replace the 1Tb primary one I have. Is there and easier way to accomplish this rather than having to reinstall Ubuntu and Windows on the new drive?

P

---

### Post by #&amp;thj^% on 2024-04-08
Not if you want a clean install and minimal left over cruft.

How is your back-up plan? Do you have one?

Or when the drive arrives just transfer over your bigger files to that new drive.

There is a lot of planing to do before you decide which way you want to proceed. :)

---

### Post by Panawe on 2024-04-08
Hi,
Yes, although I'm not super competent around Ubuntu I have compartmentalised stuff that is personal apart from the machinery of the OS. 
From memory I need to copy my Home folder and the thunderbird folder over to my secondary SSD.
P

---

### Post by TheFu on 2024-04-09
Cough ... having 1 huge partition for everything isn't very "linux-like".
```
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1                          disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M  339.8M    42%                /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 [COLOR="#008000"]35G   24.9G    22%                /[/COLOR]
  &#9500;&#9472;vg01-var01                   lvm   ext4                 [COLOR="#008000"]20G   14.1G    23%                /var[/COLOR]
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.6G     1% tmp01          /tmp
  &#9492;&#9472;vg01-home01                  lvm   ext4                 20G   10.1G    44% home01         /home
``` 

See how I split up where things belong and limit sizes for different parts of the OS - /, /var, /tmp, /boot?  The OS really shouldn't need to be over 35GB total.  Keep the OS separate from personal files to limit risks and make updates easier in the future.  I use LVM for added flexibility without needing lots of partitions.

I didn't show the full use of my NVMe storage to keep things simple, but it is a 1TB disk and I've allocated under 100G for normal use.  The OS are, /, is 35G, but I'm only using about 10GB for it.

I like clean OS partitions.  Makes upgrades and fresh installs safer.

---

### Post by Panawe on 2024-04-10
Hi,
It looks very neat but I've no idea how to achieve that starting from where I am. Do you mean if (or when) I install a new primary SSD?
Thanks anyway.
P

---

### Post by TheFu on 2024-04-10
> **Panawe said:**
> Hi,
It looks very neat but I've no idea how to achieve that starting from where I am. Do you mean if (or when) I install a new primary SSD?
Thanks anyway.
P

You can do partitioning stuff now or with a new install.  Which is easier depends on your skills.

In storage, there are OS areas and there are Data areas.  They should be separate, on different file systems.  If you have a second HDD/SSD, move the Data areas, including /home/, off the main OS SSD, then reduce the OS partition size to be under 100GB.  Smaller is better, but some people like to load thousands of fat, GUI, programs without regard for how many dependencies or if they are flatpak, snaps, appimage or some other sort of paging.  I'm fairly certain someone else,  MAFoElffen, recommended this already.  Just be certain to keep native Linux file systems - don't use NTFS or any file system like exFAT or FAT32.  Those don't work for /home/. 

The only time to actually use NTFS is when the drive/partition will be physically connected to a computer running MS-Windows.  Linux doesn't need it.  If you want to share the storage with other computers over the network, stick with native Linux file systems too.  Samba/CIFS works great on a Linux server when the storage file systems are native Linux.  Plus, with native Linux file systems, if anything happens, you don't have to hunt down an MS-Windows computer to fix non-Linux file systems, like NTFS or exFAT or FAT32.

Data areas for most people are in /home/ and under /media/.  Every other top level directory typically is part of the OS or OS-settings.  Best to leave the OS stuff alone.  There are exceptions, but those exceptions would have needed manual intervention by the admin of the system. If you are the admin and didn't do that, then what I've said in this paragraph covers you too.  /home/ and /media/ are the only places for "Data" on your computer for 90+% of Ubuntu Desktop users.

There's a wiki.ubuntu.com article for how to accomplish moving the HOME directories.  It isn't hard, but attention to details for everything **is** required.  Some guides that google found:
[LIST]
[*][https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[*][https://askubuntu.com/questions/21321/move-home-folder-to-second-drive](https://askubuntu.com/questions/21321/move-home-folder-to-second-drive)
[*][https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/](https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/)
[*][https://askubuntu.com/questions/239843/moving-home-user-directory-to-another-drive](https://askubuntu.com/questions/239843/moving-home-user-directory-to-another-drive)
[*][https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/](https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/)
[/LIST]

I think all those websites are reputable.  

BTW, moving everything in my nvme0n1**p4** PV to a different disk can be performed while the system is running and being used thanks to LVM.  Or I can move each LV one at a time, but that's actually harder.  **pvmove** is an amazing command, but only available if LVM was setup at install time.  You can choose LVM or not LVM. The way to deal with things change if LVM is involved.  LVM provides flexibility, so I don't need to guess the correct sizes for each LV/partition in the beginning. Adding more storage to a specific LV from a VG that isn't already fully allocated is about 5 seconds of work in 1 command.  Extremely flexible.  LVM has been used by enterprises running Linux since the late 1990s. It is extremely solid.  However, LVM's flexibility does come with some added complexities during the creation and setup.  It is fine if you want to avoid those complexities.  I did for my first 6 yrs running Linux.

The defaults for storage setup in Ubuntu installers is pretty poor, IMHO.  They simplify it so people coming from another OS don't freak out.  More advanced users would know how to setup their storage for maximum flexibility and expansion where needed. I guess that's the assumption of the people creating the storage setup part of the installers.  I setup my storage outside the installer, then just hook up the different parts where I need them and have the installer create file systems on each LV device.  

Just by having your /, swap and /home separate, you'll get lots of benefits.  That's my minimal recommendation for people committed to Linux.  For people just test driving it for a few months, the single partition, 1 partition method is fine ... until they outgrow it.  I think you've outgrown it.

See attachment. Ignore the LUKS/encryption part. If you don't use it, nothing much changes in the diagram - just 1 extra storage object/container is removed. Also, that diagram shows an MBR/DOS partition table.  Today we should all be using GPT instead on our Linux systems. GPT is better for a few reasons, but only worth forcing at new install time.  I wouldn't convert from MBR to GPT unless I was wiping the disk for some other reason.

---

### Post by Panawe on 2024-04-10
Thanks for this.
I shall now go and study your post.
P

---

### Post by TheFu on 2024-04-10
I forgot to mention one other method to move lots of files files for a single user outside /home/{USER} to a different disk+file system.  Lots of the Gurus in these forums do it this way.  On the other disk, they setup a data area for each user and make subdirectories that map to their $HOME/Documents

```
$ tree -d --dirsfirst  $HOME |egrep '^&#9500;&#9472;'
&#9500;&#9472;&#9472; bin
&#9500;&#9472;&#9472; Desktop
&#9500;&#9472;&#9472; Documents
&#9500;&#9472;&#9472; Downloads
&#9500;&#9472;&#9472; mail
&#9500;&#9472;&#9472; Music
&#9500;&#9472;&#9472; NextCloud
&#9500;&#9472;&#9472; PDF
&#9500;&#9472;&#9472; perl5
&#9500;&#9472;&#9472; Pictures
&#9500;&#9472;&#9472; Presentations
&#9500;&#9472;&#9472; Videos

```

Each of those directories would be **moved** to the new storage .... probably mounted under /media/newHDD/{username}/   or at least accessible to the top level for each user in that way, then symbolic links from 
/media/newHDD/Panawe/Documents ---> ~/Documents would be created.  Same for all the other, larger, directories.  Moving is important, since if you just copy, then you won't be able to create a symbolic link back inside ~/ (directory exists already).  Be certain if you do this, that you do it for all the different users and that you backup the storage in  /media/newHDD/ ...   Backup software will capture the symbolic link, but it won't follow it to the other location - that's called "dereferencing", if you care.

You can learn more about **symbolic links** here:  [https://en.wikipedia.org/wiki/Symbolic_links](https://en.wikipedia.org/wiki/Symbolic_links)  - these are also called *symlinks* or *soft-links*.  They are all the same, just different names.

Don't confuse a symlink with a hard-link.  That's a different thing and can be very useful if used appropriately.  [https://en.wikipedia.org/wiki/Hard_link](https://en.wikipedia.org/wiki/Hard_link)  Hardlinks are used by some Unix backup software to handle versioning in a more efficient way.

BTW, these different types of links have been part of Unix at least 40 yrs, perhaps longer. It is common to see both types.  I understand that MSFT added symlinks to NTFS around 2011, but I've been out of the MSFT world and have never seen anyone actually use them.  I to remember MSFT trying to setup "Libraries" in the early 2000s, but those were only for GUI programs, not part of the file system, so they didn't actually work everywhere.  Sigh.

Anyway, probably more than you care to know.

---

### Post by dragonfly41 on 2024-04-10
Everybody has their own ways and budgets to work with.
Some time ago I decided to distance Ubuntu from my primary Dell PC containing Windows 10. I started the learning process by running Ubuntu in a resized partition in internal drive with Windows in co partition.
I then purchased a StarTech dual docking bay, USB 3.0 connector, with own power supply. in fact I have a second one for grabbing data from old drives such as laptops.
[https://www.startech.com/en-gb/search?search_term=dual%20docking%20bay](https://www.startech.com/en-gb/search?search_term=dual%20docking%20bay)
U.K.suppliers are here:
[https://www.startech.com/en-gb/where-to-buy](https://www.startech.com/en-gb/where-to-buy)
Farnell and CPC are good.   Crucial for SSD purchase.
The bottom line is I keep two SSD's in pluggable caddies separately bootable.
The plugin caddy containing each SSD is IcyDock EZC Convert 2.5" to 3.5" SAS/SATA SSD & HDD Converter MB882SP-1S-1B.
This all comes at a price and not for everybody but I value the flexibility and separation of Windows and Ubuntu. And I can unplug a caddy and lock it away if needed.
Because I have multiple boots I installed rEFInd as my default boot option.

---

### Post by vrendtop on 2024-04-11
[COLOR=#000000]Thanks. Much to think on.[/COLOR]

---

### Post by MAFoElffen on 2024-04-11
+1 with TheFu on separating things out into organized storage spaces. A place for things to be, where you can find them... And where they can be moved easily during a migration.

I separate out OS, Home (personal files), and data. For my Gaming PC, I also separate out game files, and downloads. I do this in a way, that these are "portable"... meaning that they are in a storage container where if I reinstall, or install a newer version of the OS, they are not affected, and can be mounted, and added back into that OS, with little work.

Making my computers filesystems this way, things are easier down the road, over they years.

I was going to mention, as a rule of thumb, like TheFu, we both do not allocate all our allocatable space at one time. We allocate what we think we need, then add more to it as we use it. We both use Volume Managers, so that we can easily do that when the time for that comes. I like to keep my "Used space, less than 80% of the file storage container. Filesystems run faster and more dependably that way. 

On another note, Noble 24.04 LTS gets released in a few weeks... If you plan to do a do-release-upgrade, you will need run free, for that to happen. Depending on what you have installed beyond the basic OS, will affect how much room you will need for that to happen successfully.

Next... On your system, you didn't make any mention of your use of backups, or if you even have a backup strategy that you are using. That is always a good idea. People usually don't think about that, until they are making changes and something happens. Then that afterthought is too late. Think about what you can afford to lose, or what doesn't matter.

Yes. You have some thinking to do.

---

### Post by dragonfly41 on 2024-04-11
And the backup should be on at least one other separate medium such as another SSD or HDD. One reason I opted for separate pluggable caddies. Study n+1 redundancy reliability methods. Your PC might be hit by a flood. So ideally distribute backups (although I don't practice that policy myself).

---

### Post by TheFu on 2024-04-11
I've written far too much in these forums about backups and recovery. Feel free to search if you are interested in a proven, FAST, way to backup.  I wish it were 1-click to backup and 1-click to restore, but it isn't.  

For easy backups and easy restores there are huge trade-offs in how long the backup takes, how long the restore takes, how flexibly the restore process can be and, most importantly, how much storage is required.  Typically, I have 90-180 days of daily backups that require between 50% and 100% more storage than the source files/directories require.  For some, high-risk systems, I have over a year of daily backups and because those systems don't really have any data, the backups are tiny - less than 1GB for 1 yr of daily, versioned, backups.  

Say you only need 100G backed up. Keeping 60 days of daily backup versions would probably need about 130GB total.  Doesn't that sound like a bargain?

Anyway, search and you can find.

---

### Post by Panawe on 2024-04-12
Hi,
Yes, I'm rather paranoid about backups and that is partly the reason I've run short of disk space. I have copied personal files to a number of different places to the extent that I have several copies of stuff.
Thanks to all for your inputs, the rest is up to me.
P

---

### Post by TheFu on 2024-04-12
> **Panawe said:**
> Hi,
Yes, I'm rather paranoid about backups and that is partly the reason I've run short of disk space. I have copied personal files to a number of different places to the extent that I have several copies of stuff.
Thanks to all for your inputs, the rest is up to me.
P

Copying files around is the hard way to do backups.  Things get lost that way. Unnecessary duplication happens.  The true **source of the original** and the copies become confused.  It becomes a mess.  Initially, it is easy. Then you end up for 3 copies that you can't tell which is which 1, 3, 5, yrs later.  Much easier for the long term to have a specific "source" and a specific target area for backups.

I've been doing this a long time.  I made all the mistakes to be made.  I've lost lots of data.  Data has also been saved by accident - pure luck.  Eventually, I learned that a $120 2TB HDD specifically used just for backups would easily hold everything really important for 10-20 systems here.  I think these days, a $45 4TB HDD is about the cheapest for the size needed by most people.

And don't do like so many people do - don't call the disk a "backup".  It is only a "backup", if there is at least 1 other copy somewhere else.  We've all heard of people copying files to their "backup HDD", then deleting it from their laptop.  1 copy on a "backup" disk is NOT a backup.  Additionally, USB HDDs seldom have 5 yr warranties. They usually have 90 day to 1 yr warranties.  The length of a warranty tells us much about the engineering in a disk.  The vendors want to promise as much as they can in the warranty, but not lose money for failures.  That's what controls the warranty they set.  In the world of HDDs, a disk with 5 yrs of warranty is the longest and generally means the device is expected to last 10 yrs, minimal, unless there's a manufacturing defect.

Watch out for disks with 1 yr warranties.  I avoid those completely after being burned too many times.  3 yr warranty HDDs can last 10 yrs, but I've had a few only last 4 yrs.

---

