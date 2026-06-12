---
title: "Issues with downloading files"
date: 2012-11-03
forum: General Help
---

### Post by newuser1234 on 2012-11-03
hi all, i'm a new ubuntu user and am hoping someone can help me with my issue. i have ubuntu v.12.04, 64 bit running on an asus u41sv laptop. it's installed as a dual boot with windows 7 64 bit. as far as i can tell, i have the latest ubuntu updates installed.
 
basically, i get errors in large files (academic files ~5-6 Gb) that i download from a server, or copy from a hard drive. once the files are downloaded, i find that text from other files on my hard drive are introduced into the downloaded/copied files. at first i thought it was a RAM issue, but i don't seem to have this issue when i download the same files using windows 7. the RAM and hard drive have also been tested by the retailers who said everything seems fine.
 
anyway, i'm hoping someone might be able to help on this issue. thanks in advance.

---

### Post by apollothethird on 2012-11-03
> **newuser1234 said:**
> hi all, i'm a new ubuntu user and am hoping someone can help me with my issue. i have ubuntu v.12.04, 64 bit running on an asus u41sv laptop. it's installed as a dual boot with windows 7 64 bit. as far as i can tell, i have the latest ubuntu updates installed.
 
basically, i get errors in large files (academic files ~5-6 Gb) that i download from a server, or copy from a hard drive. once the files are downloaded, i find that text from other files on my hard drive are introduced into the downloaded/copied files. at first i thought it was a RAM issue, but i don't seem to have this issue when i download the same files using windows 7. the RAM and hard drive have also been tested by the retailers who said everything seems fine.
 
anyway, i'm hoping someone might be able to help on this issue. thanks in advance.

Your issue is a bit confusing.  First I'll try to isolate the unrelated things of your post.  It doesn't matter whether you have dual boot or not.  When booting under Ubuntu, that's the operating system that you're running.

Also, I don't understand what you mean when you say download.  Are you using a browser to download files?  Which browser are you using?

If you mean you're copying files from one drive (or device) to another, how are you copying the files?  Are you using the commandline (cp [/path-to-file/filename] [newfilename]"?  Are you using Nautilus?

Finally, you suggest this only happens with large files.  It may make a difference whether you have a 32bit or 64 bit installation.  Since I you mention "64 bit" in your title, I'm assuming it's a 64 bit installation.  Will you verify this with:

Click - Power Icon > System Settings > Details (And tell us what you have for OS Type?

Your answer to those questions might identify the problem or bring up more questions.  Since both downloading and copying files should be non-issues, the resolution should be simple.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by The Cog on 2012-11-03
Also, what filesystem (ext4, NTFS etc) are you saving the files on?

---

### Post by newuser1234 on 2012-11-03
thanks apollo/cog, and apologies for the lack of detail/confusion. 

i'm using a 64 bit ubuntu OS. the issue arises when i use either the scp  command to copy the files off a server (using ethernet connection),  and when i copy the files off a portable hard drive through a usb  connection (either command prompt or dragging files from one  directory to another in the ubuntu "windows"). actually, i'm not sure if the issue only  arises with big files, but i've noticed it for the big  files as i've been working on them quite intensely lately. 

the hard drive is partitioned and formatted to ext4 for ubuntu. i have these issues when i copy these files directly into the ext4 formatted partition when using the ubuntu scp command . however, the files copy perfectly from the server when i'm using windows 7 and the winscp program. in windows 7, i copy the files to a ntfs partition on my hard drive that's accessible to ubuntu. i've been working on these files in ubuntu using this shared ntfs partition.  

anyway, please let me know if you need any more detail/clarification. cheers!

---

### Post by apollothethird on 2012-11-03
> **newuser1234 said:**
> thanks apollo/cog, and apologies for the lack of detail/confusion. 

i'm using a 64 bit ubuntu OS. the issue arises when i use either the scp  command to copy the files off a server (using ethernet connection),  and when i copy the files off a portable hard drive through a usb  connection (either command prompt or dragging files from one  directory to another in the ubuntu "windows"). actually, i'm not sure if the issue only  arises with big files, but i've noticed it for the big  files as i've been working on them quite intensely lately. 

the hard drive is partitioned and formatted to ext4 for ubuntu. i have these issues when i copy these files directly into the ext4 formatted partition when using the ubuntu scp command . however, the files copy perfectly from the server when i'm using windows 7 and the winscp program. in windows 7, i copy the files to a ntfs partition on my hard drive that's accessible to ubuntu. i've been working on these files in ubuntu using this shared ntfs partition.  

anyway, please let me know if you need any more detail/clarification. cheers!

I would like to try to duplicate the problem.  To make it easier, try starting out with a couple of small files.  Give us the exact command you're using.  Use the code tags to make it easy to follow.  Also try the "cp" command if you're copying from a USB drive.  Immediately after copying the file run the cmp command to identify what has happened (if you're copying from a usb drive).

For example:

```

$ cp /mnt/usbdrive/filea ~/filea
$ cmp /mnt/usbdrive/filea ~/filea

```

After you post your "scp" examples I'll test what you're using on my computer also.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by newuser1234 on 2012-11-04
thanks. i'm kinda new to the linux environment so i won't be too  specific re. my scp command in case it's not a god thing (even though my  account is password protected), but it is essentially:

[SIZE=2]scp [SIZE=2]my_user_account[/SIZE]@[SIZE=2]server[/SIZE].university.edu.au:/[SIZE=2]home/[SIZE=2]my_user_account[/SIZE]/[SIZE=2]file [/SIZE][/SIZE].

[SIZE=2][SIZE=2][SIZE=2]with re. to co[SIZE=2]pying from my hard drive, [SIZE=2]i [/SIZE][/SIZE][SIZE=2][SIZE=2] used the following command:

[SIZE=2]cp /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq .

as s[SIZE=2]uggested[SIZE=2], [SIZE=2]i then compared the two files using cmp:

laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq[SIZE=2] [/SIZE]22Rv1_DHT_L1_1.fq 
/media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq 22Rv1_DHT_L1_1.fq differ: byte 526385153, line 8524481 is  61 1 124 T

[/SIZE][/SIZE]i[SIZE=2] [SIZE=2]copied[/SIZE] the file [SIZE=2]5[/SIZE] times, and four times i[SIZE=2]t was c[/SIZE][/SIZE][/SIZE]or[SIZE=2]rupted[SIZE=2] (on one c[SIZE=2]opy it [/SIZE]was good)[SIZE=2][SIZE=2]. [SIZE=2]also, it's not always at the same place where the errors s[SIZE=2]tart (or what's introduced into the file[SIZE=2]) [/SIZE]in[SIZE=2] the copied file.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]
[SIZE=2]as suggested, i[SIZE=2] then made two smaller fi[SIZE=2]les of the original that's on my external hard drive using the following command:

[SIZE=2]laij@laij:/media/linux/Seq/Raw_data$ head -100000 22Rv1_DHT_L1_1.fq >shorter[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
laij@laij:/media/linux/Seq/Raw_data$ head -10000000 22Rv1_DHT_L1_1.fq >short

[SIZE=2]-rw-rw-r-- 1 laij laij    6139190 Nov  4 16:33 short
-rw-rw-r-- 1 laij laij      61316 Nov  4 16:30 shorter
[SIZE=2]-rw------- 1 laij laij 5476503134 Jun 12 12:24 22Rv1_DHT_L1_1.fq   ===[SIZE=2]> ori[SIZE=2]ginal file[/SIZE][/SIZE][/SIZE]
[/SIZE]
[SIZE=2]i copied [SIZE=2]and then compared both files (with [SIZE=2]the[SIZE=2]ir respective original on the external hard drive) [/SIZE][/SIZE]10 times and they [SIZE=2]were fine [SIZE=2]for all copies.

[SIZE=2]laij@laij:~/temp$ cp /media/linux/Seq/Raw_data/short .
[/SIZE][SIZE=2]laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/short short[/SIZE]
[SIZE=2]laij@laij:~/temp$ cp /media/linux/Seq/Raw_data/shorter .
laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/shorter shorter [/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]


[/SIZE][/SIZE]
[/SIZE][/SIZE] [/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]


[/SIZE]

---

### Post by apollothethird on 2012-11-04
> **newuser1234 said:**
> thanks. i'm kinda new to the linux environment so i won't be too  specific re. my scp command in case it's not a god thing (even though my  account is password protected), but it is essentially:

[SIZE=2]scp [SIZE=2]my_user_account[/SIZE]@[SIZE=2]server[/SIZE].university.edu.au:/[SIZE=2]home/[SIZE=2]my_user_account[/SIZE]/[SIZE=2]file [/SIZE][/SIZE].

[SIZE=2][SIZE=2][SIZE=2]with re. to co[SIZE=2]pying from my hard drive, [SIZE=2]i [/SIZE][/SIZE][SIZE=2][SIZE=2] used the following command:

[SIZE=2]cp /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq .

as s[SIZE=2]uggested[SIZE=2], [SIZE=2]i then compared the two files using cmp:

laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq[SIZE=2] [/SIZE]22Rv1_DHT_L1_1.fq 
/media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq 22Rv1_DHT_L1_1.fq differ: byte 526385153, line 8524481 is  61 1 124 T

[/SIZE][/SIZE]i[SIZE=2] [SIZE=2]copied[/SIZE] the file [SIZE=2]5[/SIZE] times, and four times i[SIZE=2]t was c[/SIZE][/SIZE][/SIZE]or[SIZE=2]rupted[SIZE=2] (on one c[SIZE=2]opy it [/SIZE]was good)[SIZE=2][SIZE=2]. [SIZE=2]also, it's not always at the same place where the errors s[SIZE=2]tart (or what's introduced into the file[SIZE=2]) [/SIZE]in[SIZE=2] the copied file.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]
[SIZE=2]as suggested, i[SIZE=2] then made two smaller fi[SIZE=2]les of the original that's on my external hard drive using the following command:

[SIZE=2]laij@laij:/media/linux/Seq/Raw_data$ head -100000 22Rv1_DHT_L1_1.fq >shorter[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
laij@laij:/media/linux/Seq/Raw_data$ head -10000000 22Rv1_DHT_L1_1.fq >short

[SIZE=2]-rw-rw-r-- 1 laij laij    6139190 Nov  4 16:33 short
-rw-rw-r-- 1 laij laij      61316 Nov  4 16:30 shorter
[SIZE=2]-rw------- 1 laij laij 5476503134 Jun 12 12:24 22Rv1_DHT_L1_1.fq   ===[SIZE=2]> ori[SIZE=2]ginal file[/SIZE][/SIZE][/SIZE]
[/SIZE]
[SIZE=2]i copied [SIZE=2]and then compared both files (with [SIZE=2]the[SIZE=2]ir respective original on the external hard drive) [/SIZE][/SIZE]10 times and they [SIZE=2]were fine [SIZE=2]for all copies.

[SIZE=2]laij@laij:~/temp$ cp /media/linux/Seq/Raw_data/short .
[/SIZE][SIZE=2]laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/short short[/SIZE]
[SIZE=2]laij@laij:~/temp$ cp /media/linux/Seq/Raw_data/shorter .
laij@laij:~/temp$ cmp -b /media/linux/Seq/Raw_data/shorter shorter [/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]


[/SIZE][/SIZE]
[/SIZE][/SIZE] [/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]


[/SIZE]

I wouldn't expect for you to include passwords for your remote machines.

I'm sorry, but it's very hard for me to make out what you have done because you didn't use code tags.  That's having your commands between "[ code ]" and "[ /code ]" tags without the quotes and the spaces.

I understand your emphasis on being new, even from your first message.  New isn't a big criterion.  The commands will work the same for everyone.  You just have to take your time with the commands and you'll soon learn.

If you try to use the code tags and have problems, we'll help you with them.  You may be surprised at how quickly your messages might start to appear like an experienced user with a little effort.

If your messages are easier to read and interpret the assistance you get will be quicker and clearer.  The people trying to help will often put a lot of effort in their attempts to be clear and to help.  I hope you don't mind my taking the time to show you have to put some of this same effort into your description.

I'll keep studying your message trying to figure out where your problem lies.  But if you don't mind and will try again to make a clearer post, it'd make it much easier for me and others to identify the problems.

Edit:  I understand there is a problem somewhere.  It's nice that there is some consistency so that when the problem is resolved it'll make it easier to identify.

Also, while there is a problem, I do know it's possible to download things correctly to your system, otherwise the installation would have failed.  Also none of your updates would succeed.

In fact, would you mind running this quick test:

```

$ sudo apt-get update
$ sudo apt-get upgrade

```

Those command will verify two things.  The integrability of your system's ability to download files from the Internet and that you have a fully updated OS installation.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by newuser1234 on 2012-11-04
no worries, and thanks for the advice on code tags. i'm currently at work but will read up on code tags when i'm at home. i really appreciate your efforts.

with re. to:
```

$ sudo apt-get update
i get the following after it's printed out a list of things starting with Hit http://

Reading package lists... Done

with re. to: 

$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  base-files colord gir1.2-gudev-1.0 gnome-power-manager libcolord1
  libgudev-1.0-0 libnautilus-extension1a libudev0 nautilus nautilus-data udev
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,929 kB of archives.
After this operation, 10.2 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main base-files amd64 6.5ubuntu6.4 [69.9 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libudev0 amd64 175-0ubuntu9.2 [29.2 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libcolord1 amd64 0.1.16-2ubuntu0.1 [48.8 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libgudev-1.0-0 amd64 1:175-0ubuntu9.2 [14.5 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main colord amd64 0.1.16-2ubuntu0.1 [93.8 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main udev amd64 175-0ubuntu9.2 [323 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-gudev-1.0 amd64 175-0ubuntu9.2 [3,982 B]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-power-manager amd64 3.4.0-0ubuntu1.1 [407 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a amd64 1:3.4.2-0ubuntu5 [51.3 kB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus-data all 1:3.4.2-0ubuntu5 [63.4 kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus amd64 1:3.4.2-0ubuntu5 [824 kB]
Fetched 1,929 kB in 0s (9,564 kB/s)
(Reading database ... 279884 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.2 (using .../base-files_6.5ubuntu6.4_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
Setting up base-files (6.5ubuntu6.4) ...
(Reading database ... 279885 files and directories currently installed.)
Preparing to replace libudev0 175-0ubuntu9.1 (using .../libudev0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libcolord1 0.1.16-2 (using .../libcolord1_0.1.16-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libcolord1 ...
Preparing to replace libgudev-1.0-0 1:175-0ubuntu9.1 (using .../libgudev-1.0-0_1%3a175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace colord 0.1.16-2 (using .../colord_0.1.16-2ubuntu0.1_amd64.deb) ...
Unpacking replacement colord ...
Preparing to replace udev 175-0ubuntu9.1 (using .../udev_175-0ubuntu9.2_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace gir1.2-gudev-1.0 175-0ubuntu9.1 (using .../gir1.2-gudev-1.0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Preparing to replace gnome-power-manager 3.4.0-0ubuntu1 (using .../gnome-power-manager_3.4.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gnome-power-manager ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu4 (using .../libnautilus-extension1a_1%3a3.4.2-0ubuntu5_amd64.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu4 (using .../nautilus-data_1%3a3.4.2-0ubuntu5_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu4 (using .../nautilus_1%3a3.4.2-0ubuntu5_amd64.deb) ...
Unpacking replacement nautilus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libglib2.0-0 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for gconf2 ...
Processing triggers for menu ...
Setting up libudev0 (175-0ubuntu9.2) ...
Setting up libcolord1 (0.1.16-2ubuntu0.1) ...
Setting up libgudev-1.0-0 (1:175-0ubuntu9.2) ...
Setting up colord (0.1.16-2ubuntu0.1) ...
Setting up udev (175-0ubuntu9.2) ...
udev stop/waiting
udev start/running, process 8855
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up gir1.2-gudev-1.0 (175-0ubuntu9.2) ...
Setting up gnome-power-manager (3.4.0-0ubuntu1.1) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu5) ...
Setting up nautilus-data (1:3.4.2-0ubuntu5) ...
Setting up nautilus (1:3.4.2-0ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
Processing triggers for menu ...

```
apologies for printing it all out, but i didn't know how to sum that up or what is relevant to include.

---

### Post by apollothethird on 2012-11-04
> **newuser1234 said:**
> no worries, and thanks for the advice on code tags. i'm currently at work but will read up on code tags when i'm at home. i really appreciate your efforts.

with re. to:

$ sudo apt-get update
i get the following after it's printed out a list of things starting with Hit http://

Reading package lists... Done

with re. to: 

$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  base-files colord gir1.2-gudev-1.0 gnome-power-manager libcolord1
  libgudev-1.0-0 libnautilus-extension1a libudev0 nautilus nautilus-data udev
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,929 kB of archives.
After this operation, 10.2 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main base-files amd64 6.5ubuntu6.4 [69.9 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libudev0 amd64 175-0ubuntu9.2 [29.2 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libcolord1 amd64 0.1.16-2ubuntu0.1 [48.8 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libgudev-1.0-0 amd64 1:175-0ubuntu9.2 [14.5 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main colord amd64 0.1.16-2ubuntu0.1 [93.8 kB]
Get:6 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main udev amd64 175-0ubuntu9.2 [323 kB]
Get:7 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-gudev-1.0 amd64 175-0ubuntu9.2 [3,982 B]
Get:8 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-power-manager amd64 3.4.0-0ubuntu1.1 [407 kB]
Get:9 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a amd64 1:3.4.2-0ubuntu5 [51.3 kB]
Get:10 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus-data all 1:3.4.2-0ubuntu5 [63.4 kB]
Get:11 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus amd64 1:3.4.2-0ubuntu5 [824 kB]
Fetched 1,929 kB in 0s (9,564 kB/s)
(Reading database ... 279884 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.2 (using .../base-files_6.5ubuntu6.4_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
Setting up base-files (6.5ubuntu6.4) ...
(Reading database ... 279885 files and directories currently installed.)
Preparing to replace libudev0 175-0ubuntu9.1 (using .../libudev0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libcolord1 0.1.16-2 (using .../libcolord1_0.1.16-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libcolord1 ...
Preparing to replace libgudev-1.0-0 1:175-0ubuntu9.1 (using .../libgudev-1.0-0_1%3a175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace colord 0.1.16-2 (using .../colord_0.1.16-2ubuntu0.1_amd64.deb) ...
Unpacking replacement colord ...
Preparing to replace udev 175-0ubuntu9.1 (using .../udev_175-0ubuntu9.2_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace gir1.2-gudev-1.0 175-0ubuntu9.1 (using .../gir1.2-gudev-1.0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Preparing to replace gnome-power-manager 3.4.0-0ubuntu1 (using .../gnome-power-manager_3.4.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gnome-power-manager ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu4 (using .../libnautilus-extension1a_1%3a3.4.2-0ubuntu5_amd64.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu4 (using .../nautilus-data_1%3a3.4.2-0ubuntu5_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu4 (using .../nautilus_1%3a3.4.2-0ubuntu5_amd64.deb) ...
Unpacking replacement nautilus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libglib2.0-0 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for gconf2 ...
Processing triggers for menu ...
Setting up libudev0 (175-0ubuntu9.2) ...
Setting up libcolord1 (0.1.16-2ubuntu0.1) ...
Setting up libgudev-1.0-0 (1:175-0ubuntu9.2) ...
Setting up colord (0.1.16-2ubuntu0.1) ...
Setting up udev (175-0ubuntu9.2) ...
udev stop/waiting
udev start/running, process 8855
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up gir1.2-gudev-1.0 (175-0ubuntu9.2) ...
Setting up gnome-power-manager (3.4.0-0ubuntu1.1) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu5) ...
Setting up nautilus-data (1:3.4.2-0ubuntu5) ...
Setting up nautilus (1:3.4.2-0ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
Processing triggers for menu ...

apologies for printing it all out, but i didn't know how to sum that up or what is relevant to include.

When you reply to a message you have quote tags.  These are tags like:

[ quote ]
Your message here
[ /quote ]


It's the tags you see above without the spaces.  They are not performing above as quote tags because there are spaces between the words and the brackets.

Code tags are the same.  Look at:

[ code ]
Your code or text here
[ /code ]

If I had put the brackets and words without spaces it would appear as:

```

Your code or text here

```

I don't blame you for preferring to read up on it, or just test it and allow me to elaborate if you're having problems.  It might be clearer when you research.  If you use them in your messages when you're giving code or command output it'll make your message much easier to read.

I can't tell from what you wrote in your previous message if you performed the update, then tested copying from your media and got the same results.

Did the update help at all?

Also, I know you're having problems with both "cp" and "scp".  I'd recommend that you first try to get "cp" to work properly, then go to the "scp".  If the "cp" (copying local files) are going to fail, it would be pretty unlikely that you'd have consistent success with other manners of transferring files.


-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by newuser1234 on 2012-11-05
ok, i think i understand code tags, so hopefully my posts will be a bit more clearer now.  i'll start from post #6 :

the command (using generic names for user account and university) that i use for scp copying is:
```
[SIZE=2]$scp [SIZE=2]my_user_account[/SIZE]@[SIZE=2]server[/SIZE].university.edu.au:/[SIZE=2]home/[SIZE=2]my_user_account[/SIZE]/[SIZE=2]file [/SIZE][/SIZE].[/SIZE]
```[SIZE=2][SIZE=2]

[/SIZE]i [SIZE=2]again used scp to copy [SIZE=2]the ~5 Gb files [/SIZE][/SIZE]after [SIZE=2]instal[SIZE=2]ling the u[SIZE=2]pdates you recommended but it didn't seem to fix the problem.

 [/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2]with re. to co[SIZE=2]pying files from my external hard drive to[SIZE=2] the hard drive on my laptop[/SIZE], [SIZE=2]i [/SIZE][/SIZE][SIZE=2][SIZE=2] used the following command while i was in the laptop directory:
```
[SIZE=2]$cp /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq .[/SIZE]
```[SIZE=2]

22Rv1_D[SIZE=2]HT_L1_1.f[SIZE=2]q is the file name (~5 Gb). i th[/SIZE][/SIZE]en [SIZE=2][SIZE=2][SIZE=2]compared the two files using the cmp command:

```
$cmp -b /media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq22Rv1_DHT_L1_1.fq
```[SIZE=2]

[SIZE=2]the output for this command was:

[/SIZE][/SIZE]$/media/linux/Seq/Raw_data/22Rv1_DHT_L1_1.fq 22Rv1_DHT_L1_1.fq differ: byte 526385153, line 8524481 is  61 1 124 T

[/SIZE][/SIZE]i[SIZE=2] [SIZE=2]copied[/SIZE] the file [SIZE=2]5[/SIZE] times, and four times i[SIZE=2]t was c[/SIZE][/SIZE][/SIZE]or[SIZE=2]rupted[SIZE=2] (on one c[SIZE=2]opy it [/SIZE]was good)[SIZE=2][SIZE=2]. [SIZE=2]also, it's not always at the same place where the errors s[SIZE=2]tart (or what's introduced into the file[SIZE=2]) [/SIZE]in[SIZE=2] the copied file.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]
[SIZE=2]whilst[SIZE=2] in the external hard drive directory (/media/linu[SIZE=2]x/Seq/Raw_data/), [/SIZE][/SIZE]i[SIZE=2] then made two smaller fi[SIZE=2]les of the [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]22Rv1_DHT_L1_1.fq file[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] using the following command:

```
[SIZE=2]$head -100000 22Rv1_DHT_L1_1.fq >shorter[/SIZE]
```[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]```

$head -10000000 22Rv1_DHT_L1_1.fq >short
```[SIZE=2]while in my laptop [SIZE=2]directory(/home/laij), i used the following commands to [/SIZE]cop[SIZE=2]y[/SIZE] [SIZE=2]both files ([SIZE=2]short and shorter) [/SIZE]from my [SIZE=2]external hard drive to my laptop hard drive [SIZE=2]using[SIZE=2]:[/SIZE][/SIZE]

[SIZE=2] ```
[SIZE=2]$cp /media/linux/Seq/Raw_data/short .[/SIZE][SIZE=2]$ cp /media/linux/Seq/Raw_data/shorter .[/SIZE]
```[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]

[SIZE=2]while in my laptop directory, i then compared the copied   short and shorter files with the original ones on the external hard   drive using:
[/SIZE][/SIZE]```
$[SIZE=2]cmp -b /media/linux/Seq/Raw_data/short short[/SIZE]
```[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]```
[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] 
[SIZE=2]$[/SIZE]cmp -b /media/linux/Seq/Raw_data/shorter shorter[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
```[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]

these short and shorter files copied over perfectly a[SIZE=2]fter 10 copies and fo[SIZE=2]r both the short and shorter files. cheers, and thanks for your patience.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] [/SIZE] [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by The Cog on 2012-11-05
That's an ugly problem. I have no idea why it might be happening, but if might be useful to know if it's a read problem or a write problem. If you campare the same pair of files several times, do you always get the same answer? If not then it's a problem with reading the files. If you always get the same answer then the error must have occured while writing the copy.

Can you mount the windows disk and try writing a copy to the NTFS partition instead? 

You're not out of disk space are you? Try```
df -h
```and check there's enough space. I think this is probably not the problem because you don't see an out of space error, but it's worth double-checking.

---

### Post by newuser1234 on 2012-11-05
yeah it really sux as i'm learning linux and perl programming at the moment. as a beginner, i just assumed my programming really sucked (which it does but that's another story hahaha), but i realised that this is actually a real problem and that my code was actually ok. 

based on your description cog, i'm assuming it's a read problems as copying the same file multiple times results in different errors -- sometimes none at all. as mentioned, copying files via winscp in windows 7 doesn't give these errors so i assume it's not a hardware issue. it's def. not a space issue as i get errors even when i have hundreds of Gb hard drive space.

it's a good idea trying to copy directly to the ntfs partition -- i'll try it tomorrow. from memory, i might have started on the shared ntfs partition (but copying using ubuntu and not windows), and actually i think i originally thought that the ntfs formatting might be causing these errors.

---

### Post by The Cog on 2012-11-05
>  i'm assuming it's a read problems as copying the same file multiple times results in different errors
Copying the file involves both reading from one disk and writing to another, so you cannot tell which one is failing. That's why I suggested that you simply compare the same pair of files several times. If the problem is with reading then re-comparing the same pair of files repeatedly could produce different comparison results every time. If the problem is with writing, then re-comparing the same pair of files should consistently give the same result because comparing files doesn't involve writing.

---

### Post by apollothethird on 2012-11-05
Newuser.  I'm wondering what would be the results of copying/downloading files from a fresh try Ubuntu (with the OS run from the DVD)?

Boot to the DVD, then run the same scp, cp, and cmp commands and see if you get the same.  If you get the same, this might indicate a problem with your hardware (ram, motherboard, harddrive).  Try first running copies to the ram drive space.  Then mount your local drives and try transfers to it.

If you have success, it might indicate some problem with your OS installation.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by newuser1234 on 2012-11-05
> That's why I suggested that you simply compare the same pair of files several times. ok, i just realised what you meant. you and apollo have given me quite a few things to chase up, and given the randomness at which the copy issue arises, i'll need to spend more time on this over the weekend using different copy configurations ie. between hard drives and between partitions. i just realised that this issue also occurs in windows as 1 file copied by winscp seems to have a copy error. it seems to occur much less frequently using winscp, and the error introduced is much smaller. ie. ubuntu scp issues results in the introduction of many (off the top of my head >30) lines of text from other files on my hard drive into the copied file, whereas the windows copy error (using winscp off a server) results in the introduction of only 1 line of text into the copied file.

i brought the laptop into repair (still under warranty) ~ 1 month ago for constant bluescreens in windows. the repairers said they didn't experience any bluescreens during their tests, but they replaced 1 of the ram modules anyway (the one they upgraded for free during the purchase). since then i don't get any windows bluescreen, so i'll see if i can get the other ram module replaced on the weekend as well. will keep you guys posted on the weekend --unless the repairers want my laptop to do more testing on it.

---

### Post by The Cog on 2012-11-06
I think the live CD gives you an option of running a memory test instead of booting into Linux. That might be worth running for a while.

---

### Post by newuser1234 on 2012-11-06
thanks cog -- i'll def. give this a go. looks like i'm in for a busy weekend!

---

### Post by newuser1234 on 2012-11-10
ok, so i copied 3 files (~5 Gb each) 7 times (21 copies in total) in windows from my hard drive to my laptop hard drive with no errors in any of the copies. seeing as it's difficult to reproduce this copy error in windows, and that my warranty only covers windows issues, it looks like i won't be able to return it for repair. it's possible that the file that i thought was copied via windows and which had an error might not have been copied in windows -- i've done so many copies that i can't remember properly.
 
with re. to checking whether cmp gives the same results each time, i did a copy in ubuntu (hard drive to laptop), then did cmp between the two files 5 times, each one reporting the same error. i also did a memory test and it came back as ok.
 
i also booted ubuntu from the installation dvd and ran it under the dvd. i then did 3 copies and 2 of these resulted in an error. i think it's time to put this in the too hard basket. luckily i can copy the files i need through windows and work on it in ubuntu if needed. i also have access to other computers that i can check scripts on so i'm not too worried. hopefully, future ubuntu updates might be able to fix this issue. anyway, many thanks to cog and apollo for troubleshooting this with me -- much appreciated!

---

