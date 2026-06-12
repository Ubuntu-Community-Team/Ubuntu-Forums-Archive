---
title: "During &amp; after Jul 19 Software Updater bug?"
date: 2018-07-19
forum: General Help
---

### Post by musiclover-mm on 2018-07-19
I hope this is the correct forum. Is this General Support or is there a bug in the code that was in the update? Newbie.

running Linux 4.15.0-24-Generic i686
#26-Ubuntu SMP Wed Jun 13 08:44:45 UTC 2018
GNU C Library / (Ubuntu GLIB 2.27-3 ubuntu1) 2.27
Ubuntu 18.04 LTS

Software Updater download weirdness ie. screen fade multiple times during download & install. Close button fade. It was screen flicker on & off. Like when running windows and you are crashing.

New, so if you need more info to diagnose, plse just ask. I can run terminal commands. Also I have not downloaded anything else in months. Keeping it lean & clean as I know how to.

Thanks. 
p.s. I won't be around all day (north america PST) so I'll work with you as much as I can. I don't have a PDA.

---

### Post by slickymaster on 2018-07-19
*Thread moved to **General Help**.*

---

### Post by musiclover-mm on 2018-07-19
got it. tks.

---

### Post by Bashing-om on 2018-07-19
musiclover-mm; Hummmmm.......

what is the meaning of "got it" ?

If you no longer have an issue  Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

else provide us the outputs - Between code tags -  of terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2018-07-19
I also note you are running Linux 4.15.0-24-Generic i686 which is a kernel version which has been withdrawn from the repos due to various problems, most notably a very slow boot time, but perhaps others as well.

Try booting to another earlier kernel, eg 4.15.0-23 to see if that overcomes your problems.

---

### Post by musiclover-mm on 2018-07-20
"Got it. Tks" was a quick reply to the request to mark post as "Solved" once the issue is resolved.

Thank you for your reply Bashing-om. It is not yet resolved as I have not tried your solution yet. To be clearer, I was more concerned that the code I downloaded by using "Software Updater" was corrupt. My only other clue to why my sys was flashing is that I was on Youtube for a few hours the previous day and may have picked something up. I don't yet have the Lubuntu Firewall configured as I have no clue, and I mean none, as to how to do that. I scoured the instructions, and I couldn't make any sense of what to do or where to start. I know...but there you have it. Being poor is not a crime, being stupid is not a crime, but not having a firewall is pretty dumb. I am not a super geek and the hours needed to get familiar with this software have been squandered doing other things.

Okay here goes, I am now running the suggested commands. 

Here is what my computer said to your suggested commands. 

```
jane@jane-Inspiron-530s:~$ sudo apt update
[sudo] password for jane: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease   
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic InRelease          
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease          
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease         
Hit:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates InRelease      
Hit:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
17 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (main/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (main/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (restricted/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (restricted/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:54
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (main/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (main/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (restricted/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (restricted/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:49
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:51
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-i386) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:53
jane@jane-Inspiron-530s:~$ sudo apt full -upgrade
E: Command line option 'p' [from -upgrade] is not understood in combination with the other options.
jane@jane-Inspiron-530s:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libnss-systemd libpam-systemd libsystemd0
  libudev1 python-apt-common python3-apt python3-distupgrade snapd systemd
  systemd-sysv ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udev
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.2 MB of archives.
After this operation, 560 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 libsystemd0 i386 237-3ubuntu10.2 [221 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 libpam-systemd i386 237-3ubuntu10.2 [114 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 libnss-systemd i386 237-3ubuntu10.2 [111 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 systemd i386 237-3ubuntu10.2 [2,949 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 udev i386 237-3ubuntu10.2 [1,107 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 libudev1 i386 237-3ubuntu10.2 [57.4 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 systemd-sysv i386 237-3ubuntu10.2 [11.7 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 language-pack-en all 1:18.04+20180712 [1,904 B]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 language-pack-en-base all 1:18.04+20180712 [419 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 language-pack-gnome-en all 1:18.04+20180712 [1,920 B]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 language-pack-gnome-en-base all 1:18.04+20180712 [473 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 python-apt-common all 1.6.2 [16.4 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 python3-apt i386 1.6.2 [151 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 ubuntu-release-upgrader-gtk all 1:18.04.21 [9,372 B]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 ubuntu-release-upgrader-core all 1:18.04.21 [24.4 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 python3-distupgrade all 1:18.04.21 [105 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main i386 snapd i386 2.33.1+18.04ubuntu2 [9,435 kB]
Fetched 15.2 MB in 5s (2,864 kB/s)  
(Reading database ... 183585 files and directories currently installed.)
Preparing to unpack .../libsystemd0_237-3ubuntu10.2_i386.deb ...
Unpacking libsystemd0:i386 (237-3ubuntu10.2) over (237-3ubuntu10) ...
Setting up libsystemd0:i386 (237-3ubuntu10.2) ...
(Reading database ... 183585 files and directories currently installed.)
Preparing to unpack .../libpam-systemd_237-3ubuntu10.2_i386.deb ...
Unpacking libpam-systemd:i386 (237-3ubuntu10.2) over (237-3ubuntu10) ...
Preparing to unpack .../libnss-systemd_237-3ubuntu10.2_i386.deb ...
Unpacking libnss-systemd:i386 (237-3ubuntu10.2) over (237-3ubuntu10) ...
Preparing to unpack .../systemd_237-3ubuntu10.2_i386.deb ...
Unpacking systemd (237-3ubuntu10.2) over (237-3ubuntu10) ...
Preparing to unpack .../udev_237-3ubuntu10.2_i386.deb ...
Unpacking udev (237-3ubuntu10.2) over (237-3ubuntu10) ...
Preparing to unpack .../libudev1_237-3ubuntu10.2_i386.deb ...
Unpacking libudev1:i386 (237-3ubuntu10.2) over (237-3ubuntu10) ...
Setting up libudev1:i386 (237-3ubuntu10.2) ...
Setting up systemd (237-3ubuntu10.2) ...
(Reading database ... 183585 files and directories currently installed.)
Preparing to unpack .../00-systemd-sysv_237-3ubuntu10.2_i386.deb ...
Unpacking systemd-sysv (237-3ubuntu10.2) over (237-3ubuntu10) ...
Preparing to unpack .../01-language-pack-en_1%3a18.04+20180712_all.deb ...
Unpacking language-pack-en (1:18.04+20180712) over (1:18.04+20180423) ...
Preparing to unpack .../02-language-pack-en-base_1%3a18.04+20180712_all.deb ...
Unpacking language-pack-en-base (1:18.04+20180712) over (1:18.04+20180423) ...
Preparing to unpack .../03-language-pack-gnome-en_1%3a18.04+20180712_all.deb ...
Unpacking language-pack-gnome-en (1:18.04+20180712) over (1:18.04+20180423) ...
Preparing to unpack .../04-language-pack-gnome-en-base_1%3a18.04+20180712_all.deb ...
Unpacking language-pack-gnome-en-base (1:18.04+20180712) over (1:18.04+20180423) ...
Preparing to unpack .../05-python-apt-common_1.6.2_all.deb ...
Unpacking python-apt-common (1.6.2) over (1.6.1) ...
Preparing to unpack .../06-python3-apt_1.6.2_i386.deb ...
Unpacking python3-apt (1.6.2) over (1.6.1) ...
Preparing to unpack .../07-ubuntu-release-upgrader-gtk_1%3a18.04.21_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:18.04.21) over (1:18.04.19) ...
Preparing to unpack .../08-ubuntu-release-upgrader-core_1%3a18.04.21_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:18.04.21) over (1:18.04.19) ...
Preparing to unpack .../09-python3-distupgrade_1%3a18.04.21_all.deb ...
Unpacking python3-distupgrade (1:18.04.21) over (1:18.04.19) ...
Preparing to unpack .../10-snapd_2.33.1+18.04ubuntu2_i386.deb ...
Unpacking snapd (2.33.1+18.04ubuntu2) over (2.32.9+18.04) ...
Setting up python-apt-common (1.6.2) ...
Setting up libnss-systemd:i386 (237-3ubuntu10.2) ...
Setting up python3-apt (1.6.2) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Setting up systemd-sysv (237-3ubuntu10.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up udev (237-3ubuntu10.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Setting up python3-distupgrade (1:18.04.21) ...
Setting up libpam-systemd:i386 (237-3ubuntu10.2) ...
Setting up ubuntu-release-upgrader-core (1:18.04.21) ...
Setting up snapd (2.33.1+18.04ubuntu2) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
Installing new version of config file /etc/profile.d/apps-bin-path.sh ...
snapd.snap-repair.service is a disabled or a static unit, not starting it.
Setting up ubuntu-release-upgrader-gtk (1:18.04.21) ...
Setting up language-pack-en (1:18.04+20180712) ...
Setting up language-pack-en-base (1:18.04+20180712) ...
Generating locales (this might take a while)...
Generation complete.
Setting up language-pack-gnome-en (1:18.04+20180712) ...
Setting up language-pack-gnome-en-base (1:18.04+20180712) ...
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic
W: initramfs-tools configuration sets RESUME=UUID=55aa5b9d-9c45-40a7-a214-e0c27a14a430
W: but no matching swap device is available.
jane@jane-Inspiron-530s:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jane@jane-Inspiron-530s:~$ 
```

Cheers!

---

### Post by musiclover-mm on 2018-07-20
Hi ajgreeny,

Thanks for the suggestion. I didn't know the kernel I am using was withdrawn. Yes, it does boot slowly and I simply didn't know what to think being a new user. If you slick coders had any idea how dependent I, and I assume so many others, are on you it would blow your mind.

I just want you to know I am so very grateful. I truly hate MS, not because of some twisted rage about "the man" but the lack of dignity on being dependent on a snoopy, overweight, bloated sys that is so dependent on even more software from other companies just to keep the sys clean and running let alone safe to use, is just too much imposition on my time, trust, and energy. I even tried Chromebook as I can clearly see that Alphabet is the next, or currently is, the biggest thing since - I don't even know if there is a comparison. I am a Canadian and even though I know that my face, my deets, everything is in the NSA, which I don't really care about, it just becomes totally apparent once you fire up the Chromebook. Expletives *squared*. Their data collection could be more elegant and less intrusive. I returned the laptop.

So thanks for the info on booting to another kernel, I will try that out. I hope you don't mind me ranting a bit about my experience and point of view. I love my 13 year old Dell 530S. If it wasn't so unobtrusive I would have ditched it long ago. The 530's are simply ugly to look at. The only thing I ever have had a problem with it was still under warranty. The Hard Drive froze and they sent me a new one. Been humming along ever since. My sister gave me her 5 year old HP Pavilion that has Win 10 on it and it take far longer to boot than this ver of Linux. Piece of expletive. The software not the HP. I will clean it up and partition the drive and try Mint, Ubuntu and others on it. The RAM is the same size as this hard drive. Hilarious - and it still crawls with bloatware trying to update etc. Blah. I just moved and am busier than a skunk on a hot highway getting stuff done, and my brother is dying, which he wants to, so I am a tad busy.

Cheers and clean code.

Have a beautiful summer day, or sleep well if you are in the Southern Hemisphere.

---

### Post by Bashing-om on 2018-07-20
musiclover-mm; Hey hey !

You are making good progress in the migration to the linux mind set.

Malware: If you do nothing out of the ordinary desktop use you have nothing to fear on linux, as it is a closed system . You must open the system up and then take the preventive measures. I too migrated here from Windows and it took me some time to accept - and be grateful - that no protective measures are required out of the box. You have the time to learn IF you add to the system.

Old hardware; you want something light on resources - I run on a dual core Athlon system from 2007 and find that xubuntu performs admirably.
As to our present situation, with a possible incompatible kernel; Yeah, try a different kernel version from grub's boot menu;  there are a lot of reported bugs with that 4.15.0-24-Generic that affects some hardwares.

Once booted up on that other kernel we need to make sure the package manger is in a consistent state and the system is fully updated.
run - because I am terminally minded -:

From the above outputs we know we have to repair the fetching sources list file(s).
Show us the outputs of:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Once the sources are correct then update the system:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```
where 'update' syncs the data bases between your system and the mirror site:
full-upgrade: - note no space here - updates all installed packages to what is in the mirror:
-f install tries to "fix" any broken packages and reports errors .

[INDENT][INDENT]no step here for a stepper
[/INDENT][/INDENT]

---

