---
title: "Intermittent: unable to open a folder; wastebasket not connected"
date: 2021-03-14
forum: General Help
---

### Post by makem2 on 2021-03-14
Twice recently after a cold restart I have been unable to open a folder on my desktop by double or right clicking on it. I was also unable to open a new window with right click on desktop. I do not get any error message. The only way to get out of this was to reboot.

I have also noticed at least twice that the wastebasket has a red icon and reports unable to reconnect. I cannot say if these two problems are related but both are 'fixed' by a reboot.

I am using an XFCE desktop and thunar 1.8.14

Has anyone an suggestions as to the cause or how to diagnose the problem?

```

makem@XPS-13-9300:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.2 LTS"
NAME="Ubuntu"
VERSION="20.04.2 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.2 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
makem@XPS-13-9300:~$

```

---

### Post by TheFu on 2021-03-14
I suspect sudo abuse.
What are the permissions and ownership for the directories with the issue?

---

### Post by makem2 on 2021-03-15
Thanks for taking the time to reply.

The permissions for the folder are:

Location : /home/make.Desktop

Owner: makem (makem)

Access: Read & Write
Group: makem
Access: Read & Write
Others: Read only

Desktop Properties (For right click to menu including 'Open in New Window')

Owner: makem (makem)

Access: Read & Write
Group: makem
Access: Read only
Others: Read only

---

### Post by TheFu on 2021-03-15
Please post the **ls -al /path/to/directory**

Something like this: 
```
$ \ls -al ~/.config/|more
total 404
drwx------  86 thefu thefu  4096 Jan  3 12:58 .
drwxr-x--- 195 thefu thefu 20480 Mar 15 15:06 ..
```
That's much easier to see the permissions, owners, and no risk of mistakes.

_/home/make.Desktop_ doesn't make sense.

---

### Post by makem2 on 2021-03-15
```

makem@XPS-13-9300:~/Desktop$ ls -la
drwxrwxr-x  3 makem makem   4096 Mar 14 22:47 'may new stuff'
makem@XPS-13-9300:~/Desktop$

```

Yes I agree, _/home/make.Desktop_[COLOR=#000000] doesn't make sense.

I feels sure I copy/pasted but must not have. But if not why not when in front of me? Strange[/COLOR]

---

### Post by TheFu on 2021-03-15
We need to see the . and .. permissions too.  Directory permissions control access to subdirectories.

There are 2 other directories that you reported problems. Am I missing something?  What are the **ls -al** for those?

BTW, I showed a specific command in a specific way to ensure funky aliases wouldn't get in the way.

---

### Post by makem2 on 2021-03-15
> **TheFu said:**
> We need to see the . and .. permissions too.  Directory permissions control access to subdirectories.

There are 2 other directories that you reported problems. Am I missing something?  What are the **ls -al** for those?

BTW, I showed a specific command in a specific way to ensure funky aliases wouldn't get in the way.

I don't understand the 'see the . and .. permissions too.'

I showed the permissions of the one folder which I could not open. I never checked any other folders on the desktop at the tow times I had the problem. Instead I right clicked on the desktop to open a new window from which to then select the errant folder. I could not open the right click menu.

The 'other two directories' you mention were not directories. I reported that I had also had on two occasions had a problem with the wastebasket 'not connecting' I am unable to say if the cause was related to the folder problem.

I have only ever had a problem with one directory because I never checked any others.

Ah, I think I have remebered what you mean about . and .. permissions.

```

makem@XPS-13-9300:~/Desktop$ ls -la
total 884
drwxr-xr-x  9 makem makem   4096 Mar 15 14:44  .
drwxr-xr-x 34 makem makem   4096 Mar 15 14:13  ..


drwxrwxr-x  3 makem makem   4096 Mar 14 22:47 'may new stuff'


makem@XPS-13-9300:~/Desktop$



```

I have cut out the other folder and files as their names are revealing. I could give each an 'X' if you want to see all. There are 20 currently, including directories and files.

I can add:

```

makem@XPS-13-9300:~$ ls -la
total 224
drwxr-xr-x 34 makem makem  4096 Mar 15 14:13 .
drwxr-xr-x  4 root  root   4096 May  6  2020 ..
drwxrwxr-x  2 makem makem  4096 Aug 23  2020 appimages
drwx------  4 makem makem  4096 May  7  2020 .aqbanking
-rw-------  1 makem makem 27981 Mar 14 23:19 .bash_history
-rw-r--r--  1 makem makem   220 May  6  2020 .bash_logout
-rw-r--r--  1 makem makem  3771 May  6  2020 .bashrc
drwxrwxr-x 27 makem makem  4096 Mar 15 14:14 .cache
drwxr-xr-x 34 makem makem  4096 Mar  5 16:40 .config
drwx------  3 makem makem  4096 May  9  2020 .dbus
drwxr-xr-x  9 makem makem  4096 Mar 15 14:44 Desktop

```

---

### Post by TheFu on 2021-03-15
No need to see all the directories or files. What is above is fine.  I'm not seeing anything wrong.  If ACLs are used (you'd know if that was the case), then  those could prevent access. If you didn't specifically go out of your way to setup ACLs, then that isn't the problem.

Lacking permissions and ownership issues, I'd run an **fsck** on the partition where /home is and I'd check the storage using SMART tools for failing disks.  To run fsck, you'll probably need to boot into rescue mode under the Advanced grub menu or boot from an Ubuntu Desktop (any flavor) install flash drive.  fsck cannot be run against any mounted partitions or logical volumes.

For checking SMART data, there are 2 ways.  I'd use smartctl - first run a short or long test, wait for those to finish, then run a report. When requesting a test, the output will say how many minutes to completion. Wait at least that long.

---

### Post by makem2 on 2021-03-15
Ok I will do both. However, the machine is a laptop and the SSD drive is less than 1 year old

---

### Post by makem2 on 2021-03-15
I ran smartctl:

```

makem@XPS-13-9300:~$ sudo smartctl -i -a /dev/nvme0n1
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-44-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Number:                       PC611 NVMe SK hynix 512GB
Serial Number:                      NJ02N799510203421
Firmware Version:                   11000111
PCI Vendor/Subsystem ID:            0x1c5c
IEEE OUI Identifier:                0xace42e
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            ace42e 0005348ed7
Local Time is:                      Mon Mar 15 22:07:29 2021 GMT
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         64 Pages
Warning  Comp. Temp. Threshold:     83 Celsius
Critical Comp. Temp. Threshold:     84 Celsius


Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +   6.3000W       -        -    0  0  0  0        5       5
 1 +   2.4000W       -        -    1  1  1  1       30      30
 2 +   1.9000W       -        -    2  2  2  2      100     100
 3 -   0.0500W       -        -    3  3  3  3     1000    1000
 4 -   0.0040W       -        -    3  3  3  3     1000    9000


Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0
 1 -    4096       0         0


=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        36 Celsius
Available Spare:                    100%
Available Spare Threshold:          50%
Percentage Used:                    0%
Data Units Read:                    7,185,286 [3.67 TB]
Data Units Written:                 5,117,178 [2.61 TB]
Host Read Commands:                 90,208,008
Host Write Commands:                75,182,725
Controller Busy Time:               140
Power Cycles:                       1,095
Power On Hours:                     2,756
Unsafe Shutdowns:                   73
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               37 Celsius
Temperature Sensor 2:               39 Celsius


Error Information (NVMe Log 0x01, max 256 entries)
No Errors Logged


makem@XPS-13-9300:~$ 

```

I didn't get any choices and it finished in seconds.

---

### Post by TheFu on 2021-03-15
That SMART output doesn't look like any test was run yet.  A test is required first.

---

### Post by makem2 on 2021-03-15
```

makem@XPS-13-9300:~$ sudo smartctl -t long /dev/nvme0n1
[sudo] password for makem: 
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-45-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


NVMe device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information


makem@XPS-13-9300:~$ sudo smartctl -a /dev/nvme0n1
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-45-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Number:                       PC611 NVMe SK hynix 512GB
Serial Number:                      NJ02N799510203421
Firmware Version:                   11000111
PCI Vendor/Subsystem ID:            0x1c5c
IEEE OUI Identifier:                0xace42e
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            ace42e 0005348ed7
Local Time is:                      Mon Mar 15 23:04:04 2021 GMT
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         64 Pages
Warning  Comp. Temp. Threshold:     83 Celsius
Critical Comp. Temp. Threshold:     84 Celsius


Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +   6.3000W       -        -    0  0  0  0        5       5
 1 +   2.4000W       -        -    1  1  1  1       30      30
 2 +   1.9000W       -        -    2  2  2  2      100     100
 3 -   0.0500W       -        -    3  3  3  3     1000    1000
 4 -   0.0040W       -        -    3  3  3  3     1000    9000


Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0
 1 -    4096       0         0


=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        39 Celsius
Available Spare:                    100%
Available Spare Threshold:          50%
Percentage Used:                    0%
Data Units Read:                    7,215,101 [3.69 TB]
Data Units Written:                 5,122,727 [2.62 TB]
Host Read Commands:                 90,559,969
Host Write Commands:                75,269,734
Controller Busy Time:               141
Power Cycles:                       1,105
Power On Hours:                     2,757
Unsafe Shutdowns:                   79
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               40 Celsius
Temperature Sensor 2:               41 Celsius


Error Information (NVMe Log 0x01, max 256 entries)
No Errors Logged


makem@XPS-13-9300:~$ 

```

Am I doing something wrong?

I used this page for help:

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Edit:

I have just rebooted and I am able to access the directory in question. However, the error with the wastebasket shows up, suggesting the problem is not related to the directory problem. The wastebasket error is:

Failed to connect to Wastebasket: Error calling StartServiceByName for org.xfce.FileManager:Timeout was reached.

The wastebasket icon is red with an exclamation mark.

---

### Post by TheFu on 2021-03-15
I'm out of ideas, besides
the SSD is failing
or it needs a firmware update.

BTW, wastebasket sounds like "Trash" in American English, so searching for answers with that term may find something.  I don't use a file manager, so we are beyond my knowledge. Sorry. 

Hope someone else can be more helpful.

---

### Post by makem2 on 2021-03-15
Dealing only with the directory which I was unable to open twice:

I tried:

```

sudo touch /forcefsck

```

But either did it very very quick or did nothing. I am having problems checking this SSD which is the soldered in type.

If the drive fails then the machine will need a new motherboard!

Dell offer very little support for machine which are dual booted although they support their own Linux machines.

I will try their windows update facility to see if that will check the drive.

---

### Post by makem2 on 2021-03-16
Dell 'Assist' software performed a hardware check and did not report any problems.

---

### Post by TheFu on 2021-03-16
```
sudo touch /forcefsck
```
stopped working when systemd took over, I'm sad to say. That was around 2016.  You have to either go into the Grub Advanced menu and go into recovery mode or boot from alternate media - like an Ubuntu Install Flash drive - and run fsck for any file systems that are always mounted when the normal system is running.  One more reason that systemd isn't great.  I miss the /forcefsck. It was a great tool.

I've never been impressed by Dell software. I have owned a number of Dell laptops and computers over the years. Dell is always on my short list of laptops for consideration. I prefer their laptop keyboards.

---

### Post by makem2 on 2021-03-16
I didn't trust Dell computers having bought three of them trying to get one which didn't have a problem. I gave up and changed the third one for Toshiba.

I changed back to Dell because of the screen size and a few other things with trepidation. However after quite a good experience with the XPS I bought another. The oldest is now a 11 months old and has never given trouble. Everything went fine on dual boot install compared with some other machines Iv'e had. All the software worked out of the box which I had hoped because Dell do a Ubuntu XPS machine.

This directory thing is annoying and I am hoping it is not a sign of M2 SSD degradation as you suggest may be. A new mobo would cost an arm and a leg for 2 machines. It was something I spoke to Dell about before I bought but it seems all small thin light laptops were going that way.

I will try using a live USB to do an fsck soon. Are you able to point me to a page for help?

---

