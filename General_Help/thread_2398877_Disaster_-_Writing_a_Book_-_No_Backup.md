---
title: "Disaster - Writing a Book - No Backup"
date: 2018-08-18
forum: General Help
---

### Post by skyesharica on 2018-08-18
Throw me a bone! I can't backup. I use to burn CDs and DVDs with XBurn - I'm not positive but I think that's what it was called. I can't find it on the Software Download app. But I think that name is right. Can anyone help or I'm through! I've had it. And please escalate this matter as it is very important. I don't know how to push ideas up to the top.  ):P

---

### Post by mc4man on 2018-08-18
Probably is called xfburn or install brasero.

---

### Post by Impavidus on 2018-08-18
xfburn or brasero to burn cds/dvds. If comments by random Ubuntu users are worth something, xfburn is the better of the two. You can also make backups on external drives or in the cloud, but in the last case I suggest you encrypt it with a passphrase you won't forget. Or even better, do it all at the same time. A book in plain text is about 600 pages per megabyte, so storage space or bandwidth shouldn't be much of a problem.

---

### Post by The Cog on 2018-08-18
For something that has taken as long as a book does to produce, I would be inclined to keep several copies on USB sticks and have a few friends keep one just to be on the safe side.

---

### Post by rbmorse on 2018-08-18
> **The Cog said:**
> For something that has taken as long as a book does to produce, I would be inclined to keep several copies on USB sticks and have a few friends keep one just to be on the safe side.

This.

Or a dissertation.  Don't ask me how I know that.

---

### Post by skyesharica on 2018-08-18
> **mc4man said:**
> Probably is called xfburn or install brasero.

Thanks. No these words give NO results - "xfburn", "install brasero", and "brasero".

> **Impavidus said:**
> xfburn or brasero to burn cds/dvds. If comments by random Ubuntu users are worth something, xfburn is the better of the two. You can also make backups on external drives or in the cloud, but in the last case I suggest you encrypt it with a passphrase you won't forget. Or even better, do it all at the same time. A book in plain text is about 600 pages per megabyte, so storage space or bandwidth shouldn't be much of a problem.

Thanks, but where do I get the software "xfburn"? It's not in the Software app. How do I access cloud? There is nothing in Ubuntu 18.04 LTS that offers cloud. Many programs are not visible in Ubuntu 18.04 LTS.

---

### Post by sudodus on 2018-08-18
xfburn can be installed from the repository universe.

```

$ apt-cache policy xfburn
xfburn:
  Installed: 0.5.5-1
  Candidate: 0.5.5-1
  Version table:
 *** 0.5.5-1 500
        500 http://se.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

If not already available, you can connect to universe via the command line

```

sudo add-apt-repository universe

```

and then run

```

sudo apt update
sudo apt install xfburn

```

There are free storage facilities in the 'internet cloud', for example Dropbox and Google Drive. There are also 'pay' solutions/alternatives, that may or may not be more reliable.

I would recommend a solution suggested altready, to backup the valuable files locally to two or more USB drives, and store at least one of them in another house (to keep it safe in case of fire or theft).

---

### Post by bodhin2 on 2018-08-18
sky - install synaptic and do search in synaptic for xfburn.  i just did and it is there.  i installed it from there so i made sure before i posted.

---

### Post by skyesharica on 2018-08-18
> **The Cog said:**
> For something that has taken as long as a book does to produce, I would be inclined to keep several copies on USB sticks and have a few friends keep one just to be on the safe side.

Yes, that's good, but I've had problems with flash drives - the software that supports the flash memory crashes - others have had the same experience and lost all their data. But I do have flash drive backups, daily.

> This.

Or a dissertation.  Don't ask me how I know that.[INDENT]regards[/INDENT]
[INDENT]

[/INDENT]

Please don't ruin Linux with your silly nonsense.

> xfburn can be installed from the repository universe.

```

$ apt-cache policy xfburn
xfburn:
  Installed: 0.5.5-1
  Candidate: 0.5.5-1
  Version table:
 *** 0.5.5-1 500
        500 http://se.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

I've just tried that - I assume it's just the first line. I got this.:
```
mofa511@mofa511-All-Series:~$ apt-cashe policy xfburn

Command 'apt-cashe' not found, did you mean:

  command 'apt-cache' from deb apt

Try: sudo apt install <deb name>
```


> If not already available, you can connect to universe via the command line

```

sudo add-apt-repository universe

```

and then run

```

sudo apt update
sudo apt install xfburn

```

YES! I'm away. I tried all lines separately - I guessed because I don't even know that you are suppose to type in the instructions a line at a time, in the terminal. AND I'VE GOT IT - xfburn ... backup. More reliable than online cloud sort of systems. Can you please somehow send a link to the bosses. Or how can I do that? It's a hard website to venture into. I think it's important to inform the Linux community, the developers, that such a major problem has arisen. :guitar:Just in case it interests you, or I made a mistake, I put the code in.

```
mofa511@mofa511-All-Series:~$ sudo add-apt-repository universe
[sudo] password for mofa511: 
'universe' distribution component enabled for all sources.
Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://au.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8,531 kB]
Hit:3 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Get:4 http://archive.ubuntu.com/ubuntu bionic/universe Sources [9,051 kB]      
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Get:6 http://security.ubuntu.com/ubuntu bionic-security/universe Sources [14.2 kB]
Get:7 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:8 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [50.9 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [50.8 kB]
Get:10 http://security.ubuntu.com/ubuntu bionic-security/universe Translation-en [29.4 kB]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [5,784 B]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [6,962 B]
Get:13 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [8,064 B]
Get:14 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8,570 kB]
Get:15 http://au.archive.ubuntu.com/ubuntu bionic/universe Translation-en_AU [4,118 kB]
Get:16 http://au.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4,941 kB]
Get:17 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Get:18 http://au.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons [2,151 kB]
Get:19 http://au.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8,420 kB]
Fetched 49.3 MB in 2min 48s (293 kB/s)                                         
Reading package lists... Done
mofa511@mofa511-All-Series:~$ sudo apt update
Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                        
Hit:3 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
All packages are up to date.
mofa511@mofa511-All-Series:~$ sudo apt install xfburn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libburn4 libexo-1-0 libexo-2-0 libexo-common libexo-helpers libisofs6
  libjte1 libxfce4ui-1-0 libxfce4ui-2-0 libxfce4ui-common libxfce4util-bin
  libxfce4util-common libxfce4util7 libxfconf-0-2 xfconf
Suggested packages:
  devhelp
The following NEW packages will be installed:
  libburn4 libexo-1-0 libexo-2-0 libexo-common libexo-helpers libisofs6
  libjte1 libxfce4ui-1-0 libxfce4ui-2-0 libxfce4ui-common libxfce4util-bin
  libxfce4util-common libxfce4util7 libxfconf-0-2 xfburn xfconf
0 to upgrade, 16 to newly install, 0 to remove and 0 not to upgrade.
Need to get 1,646 kB of archives.
After this operation, 8,678 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libburn4 amd64 1.4.8-1 [146 kB]
Get:2 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libexo-common all 0.12.0-1 [8,988 B]
Get:3 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libexo-helpers all 0.12.0-1 [18.7 kB]
Get:4 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4util-common all 4.12.1-3 [49.8 kB]
Get:5 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4util7 amd64 4.12.1-3 [22.9 kB]
Get:6 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libexo-2-0 amd64 0.12.0-1 [92.2 kB]
Get:7 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4ui-common all 4.13.4-1ubuntu1 [158 kB]
Get:8 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 xfconf amd64 4.12.1-1 [95.9 kB]
Get:9 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfconf-0-2 amd64 4.12.1-1 [25.8 kB]
Get:10 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4ui-2-0 amd64 4.13.4-1ubuntu1 [42.8 kB]
Get:11 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libexo-1-0 amd64 0.12.0-1 [341 kB]
Get:12 http://au.archive.ubuntu.com/ubuntu bionic/main amd64 libjte1 amd64 1.20-2ubuntu2 [25.1 kB]
Get:13 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libisofs6 amd64 1.4.8-1 [189 kB]
Get:14 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4ui-1-0 amd64 4.13.4-1ubuntu1 [42.6 kB]
Get:15 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 libxfce4util-bin amd64 4.12.1-3 [5,566 B]
Get:16 http://au.archive.ubuntu.com/ubuntu bionic/universe amd64 xfburn amd64 0.5.5-1 [381 kB]
Fetched 1,646 kB in 9s (191 kB/s)                                              
Selecting previously unselected package libburn4:amd64.
(Reading database ... 161556 files and directories currently installed.)
Preparing to unpack .../00-libburn4_1.4.8-1_amd64.deb ...
Unpacking libburn4:amd64 (1.4.8-1) ...
Selecting previously unselected package libexo-common.
Preparing to unpack .../01-libexo-common_0.12.0-1_all.deb ...
Unpacking libexo-common (0.12.0-1) ...
Selecting previously unselected package libexo-helpers.
Preparing to unpack .../02-libexo-helpers_0.12.0-1_all.deb ...
Unpacking libexo-helpers (0.12.0-1) ...
Selecting previously unselected package libxfce4util-common.
Preparing to unpack .../03-libxfce4util-common_4.12.1-3_all.deb ...
Unpacking libxfce4util-common (4.12.1-3) ...
Selecting previously unselected package libxfce4util7:amd64.
Preparing to unpack .../04-libxfce4util7_4.12.1-3_amd64.deb ...
Unpacking libxfce4util7:amd64 (4.12.1-3) ...
Selecting previously unselected package libexo-2-0:amd64.
Preparing to unpack .../05-libexo-2-0_0.12.0-1_amd64.deb ...
Unpacking libexo-2-0:amd64 (0.12.0-1) ...
Selecting previously unselected package libxfce4ui-common.
Preparing to unpack .../06-libxfce4ui-common_4.13.4-1ubuntu1_all.deb ...
Unpacking libxfce4ui-common (4.13.4-1ubuntu1) ...
Selecting previously unselected package xfconf.
Preparing to unpack .../07-xfconf_4.12.1-1_amd64.deb ...
Unpacking xfconf (4.12.1-1) ...
Selecting previously unselected package libxfconf-0-2.
Preparing to unpack .../08-libxfconf-0-2_4.12.1-1_amd64.deb ...
Unpacking libxfconf-0-2 (4.12.1-1) ...
Selecting previously unselected package libxfce4ui-2-0:amd64.
Preparing to unpack .../09-libxfce4ui-2-0_4.13.4-1ubuntu1_amd64.deb ...
Unpacking libxfce4ui-2-0:amd64 (4.13.4-1ubuntu1) ...
Selecting previously unselected package libexo-1-0:amd64.
Preparing to unpack .../10-libexo-1-0_0.12.0-1_amd64.deb ...
Unpacking libexo-1-0:amd64 (0.12.0-1) ...
Selecting previously unselected package libjte1:amd64.
Preparing to unpack .../11-libjte1_1.20-2ubuntu2_amd64.deb ...
Unpacking libjte1:amd64 (1.20-2ubuntu2) ...
Selecting previously unselected package libisofs6:amd64.
Preparing to unpack .../12-libisofs6_1.4.8-1_amd64.deb ...
Unpacking libisofs6:amd64 (1.4.8-1) ...
Selecting previously unselected package libxfce4ui-1-0:amd64.
Preparing to unpack .../13-libxfce4ui-1-0_4.13.4-1ubuntu1_amd64.deb ...
Unpacking libxfce4ui-1-0:amd64 (4.13.4-1ubuntu1) ...
Selecting previously unselected package libxfce4util-bin.
Preparing to unpack .../14-libxfce4util-bin_4.12.1-3_amd64.deb ...
Unpacking libxfce4util-bin (4.12.1-3) ...
Selecting previously unselected package xfburn.
Preparing to unpack .../15-xfburn_0.5.5-1_amd64.deb ...
Unpacking xfburn (0.5.5-1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) ...
Setting up libxfce4ui-common (4.13.4-1ubuntu1) ...
Setting up libburn4:amd64 (1.4.8-1) ...
Setting up libexo-common (0.12.0-1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libxfce4util-common (4.12.1-3) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up libjte1:amd64 (1.20-2ubuntu2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up libexo-helpers (0.12.0-1) ...
Setting up libxfce4util7:amd64 (4.12.1-3) ...
Setting up libisofs6:amd64 (1.4.8-1) ...
Setting up libxfce4util-bin (4.12.1-3) ...
Setting up libexo-2-0:amd64 (0.12.0-1) ...
Setting up xfconf (4.12.1-1) ...
Setting up libxfconf-0-2 (4.12.1-1) ...
Setting up libxfce4ui-1-0:amd64 (4.13.4-1ubuntu1) ...
Setting up libxfce4ui-2-0:amd64 (4.13.4-1ubuntu1) ...
Setting up libexo-1-0:amd64 (0.12.0-1) ...
Setting up xfburn (0.5.5-1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
```

---

### Post by sudodus on 2018-08-19
Looks like you managed to install xfburn :-)

```
Setting up xfburn (0.5.5-1) ...
```

---

### Post by mc4man on 2018-08-19
> **skyesharica said:**
> 


.Can you please somehow send a link to the bosses. Or how can I do that? It's a hard website to venture into. I think it's important to inform the Linux community, the developers, that such a major problem has arisen

There are no bosses so to speak, if you feel there is a valid bug then file a bug report on launchpad.
Most likely your problems were self-inflicted unless you can show universe was removed from your sources on it's own..

---

### Post by skyesharica on 2018-08-20
Thankyou again, sudodus.

> **mc4man said:**
> There are no bosses so to speak, if you feel there is a valid bug then file a bug report on launchpad.
Most likely your problems were self-inflicted unless you can show universe was removed from your sources on it's own..

Thanks. What is "universe"? How could I have removed it by a clean install of Ubuntu 18.04 LTS? What are my "sources"? And how do I use "launchpad" - do you have a link to it?

---

### Post by Holger_Gehrke on 2018-08-20
> **skyesharica said:**
> Thanks. What is "universe"? How could I have removed it by a clean install of Ubuntu 18.04 LTS? What are my "sources"? And how do I use "launchpad" - do you have a link to it?

All the packages in the repositories are split into several sets: main,  universe, multiverse and restricted (which is a special case; those are  closed source packages that are some kind of necessary evil;  nvidia-drivers and stuff like that) in decreasing order of involvement  by Canonical, the company that develops Ubuntu and makes money from  selling software and services around it.

You probably didn't remove "universe". Packages don't come up in the "Software" application just because they are in the repositories. A lot of packages are of no interest or use to normal users (libre  office for example is split into several dozen packages, not all of  which you're going to need). Somebody - probably the package maintainer - has to write and submit some additional data for the app to know about the package. So even though "universe" was active and available in your package management, xfburn didn't show up in "Software" because nobody submitted that additional data. 'apt' and 'synaptic' don't rely on this additional data, they just show and install whatever is in the repos - it's up to you to know what package you actually need.

Your "Sources" is the list of places were the package management software looks for packages. There's a program named "Software & Updates" which allows you to set these up or you can change the underlying text file(s) in /etc/apt/sources.list and the files in the directory /'etc/apt/sources.list.d/'.

launchpad.net is the site were the Ubuntu bug-tracker and a lot of other things are hosted. A link to the bug-tracker can be found in the menu at the top of this page in the "Useful Links" drop-down menu.

Holger

---

### Post by oldfred on 2018-08-20
More info on repositories:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

It may depend on flavor of Ubuntu you install, but I do not think all repositories are enabled by default. 

My system 18.04 Ubuntu pops up periodically with a suggestion to do backups.

---

### Post by mc4man on 2018-08-20
A _ default install_  of Ubuntu will have and always had the Universe repo enabled.

---

### Post by mc4man on 2018-08-20
Just to make sure open up the Software & Updates app, make sure you have the 4 enabled on 1st screen under the Ubuntu Software tab & the 3 enabled under the Updates tab as in screen 2 .
This will assure you full access to apps & a trouble free experience down the road.

---

### Post by sudodus on 2018-08-20
Several (maybe all) versions, e.g. 14.04 LTS, 16.04 LTS, 18.04 LTS, *live-only* or *persistent live* of standard Ubuntu have *not* the Universe repo enabled by default.

But most (I think all) Ubuntu community flavours (Kubuntu, Lubuntu, ... Xubuntu) have the Universe repo installed also for live-only and persistent live systems.

---

### Post by skyesharica on 2018-08-22
> **Holger_Gehrke said:**
> All the packages in the repositories are split into several sets: main,  universe, multiverse and restricted (which is a special case; those are  closed source packages that are some kind of necessary evil;  nvidia-drivers and stuff like that) in decreasing order of involvement  by Canonical, the company that develops Ubuntu and makes money from  selling software and services around it.

You probably didn't remove "universe". Packages don't come up in the "Software" application just because they are in the repositories. A lot of packages are of no interest or use to normal users (libre  office for example is split into several dozen packages, not all of  which you're going to need). Somebody - probably the package maintainer - has to write and submit some additional data for the app to know about the package. So even though "universe" was active and available in your package management, xfburn didn't show up in "Software" because nobody submitted that additional data. 'apt' and 'synaptic' don't rely on this additional data, they just show and install whatever is in the repos - it's up to you to know what package you actually need.

Your "Sources" is the list of places were the package management software looks for packages. There's a program named "Software & Updates" which allows you to set these up or you can change the underlying text file(s) in /etc/apt/sources.list and the files in the directory /'etc/apt/sources.list.d/'.

launchpad.net is the site were the Ubuntu bug-tracker and a lot of other things are hosted. A link to the bug-tracker can be found in the menu at the top of this page in the "Useful Links" drop-down menu.

Holger

It's nice of you to go to so much trouble, but I hardly understand a word of what you are saying. I don't want to know anymore. I don't know what a 'repository' is, for example. I just think it is criminal of Ubuntu to leave out backup software and someone has to report it. Obviously launchpad is just for bugs.

> **sudodus said:**
> Several (maybe all) versions, e.g. 14.04 LTS, 16.04 LTS, 18.04 LTS, *live-only* or *persistent live* of standard Ubuntu have *not* the Universe repo enabled by default.

But most (I think all) Ubuntu community flavours (Kubuntu, Lubuntu, ... Xubuntu) have the Universe repo installed also for live-only and persistent live systems.

I don't understand that. I don't want to. Linux should not advertise that they have a working desktop system, and NOT put backup software in it. Who shall I inform?

> **mc4man said:**
> Just to make sure open up the Software & Updates app, make sure you have the 4 enabled on 1st screen under the Ubuntu Software tab & the 3 enabled under the Updates tab as in screen 2 .
This will assure you full access to apps & a trouble free experience down the road.

Thanks for that and the images. But I don't need anymore apps, and I don't want to download a lot of unnecessary stuff so I leave it as minimal with just the first item ticked. Is this right? I went through hell trying to get that information years ago. I don't know exactly how it works.

---

### Post by speartip on 2018-08-22
> **skyesharica said:**
> I don't understand that. I don't want to. Linux should not advertise that they have a working desktop system, and NOT put backup software in it. Who shall I inform?

Linux/Ubuntu has always had backup software in it. It's just that you needed to run "sudo apt update" to update the software repositories.
The fact that you seem to not want to understand it has been the issue. What you have just done to install xfburn, is absolutely basic. If you taught yourself just the basics of Linux/Ubuntu, this thread would not have even been needed.

---

### Post by QIII on 2018-08-22
OK.  I think we're done here.

Closed.

---

