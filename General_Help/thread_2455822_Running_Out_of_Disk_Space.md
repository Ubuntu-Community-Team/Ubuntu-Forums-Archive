---
title: "Running Out of Disk Space"
date: 2020-12-28
forum: General Help
---

### Post by scottydel on 2020-12-28
New to Ubuntu.  I have a dual boot Windows 10 / Linux Ubuntu machine.  I put Ubuntu on a 25 GB partition on my HD.  I researched and thought this would be more than enough, but after a few months Ubuntu started giving me warnings about disk space.  Ubuntu also doesn't seem to install any updates now due to disk space.  I love using Ubuntu over Windows, but I'm much more familiar with Windows.  I'm a little lost as to why I've used up nearly all of my 24 GB on /dev/sda6, and what I can do to fix it.  I have put on some software, but I didn't think I went too crazy.  Should I start over with more than 25 GB as my Ubuntu partition?  Here is what my $ df -h returns:


```
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  3.6M  1.6G   1% /run
/dev/sda6        24G   23G   59M 100% /
tmpfs           7.8G  688M  7.2G   9% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop1       56M   56M     0 100% /snap/core18/1932
/dev/loop4       65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop5       68M   68M     0 100% /snap/sublime-text/85
/dev/loop2       98M   98M     0 100% /snap/core/10444
/dev/loop7      2.3M  2.3M     0 100% /snap/gnome-system-monitor/145
/dev/loop8      2.5M  2.5M     0 100% /snap/gnome-calculator/748
/dev/loop6      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop11      58M   58M     0 100% /snap/sublime-text/97
/dev/loop12     256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop9      147M  147M     0 100% /snap/code/51
/dev/loop10     384K  384K     0 100% /snap/gnome-characters/550
/dev/loop13     1.0M  1.0M     0 100% /snap/gnome-logs/93
/dev/loop14     2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop15      65M   65M     0 100% /snap/gtk-common-themes/1513
/dev/loop16     384K  384K     0 100% /snap/gnome-characters/570
/dev/loop18     1.0M  1.0M     0 100% /snap/gnome-logs/100
/dev/loop17     162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop19     2.5M  2.5M     0 100% /snap/gnome-calculator/826
/dev/loop21      56M   56M     0 100% /snap/core18/1944
/dev/loop23     218M  218M     0 100% /snap/gnome-3-34-1804/60
/dev/loop22      62M   62M     0 100% /snap/core20/875
/dev/sda1       496M   33M  464M   7% /boot/efi
tmpfs           1.6G   16K  1.6G   1% /run/user/121
/dev/loop24     144M  144M     0 100% /snap/code/52
tmpfs           1.6G   60K  1.6G   1% /run/user/1000
/dev/loop0       62M   62M     0 100% /snap/core20/904
/dev/loop20      98M   98M     0 100% /snap/core/10577
```

---

### Post by GhX6GZMB on 2020-12-28
What sticks out is that you don't have a /home partition.
This means that all your user data (pictures, videos etc.) will be stored on / which is your /dev/sda6

You need to think about how to partition your disk(s).

---

### Post by scottydel on 2020-12-28
I see what you're saying.  I have installed Ubuntu into one 25 GB partition, which has both \root and \home, I think.  I have plenty of space on my hard drive (2 TB).  Can I somehow split out \home into a second, new 25 GB partition, leaving \root intact, or should I just start over and reinstall Ubuntu?

---

### Post by CelticWarrior on 2020-12-28
It is possible to move /home to a separated partition but it's NOT for newbies.

I strongly suggest backing up any personal files you may have in Ubuntu and after that reinstall. Previously you should shrink one or more (Windows) partitions from Windows with Windows native tools to make adequate room for Ubuntu. 

Considering you'll manually partition for the new installation in order to have the separated /home then 25-30GB, maybe some more, is fine for / (root) which then will only have the OS and programs installed there is perfectly fine. Give /home as much as you can afford.

The way you did it before isn't necessarily wrong. Again, 25 GB is enough for the OS and many additional (small) programs. But if that is the same space for your personal files then it depends. I would say that for most typical usages nowadays it's ridiculously small. I have several HD movies each one occupying more than 10GB.

---

### Post by GhX6GZMB on 2020-12-28
I'm 100% with CelticWarrior here.
A reinstall with new partitioning is the way to go. Remember to store your personal stuff first.

I also agree 100% on 25...30 GB for / (on my disk it somehow always works out at 29.3 GB, probably due to the sector sizes).
For /home whatever you think is right. As you have 2 TB, and depending on what your Win partition needs, 500 GB or more wouldn't be bad.

---

### Post by scottydel on 2020-12-28
Good to know it's not for newbies.  I will do as you suggest and reinstall with two partitions, \root and \home.  I think I dumped too many photos/videos/downloads without realizing how much space it was.  Appreciate it!

---

### Post by TheFu on 2020-12-28
Unix uses /, not \. ;)

You have a bunch of snap packages. Those can use more storage than normal, APT packages. Just something to consider.

/root, /, are different things not to be confused.
/root is the HOME directory for the root account.
/ is the "root directory". See the difference?

In general, with newer releases, 25-35G is needed for the OS, especially if you use snaps and allow the swap to be stored inside the / (OS) partition.

Having a separate /home/ would be very useful for many reasons. I think there is a guide to set that up somewhere [https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder).  It must use a native Linux file system. There are many, many, options for all this stuff.

May want to have a separate swap partition as well.  Older disk sizing guides wold all assume a separate swap. That only changed recently. Some people are fine with it. I'm old school and prefer a separate swap.

---

### Post by Impavidus on 2020-12-29
I think moving a home directory to a separate partition isn't that hard. I expect many, although maybe not all, newbies to be able to follow this guide: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
I think you can ignore the final section. I've never encountered that problem. But the occasional **sudo gedit [filename]** command in there is not so proper, although I think it should be relatively safe if you're on 20.04 or newer. The proper way to edit files as root is using```
sudoedit [filename]
```which will allow you to edit the file with the nano text editor (unless you configured something else), which you may not be used to. Key commands are listed at the bottom of the screen, ^X means ctrl-x, etc.

Use Windows tools to edit Windows partitions, use Linux tools to edit Linux partitions.

BTW, have you got backups of all your important files on a removable drive? Reinstalling and partitioning are high-risk operations, so you may lose files if you make some error of suffer a power failure. Having backups is a good idea anyway, as hard drive failures happen.

---

### Post by rsteinmetz70112 on 2020-12-29
I agree that creating anew /home isn't that hard and I think the process in the linked article is more complicated that it needs to be. At least the way I'd do it seems simpler to me.

---

### Post by TheFu on 2020-12-29
> **rsteinmetz70112 said:**
> I agree that creating anew /home isn't that hard and I think the process in the linked article is more complicated that it needs to be. At least they way I'd do it seems simpler to me.

There are lots a tiny steps, each can be very confusing to someone new to Linux CLI ideas, and things that we take as automatic knowledge/skills just aren't part of MS-Windows learning.  Things like:
[LIST]
[*]file systems - need to pick the correct one and create it inside a partition ... or LV or ZFS pool
[*]mounting file systems to multiple places - a temporary location first to copy/move everything into, then the real location later.
[*]setting correct directory ownership and permissions. Get this wrong and it is a bad day.
[*]modifying system files like the /etc/fstab, correctly.
[*]setting mount directory levels exactly correct. Many MS-Windows people never learned relative vs absolute paths and directories, adding to the confusion.
[*]If the new file system will be placed somewhere other than /home/, then snap programs will break, which makes hassles for new people who aren't certain what should and shouldn't work.
[/LIST]

Get any of these details and decide that rebooting will fix it and the userid probably won't be able to login at all. A simple, minor change, for an expert becomes an ordeal and reinstall everything problem for someone else.

More tiny details than experts would worry about, but nearly insurmountable for someone new to Unix/Linux.  Doing this would take you or me less than 3-5 minutes, but someone else may need a few days to look up each command. I'm not saying I'd get each command perfect the first time, but I would recognize any issues quickly and be able to recover from those is very little problem.

---

### Post by ActionParsnip on 2020-12-29
If you uninstall some old kernels it'll free up space to give you some wiggle room

---

### Post by Dennis N on 2020-12-29
You are forgetting the systemd journal. Depending on how long your OS has been installed, you can sometimes find disk space used by the journal has grown to several gigabytes!

Here's an example: I just now checked this Ubuntu 18.04 I am using, and find the journal is using 1.1G of disk space!
```
dmn@Sydney:~$ journalctl --disk-usage
Archived and active journals take up 1.1G in the file system.

```
I can reduce it to approximately 100 megabytes by:
```
dmn@Sydney:~$ sudo journalctl --vacuum-size=100M
Vacuuming done, freed 1.0G of archived journals...
```
Check new usage:
```
dmn@Sydney:~$ journalctl --disk-usage
Archived and active journals take up 104.0M in the file system.

```
The size and other parameters of the journal can be controlled through it's configuration settings.

---

### Post by TheFu on 2020-12-29
> **Dennis N said:**
>  The size and other parameters of the journal can be controlled through it's configuration settings.

I didn't know those commands. Thanks!
The /etc/systemd/journald.conf controls how large the logs are allowed to get.  The manpage for journald.conf spells out the details for each setting. I use something like this:
```
[Journal]
Storage=persistent
SystemMaxFileSize=500M
SystemMaxFiles=10
```
to ensure they aren't temporary and wiped with each boot. Should anything go wrong, it is hard to troubleshoot when all the logs are gone.

---

### Post by #&amp;thj^% on 2020-12-29
> **Dennis N said:**
> You are forgetting the systemd journal. Depending on how long your OS has been installed, you can sometimes find disk space used by the journal has grown to several gigabytes!

I can reduce it to approximately 100 megabytes by:
```
dmn@Sydney:~$ sudo journalctl --vacuum-size=100M
Vacuuming done, freed 1.0G of archived journals...
```


I had added that to bleachbit  {Custom}a while back. :)

For safety i should add you don't typically clear the journal yourself. That is managed by systemd itself and old logs are rotated out as new data comes in. The correct thing to do would be to schedule journald to only keep as much data as you are interested in. The most usual thing to adjust is the total disk space it is allowed to take up. Once it crosses this boundry it will start pitching old entries to stay near this value.

You can set this in /etc/systemd/journald.conf like so:

```
SystemMaxUse=100M
```

---

### Post by guiverc on 2020-12-29
Just an FYI, but 25GB is the minimum recommended for Ubuntu Desktop

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You need [unused] space come *release-upgrade* time, which is something bloggers don't worry about generally, as they write their article, then *hop* *to* (*nuke & install*) their next distro so are starting again.  Their audience usually is someone who is only going to play/try with the system, and not actually use it for serious work (users who are trying something usually need less space than workers using it)

---

### Post by #&amp;thj^% on 2020-12-29
> **guiverc said:**
> Just an FYI, but 25GB is the minimum recommended for Ubuntu Desktop

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You need [unused] space come *release-upgrade* time, which is something bloggers don't worry about generally, as they write their article, then *hop* *to* (*nuke & install*) their next distro so are starting again.  Their audience usually is someone who is only going to play/try with the system, and not actually use it for serious work (users who are trying something usually need less space than workers using it)

Been Waiting for someone to state this, you did it very nicely.
I always get taken as grumpy or snaarky...;)

---

### Post by TheFu on 2020-12-29
> **1fallen said:**
> Been Waiting for someone to state this, you did it very nicely.
I always get taken as grumpy or snaarky...;)

We can be both?  I have a goal! ;)

25G seems new since 20.04, waz it always that large? Until 20.04, my desktops easily fit in 15-20G total.  With 20.04, I ended up adding more storage - using 30G now with 10G as spare.
```
$ df -Th                            # with lots of junk removed
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G   11G  5.0G  69% /
/dev/mapper/vgubuntu--mate-home ext4   12G  7.6G  3.6G  69% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi

```
Sorry that I use LVM and not straight partitions.  Just consider the 1st column of stuff as partitions.

---

### Post by guiverc on 2020-12-29
> **TheFu said:**
> 25G seems new since 20.04, waz is always that large? Until 20.04, my desktops easily fit in 15-20G total. ..

It was changed to 25GB prior to artful/17.10's release.  Ubuntu 17.04 was the last release with a smaller recommended size ([changed by Will Cooke; update for GNOME Shell]("https://help.ubuntu.com/community/Installation/SystemRequirements?action=recall&rev=108"))

The size required depends on use... my /  is 27gb, and I have separate /home & swap partitions so don't use a swap file, but regularly have to fight *disk full issues* & wish I had a 32gb partition...  Our needs will depend on how lean we run our desktops (or how *bloated* in my case; having multiple desktops installed).

---

