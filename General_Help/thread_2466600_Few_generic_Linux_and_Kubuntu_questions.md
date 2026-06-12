---
title: "Few generic Linux and Kubuntu questions"
date: 2021-08-31
forum: General Help
---

### Post by keijo-kukka on 2021-08-31
Hi guys,
I consider myself still a newbie in Linux and I've mostly used Kubuntu for only around two years (version 20.04. Kernel: x86_64 Linux 5.6.17-050617-generic).

I try to learn more about Linux as often as I can, and I have few pretty basic generic Linux questions. May I have some help please?

1. I happen to use pCloud public cloud service and its own client, which after installation creates automatically directory in path home\*username*\pCloudDrive.
In this path - I believe Kubuntu itself - creates automatically a directory called "System Volume Information" and inside this directory two files are being generated automatically called: IndexerVolumeGuid and WPSettings.dat. What is the purpose of this directory and those files? Is this directory and the files in any means necessary? If I delete them, they will spawn again at least after next reboot.

2. I've recently educated myself with different Linux packet management variations and file formats and I've learned differences between .deb format, Appimage, Snap and Flatpak. But I've also found file (application) format, simply recognized as "executable" at least in Kubuntu / KDE Plasma. App is a backup SW called "Borg backup". What is this simply "executable" called file format? What kind of attributes / features are related to this format? It's not any of the previously mentioned app formats, or is it? I would like to understand more about this.

3. I try to avoid working as a root user, unless there is a good reason for that (e.g. to avoid messing my system). Does it make any difference, if I happen to install a specific application as a *root user? *(so not using the sudo command) Would this particular app gain any elevated rights compared if I install it as non-root user and use sudo?

4. I've grown very fond of Kali Linux's terminal layout, appearance, functionality and pretty much everything. What is the name of Kali's terminal and can I install it in Kubuntu as well?

Thank you very much!!

---

### Post by grahammechanical on 2021-08-31
The English language often gives different meanings to words that are pronounced and spelt the same way. The word "format" also has different meanings in Linux. A Package Manager format is different to a file format. You can read about file formats in Linux here:

[http://www.linfo.org/file_format.html](http://www.linfo.org/file_format.html)

> What is this simply "executable" called file format? What kind of attributes / features are related to this format?

I do not think that the file is in a special "executable" format but that it is been given permission to execute or run. Programs, applications and scripts cannot run unless given permission to execute. 

If I understand you correctly the file you are referring to is a backup application. It would have to be set to be executable otherwise it would not run and perform a backup. Borg backup might be a Linux binary file (bin format) or it might simply be a script (text file format) that runs a sequence of Linux commands. Launch Borg backup and the program runs as it has been programmed to run. If it is a script then the sequence of Linux commands are executed as scripted.

I give an example that I am familiar with. In the Grub menu under Advanced options for Ubuntu if we select a Linux kernel with recovery mode then Linux will load and run an application called Whiptail. This application paints the recovery menu on the screen. The menu items are scripts that are executable. Select an menu item and the scripts activate and runs particular Linux commands. Whiptail and the scripts have to be executable for recovery mode to be of any us.

It might be wrong about all this but I have given my opinion.

Regards

---

### Post by TheFu on 2021-08-31
1. That's a pCloud question, not an Ubuntu question.  No clue what **System Volume Information** is. That isn't a Linux thing.

2. Every computer has binary code that runs on a specific OS, using a specific libc, with a specific CPU.  For example, a binary (compiled) program for amd64 Ubuntu isn't the same format as an ARM64 UBuntu format or a Windows10 compiled program.  If you use the "file" command ... the specific binary type is show. A few examples:
```
$ file /bin/ls
/bin/ls: ELF 64-bit LSB shared object, **x86-64**, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=2f15ad836be3339dec0e2e6a3c637e08e48aacbd, for GNU/Linux 3.2.0, stripped

$ file /bin/ls
/bin/ls: ELF 32-bit LSB pie executable, **ARM**, EABI5 version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-armhf.so.3, for GNU/Linux 3.2.0, BuildID[sha1]=0db49c0d51e238f0362e4d0c1ab91709a0279406, stripped

$ file /snap/core20/1081/usr/lib/python3/dist-packages/setuptools/cli.exe
/snap/core20/1081/usr/lib/python3/dist-packages/setuptools/cli.exe: [B]PE32 executable (console) Intel 80386, for MS Windows
[/B]
```
That was run against binaries for 3 different computer architectures. If you want to know more, take a beginning C programming class.  

3. sudo or root.  There is no reason on Ubuntu to ever use a root login.  It gets most people into all sorts of problems and breaks things.  Additionally, NEVER, EVER, run any GUI program as root or with sudo.

4. Kali Linux is a hacking distro. Learn to check the process table to know any commands being run.  Join a DefCon group for help with that. If you really want to know more about Linux, [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php) and work through that book a chapter each week. Do all the exercises AND all the "extra" questions too.  This isn't about being a programmer, but it will fill in some clear gaps in knowledge and all the how-tos and copy/pasting will never teach.

About 50% of the stuff I do on Linux isn't in any book or training.  I merge what I learned from books and examples, to fit my needs and create something completely new.  Seeing techniques used by other people is also great for learning.  For example, to create a flash install drive with Ubuntu on it, I can use either of these commands:
```
sudo dd    if=/tmp/ubuntu-xyz.iso      of=/dev/sdz      bs=1M
```
or
```
sudo cp     /tmp/ubuntu-xyz.iso       /dev/sdz
```
which is easier? They both result in exactly the same thing.  I'm lazy. The 2nd is much easier.  Think I learned that from Herman in these forums.

---

### Post by HermanAB on 2021-09-01
Regarding the indexer files:
Some Linux desktop systems have a built-in search function that makes it easier(?!) to find stuff.  The KDE indexer runs periodically, generates those weird files to speed up the searching and the search function is somewhat useful nowadays, so you can leave it alone.

---

### Post by HermanAB on 2021-09-01
Regarding file types:
UNIX systems don’t care much about the filenames.  You can name a JPG picture textfile.txt and it will still work.  The file type is figured out by a little program called - wait for it - drum roll - file.
A complication exists for the Mail Extensions standard called MIME.  This is a Windows monstrosity that wormed its way into Linux desktop systems.  So sometimes, with some programs,  the filename extensions do matter.
Whether a file is executable or not, is marked by a flag in the file system.  So you can take an executable program and mark it as not executable and then sleep in peace that something or someone will not be able to accidentally run it.

---

### Post by Impavidus on 2021-09-01
Two notes not related to your questions:
> **keijo-kukka said:**
> I consider myself still a newbie in Linux and I've mostly used Kubuntu for only around two years (version 20.04. Kernel: x86_64 Linux 5.6.17-050617-generic).That's not the default kernel, which would be either 5.4.0-81 or 5.11.0-27. You may have a good reason for that, but, as you're a newbie, I want to remind you that one should only install a non-standard kernel with good reason and make sure it's properly updated.

> 1. I happen to use pCloud public cloud service and its own client, which after installation creates automatically directory in path home\*username*\pCloudDrive.
The backslash character (\) is in Linux a normal character that can be used in filenames. It's not, like in Windows, a separator used between directories. Only the forward slash (/) is used like that.

---

### Post by timgood on 2021-09-01
As far as I'm aware, System Volume Information is created by Windows - so if a Windows OS has previously or  recently accessed that folder, it will be created. In  Windows it is a hidden folder and helps the OS index contents. It is visible in Linux and can be ignored or deleted - but will be recreated should you visit the folder within a Windows OS.

---

### Post by TheFu on 2021-09-01
> **timgood said:**
> As far as I'm aware, System Volume Information is created by Windows - so if a Windows OS has previously or  recently accessed that folder, it will be created. In  Windows it is a hidden folder and helps the OS index contents. It is visible in Linux and can be ignored or deleted - but will be recreated should you visit the folder within a Windows OS.

Further, that name would only appear on NTFS formatted file systems, which are not POSIX compliant by default with what Unix/Linux expect.  chmod and chown don't work with NTFS.   So, you might want to run

```
chmod a+x some-program.exe
```
but if it is located on NTFS storage, that command will be ignored.

---

### Post by keijo-kukka on 2021-09-06
Thank you all for providing helpful advises!! I surely appreciate A LOT of your help!! &#65533;&#65533;

1. I now believe, that the files in pCloud directory I mentioned are being generated by Windows and not my Linux, whenever I access pCloud via Windows. Thank you especially @timogood and @TheFu.

2. I'm still uncertain what is the file type of the "borg-backup" file I mentioned (it is set to run as "executable", it is a backup application). 
I did run the "file" command, but it didn't tell me much about the file type:
```

borg-linux64: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=373ec5dee826653796e927ac3d65c9a8ec7db9da, stripped
```
It didn't tell me whether it is e.g. Appimage file, with all the required dependencies, or e.g. Snap or Flatpak.
When using KDE Plasma GUI and clicking properties of the file, it just tells that the type is "executable" and nothing more.

3. I guess, that it doesn't really matter if I use *sudo* command or change my user account to *root* when *I simply need to update my Linux and all the installed applications*. I guess they both get job done, but if I execute anything (e.g. updates) as a root user, I should exit root user account when ever I get my job done. I understand the risks related to staying constantly as a root user.

4. I've found on my own, that the default terminal in Kali is called "qterminal". I also found that qterminal comes preinstalled in Kubuntu. However, it certainly does not look & feel as Kali's default qterminal, so I guess Kali's qterminal comes already heavily pre-customized. I guess I should next try to customize my Kubuntu qterminal to function the same exact way as Kali's qterminal. Easier said than done...

Thanks once again.

---

### Post by TheFu on 2021-09-06
Please don't change the fonts just to chagne the fonts.  Just use the defaults - use the quote/code and perhaps color options to bring out ... er ... quoted text, code/terminal commands AND output, and really important text.

> **keijo-kukka said:**
> 2. I'm still uncertain what is the file type of the "borg-backup" file I mentioned (it is set to run as "executable", it is a backup application). 
I did run the "file" command, but it didn't tell me much about the file type:
```
borg-linux64: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=373ec5dee826653796e927ac3d65c9a8ec7db9da, stripped
```It didn't tell me whether it is e.g. Appimage file, with all the required dependencies, or e.g. Snap or Flatpak.
When using KDE Plasma GUI and clicking properties of the file, it just tells that the type is "executable" and nothing more.

Appimage files will have AppImage as the suffix.  Snaps are expanded and mounted to loop devices, so the files inside that loop mount location will be part of 1 snap.  I've never used a flatpak and avoid snaps whenever possible.  I use appimages because they don't get in the way for seldom used programs.

That file command tells us a bunch.  Compare that output to what an appimage file generates.

> **keijo-kukka said:**
> 
3. I guess, that it doesn't really matter if I use *sudo* command or change my user account to *root* when *I simply need to update my Linux and all the installed applications*. I guess they both get job done, but if I execute anything (e.g. updates) as a root user, I should exit root user account when ever I get my job done. I understand the risks related to staying constantly as a root user.
Only experts with years of experience can fully understand the risks. Some of the risks are distribution specific, since Ubuntu just changed their default handling for **sudo** vs **sudo -H**.  sudo -H solves some issues, but breaks other things.

> **keijo-kukka said:**
> 4. I've found on my own, that the default terminal in Kali is called "qterminal". I also found that qterminal comes preinstalled in Kubuntu. However, it certainly does not look & feel as Kali's default qterminal, so I guess Kali's qterminal comes already heavily pre-customized. I guess I should next try to customize my Kubuntu qterminal to function the same exact way as Kali's qterminal. Easier said than done...
Program settings are normally placed into ~/.config/{programname}/ or under /etc/{programname} or in /usr/share/{programname} .... so if you check some other distro for those settings and copy them over to your distro ... probably best to not touch global confif files - just drop them into your ~/.config/{programname}/  and I'd bet that will give you the stuff you prefer ... provided there aren't fonts or backgrounds or specific themes connected.  Those are also under  /usr/share/  and you can probably find a theme directory inside your HOME.  I really don't know, since I've been rockin' fvwm as my WM the last few years .... it is just as small and fast as it was in 1995. Simple, complex, yet beautiful.  YMMV.  Everyone as slightly different tastes.

You do understand that programs that use the Qt toolkit will load about 1G of junk into RAM whenever you run a program that starts with a 'q' if your system isn't LXQt or KDE-based, right?  On a 2GB RAM system, that could be extremely bad.  Of systems with more RAM, how bad it might be depends on the amount of RAM already used and how many other programs used do that.  

The same is true for programs that begin with a 'g' on non-GTK systems. On those, we'd want to prefer Qt-based programs over GTK to limit the RAM used because both Qt and GTK are loaded.

---

