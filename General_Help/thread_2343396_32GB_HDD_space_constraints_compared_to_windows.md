---
title: "32GB HDD space constraints compared to windows"
date: 2016-11-15
forum: General Help
---

### Post by tl120002 on 2016-11-15
Hi There.

I have been wondering about how ubuntu and linux in general can counteract the constraint issues faced with low HDD space.

In windows for example, i can change system variables like temp directories, etc to another expandable storage and have program files installed in a specified directory.
This essentially allows me to keep the base system windows on a small HDD space and have everything else on a second expandable storage drive.

What is the equivalent of environment system variables in ubuntu?

---

### Post by jerome1232 on 2016-11-16
In Linux the filesystem hirearchy works a bit different.

You have the top level at /, this is the root of your file system.

under that you have directories like 

/usr  -- for user programs
/bin -- user binaries
/sbin -- system binaries
/etc -- configuration files
/dev -- devices (yes, your devices are a part of the file system, like your first hard drive is at /dev/sda)
/home -- users home directories

and a lot more... you can mount partitions under the root directory. For example on my system I have a ssd, a 2 tb drive, and an old 300 gb drive that I'm simply too lazy to remove. I mount the ssd at /, and the 2 tb at /home. This way all system stuff is on the ssd, all of my user files are on the large 2 tb disc (all your personal files are in /home).

---

### Post by oldfred on 2016-11-16
I keep /home inside / (root) and use 25GB for / on SSD. And actually use 10 to 12GB of that.
But I have all my data in a ext4 formatted /mnt/data partition on HDD. But I have multiple installs of Ubuntu and want to be able to use the same data in all of them.

Back when I had XP, I also keep XP smaller and used a large NTFS data partition for sharing most data. As I weaned myself off Windows less data was in the NTFS data partition and more in the ext4 data partition.

---

### Post by tl120002 on 2016-11-16
Awesome thanks, thats what im looking for. Im going to mount the base system on 32GB and mount everything else on another drive.

Quick question, whats the difference between "User programs" and "User binaries"? I understand both binaries and programs are....well......programs....
If i were to mount /usr and /bin on another drive, will programs i install from repositories immediately recognize that and move to the respective drive (/dev/sda) on their own? Or do i have to specify somewhere for them to install?

---

### Post by jerome1232 on 2016-11-17
As I understand it /bin holds simple binaries needed very early in the boot stage, where /usr holds more general programs. I wouldn't bother mounting /usr or /bin on separate partitions, my current Ubuntu install only consumes 8 GB's of space. 6.8 GB's of that are in /usr which is the largest folder.

Mount /home on a different partition, but 32 GB's should be plenty of space for everything else.

When you install programs through Ubuntu Software (or install 3rd party .debs) they are scripted where to go.

---

### Post by jerome1232 on 2016-11-17
Duplicate

---

### Post by Impavidus on 2016-11-17
Loosely speaking, binaries are executables, which are programs. Strictly speaking, this isn't really true. A jpeg file is binary too, a shell script is not.

/sbin is for the tools that aren't useful to the normal user and are normally only used by root that must be available early in the booting process, before other file systems can be mounted. File system checks, mount. /bin is for programs the ordinary users may need, but must be available before mounting other file systems, like tools you need to fix a broken system. Simple text editors, bash, basic commands like mv, ls, rm, cp. /usr is for all higher stuff.

/bin, /sbin, /lib, /etc and /root must all be on the root partition. Everything else can be moved to whatever partition you like, but for most directories that's rarely useful nowadays.

---

