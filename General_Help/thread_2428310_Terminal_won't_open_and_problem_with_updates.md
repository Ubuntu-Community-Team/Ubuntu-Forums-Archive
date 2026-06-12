---
title: "Terminal won't open and problem with updates"
date: 2019-10-02
forum: General Help
---

### Post by fiza92 on 2019-10-02
Hi,

Just a little bit of background first. I am new to ubuntu. I've used  it  briefly in the past in a virtualized environment. I've officially  switched  over to ubuntu now and am running into quite a few errors.

1. Ubuntu terminal won't open! I downloaded terminator and that works   but the original gnome terminal won't and I want to fix this bug. I   pressed Alt+F2 and entered gnome-terminal on xterm and it tell me   command not found. What do I do?

All I have done since I got this pc is download python 3.6. This one   comes with python2.7 already downloaded. I tried a bunch of things to   get python 3.6 to open because it was giving me errors. I'm not sure if   that switched symlink (and I am not entirely sure what that is or how  to  switch it although I have tried with the use of different codes on   different forums here).

2. I get a stop sign at the top left hand of the screen with the notice, "A problem occurred when checking for updates." [Someone else]("https://ubuntuforums.org/showthread.php?t=2365720") was running into the same issues so I did the following based on that:

```
 sudo apt autoremove 
```

```

sudo apt update
sh: 1: /usr/lib/cnf-update-db: not found
Reading package lists... Done
E: Problem executing scripts APT::Update::razz:ost-Invoke-Success  'if  /usr/bin/test -w /var/lib/command-not-found/ -a -e   /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'

```
```
sudo apt full-upgrade

Errors were encountered while processing:
 /tmp/apt-dpkg-install-j3Rg2C/11-ibus_1.5.17-3ubuntu5.2_amd64.deb
 /tmp/apt-dpkg-install-j3Rg2C/12-gir1.2-ibus-1.0_1.5.17-3ubuntu5.2_amd64.deb
 /tmp/apt-dpkg-install-j3Rg2C/39-python3-uno_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

NOTE: I also get a bunch of dkpg errors!


Then I tried ```
uname -a:

Linux fiza 4.15.0-62-generic #69-Ubuntu SMP Wed Sep 4 20:55:53 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```
Then I tried ```
lsb_release -a:
bash: /usr/bin/lsb_release: /usr/bin/python3: bad interpreter: No such file or directory

```

Following the above to [this new thread]("https://ubuntuforums.org/showthread.php?t=2365934").

I tried ```
 dpkg --audit distro-info-data 
``` which gave me nothing.

I tried ```
locate distro-info
``` and got:

```
/usr/share/distro-info
/usr/share/distro-info/debian.csv
/usr/share/distro-info/ubuntu.csv
/usr/share/doc/distro-info-data
/usr/share/doc/python3-distro-info
/usr/share/doc/distro-info-data/README.Debian
/usr/share/doc/distro-info-data/changelog.gz
/usr/share/doc/distro-info-data/copyright
/usr/share/doc/python3-distro-info/changelog.gz
/usr/share/doc/python3-distro-info/copyright
/var/lib/dpkg/info/distro-info-data.list
/var/lib/dpkg/info/distro-info-data.md5sums
/var/lib/dpkg/info/python3-distro-info.list
/var/lib/dpkg/info/python3-distro-info.md5sums
/var/lib/dpkg/info/python3-distro-info.postinst
/var/lib/dpkg/info/python3-distro-info.prerm
```

Then I tried ```
sudo apt-get install --reinstall distro-infor-data
``` and got :

```
Errors were encountered while processing:
 /var/cache/apt/archives/ibus_1.5.17-3ubuntu5.2_amd64.deb
 /var/cache/apt/archives/gir1.2-ibus-1.0_1.5.17-3ubuntu5.2_amd64.deb
 /var/cache/apt/archives/python3-uno_1%3a6.0.7-0ubuntu0.18.04.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Basically, I am at a loss. Please help!

UPDATE: I re-tried: 

```
 dpkg --audit distro-info-data 
dpkg: error: unable to open lock file /var/lib/dpkg/lock for testing: Permission denied

```

---

### Post by Skaperen on 2019-10-02
it appears there was some failure during your initial install.  in terminator can you try this command and give us the result:  [COLOR=#0000cd][FONT=courier new]**dpkg -l|fgrep ii|wc -l**[/FONT][/COLOR]

---

### Post by Skaperen on 2019-10-02
after re-reading your post more slowly this time i am wondering if you got this pc with ubuntu already on it.  if so, maybe the previous owner removed some packages to save space and made some bad choices.

---

### Post by fiza92 on 2019-10-02
Perhaps! I just bought the workstation with Ubuntu 18.04 pre-installed so I am not sure how that would be.

Tried this:
```
  dpkg -1|fgrep ii|wc -1
wc: invalid option -- '1'
Try 'wc --help' for more information.
dpkg: error: unknown option -1

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
 
```

---

### Post by Skaperen on 2019-10-02
both options on that command are lower case letter L, not digit one.

---

### Post by fiza92 on 2019-10-02
Right, sorry, I get 1535.

> **Skaperen said:**
> both options on that command are lower case letter L, not digit one.

---

### Post by Skaperen on 2019-10-02
i recommend that you get an iso for version 18.04 (preferred) or 19.04 and perform a fresh new install of ubuntu.  you can put the iso on a USB memory stick and use that if your pc can boot from USB hard drives.  it might be easier/faster for you.  i do that because my only CD/DVD drive was loaned out and not returned 5 years ago.

---

### Post by Skaperen on 2019-10-02
yeah, you have many missing packages

---

### Post by fiza92 on 2019-10-02
Okay, if that's the only way to do it, I suppose I will. I really wanted to avoid doing this. Ubuntu is the only software I have on here. I am concerned about messing up the re-installation. I will keep you and the thread updated in any case.

> **Skaperen said:**
> i recommend that you get an iso for version 18.04 (preferred) or 19.04 and perform a fresh new install of ubuntu.  you can put the iso on a USB memory stick and use that if your pc can boot from USB hard drives.  it might be easier/faster for you.  i do that because my only CD/DVD drive was loaned out and not returned 5 years ago.

---

### Post by Skaperen on 2019-10-02
this is the best way to be sure you have a good clean system.  after you install it and give it a try you probably should upgrade everything to the very latest (be sure you are connected to the internet).  gnome-terminal should work:

[COLOR=#0000cd][FONT=courier new]**sudo apt-get update && sudo apt-get -y dist-upgrade**[/FONT][/COLOR]

---

### Post by Skaperen on 2019-10-02
additional packages to install are up to you.  i believe python3.6 will be included.  i use xubuntu 18.04 and it was there for me.  you should not need terminator but if you like it, go ahead and install it.

---

### Post by TheFu on 2019-10-02
With almost all Ubuntu Desktop installers, there is a "Try Ubuntu" option, which lets you have enough of a computer to check email, pay bills, AND fix any issues with the install.  Keep that flash drive around. There are times it can be really handy.

Also, every week, run these things:
```
sudo apt update
sudo apt upgrade 
sudo apt autoremove
sudo apt autoclean

```
Create a weekly backup for anything you don't want to lose.

This "Try Ubuntu" works with the different ubuntu desktop flavors - to Mate, XFCE, LXQt, Gnome3, KDE ... and probably a few others.  I prefer to use the Ubuntu-Mate variant for system fixes.

For some disk changes/fixes, booting from a desktop ISO is the best/easiest way.

---

### Post by fiza92 on 2019-10-02
I wish I knew that there was a way to boot from desktop. I've officially wiped out the previous ubuntu and haven't been able to reinstall from the bootable USB drive. I get the following error: "0.5918971 Initramfs upacking failed: Decoding failed".

> **TheFu said:**
> With almost all Ubuntu Desktop installers, there is a "Try Ubuntu" option, which lets you have enough of a computer to check email, pay bills, AND fix any issues with the install.  Keep that flash drive around. There are times it can be really handy.

Also, every week, run these things:
```
sudo apt update
sudo apt upgrade 
sudo apt autoremove
sudo apt autoclean

```
Create a weekly backup for anything you don't want to lose.

This "Try Ubuntu" works with the different ubuntu desktop flavors - to Mate, XFCE, LXQt, Gnome3, KDE ... and probably a few others.  I prefer to use the Ubuntu-Mate variant for system fixes.

For some disk changes/fixes, booting from a desktop ISO is the best/easiest way.

---

### Post by Skaperen on 2019-10-02
how big is your disk drive?  if you repeat the install, do you get *exactly* the same error?

---

### Post by fiza92 on 2019-10-02
I created a bootable drive for Ubuntu 19.10 and I get the error 0.5918971 Initramfs unpacking failed: Decoding failed. My earlier version of ubuntu is also complete wiped out in the process.

> **Skaperen said:**
> this is the best way to be sure you have a good clean system.  after you install it and give it a try you probably should upgrade everything to the very latest (be sure you are connected to the internet).  gnome-terminal should work:

[COLOR=#0000cd][FONT=courier new]**sudo apt-get update && sudo apt-get -y dist-upgrade**[/FONT][/COLOR]

---

### Post by fiza92 on 2019-10-02
The drive is pretty big. Its 2TB HDD and 256 SSD. I just don't get past that error. It's a blank, black screen with the decoding failed error. The installation window does not even pop up. Let me try 18.04 with another USB.

So this works in a sense. I get the terminal but really nothing else works. There is no GUI.

---

### Post by TheFu on 2019-10-02
19.10 is a non-released alpha version. Really not for non-experts.  Newer isn't better.  Stay with LTS releases, especially when new.  18.04 is the current LTS.

When using the *Try Ubuntu* method to fix an existing install, be certain it is the same release for most stuff (18.04 installed, then use an 18.04 desktop *Try* out ISO), though for disk stuff is hasn't been THAT important. That might change with some of the newer file system support coming.  For other fixes, like resetting a password if you don't have sudo anymore or using a chroot to fix APT or install packages, then having the same release number matters.  Most of these issues will be self-inflicted. They aren't likely at all, but people do uninformed things all the time.  I know I did and still do. ;)

If you are installing a fresh OS, having a few partitions is good hygiene.  / should be at most 25G.  That is actually about 10G larger than should ever be needed. All the other partition sizes are up to you, but when it comes to migrating to a new version, having only 25G to deal with is a good thing.  At install time, I'd only worry about /, /home, and swap.  Any others can be added later.  Also, no need to allocate all the storage during install.  Start with just 100GB total.  Leaving at least 20% free on the SSD should drastically extend the lifespan for it too.

---

### Post by fiza92 on 2019-10-03
So I finally got 18.04 reinstalled with the bootable USB drive. I downloaded it on one of the partitions: ext4. The installation went well but now I have three ubuntu versions installed and none of them will actually boot. The first is the factory installation, the second is ubuntu 19.10, and the third is my newest 18.04 installation. Any suggestions? I could use all the help.

> **TheFu said:**
> 19.10 is a non-released alpha version. Really not for none experts.  Newer isn't better.  Stay with LTS releases, especially when new.  18.04 is the current LTS.

When using the *Try Ubuntu* method to fix an existing install, be certain it is the same release for most stuff (18.04 installed, then use an 18.04 desktop *Try* out ISO), though for disk stuff is hasn't been THAT important. That might change with some of the newer file system support coming.  For other fixes, like resetting a password if you don't have sudo anymore or using a chroot to fix APT or install packages, then having the same release number matters.  Most of these issues will be self-inflicted. They aren't likely at all, but people do uninformed things all the time.  I know I did and still do. ;)

If you are installing a fresh OS, having a few partitions is good hygiene.  / should be at most 25G.  That is actually about 10G larger than should ever be needed. All the other partition sizes are up to you, but when it comes to migrating to a new version, having only 25G to deal with is a good thing.  At install time, I'd only worry about /, /home, and swap.  Any others can be added later.  Also, no need to allocate all the storage during install.  Start with just 100GB total.  Leaving at least 20% free on the SSD should drastically extend the lifespan for it too.

---

### Post by TheFu on 2019-10-03
Factory installed?  I would have contacted them 1st and demanded a solution for a factory installed Ubuntu.

If you pay a friend to setup the system, that's completely different. 

If all the installs aren't booting, it is time to figure out if the hardware has known issues that are easily solved.  Search for "ubuntu 18.04 install {vendor + model number}"  Replace the vendor and model for your system.  Some vendors are known to have poor support for standards, like UEFI.   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  On my prior Toshiba laptop, I had to copy a file from 1 directory to another in the FAT32 partition for booting to work.  I've seen HP and some Acer laptops with similar issues. 

If you are getting passed the boot screen, then there are some other known issues for some hardware. Sometimes specific laptop+GPUs need a little help, initially.

For desktops, loop up the motherboard and GPU.

---

### Post by fiza92 on 2019-10-03
I can definitely look up hardware issues but I really didn't pay for this. And the vendor basically won't help with OS installation, Nvidia update, and the video showing. I don't think any of this is the problem any longer. 

I got it configured from Exxact Corp for work. I called their support and they did link me up with one of their pages on how to install the nvidia drivers. But that's pretty much it. They have been pretty clear with not being able to help further because their tests based on what I told them to install showed up okay. All I said was that I want ubuntu installed and gave them no further instructions. As such, they can't do much unless I ordered a pre-installed OS drive off them (which I won't). 

The good news is I deleted all of the previous installations and re-installed for the third time again. I got to the blank user login screen and not further. One of the other drives still has some sort of ubuntu on it, but its basically linux's grub. 

"Try ubuntu" also works so it can't be a hardware problem.

> **TheFu said:**
> Factory installed?  I would have contacted them 1st and demanded a solution for a factory installed Ubuntu.

If you pay a friend to setup the system, that's completely different. 

If all the installs aren't booting, it is time to figure out if the hardware has known issues that are easily solved.  Search for "ubuntu 18.04 install {vendor + model number}"  Replace the vendor and model for your system.  Some vendors are known to have poor support for standards, like UEFI.   [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  On my prior Toshiba laptop, I had to copy a file from 1 directory to another in the FAT32 partition for booting to work.  I've seen HP and some Acer laptops with similar issues. 

If you are getting passed the boot screen, then there are some other known issues for some hardware. Sometimes specific laptop+GPUs need a little help, initially.

For desktops, loop up the motherboard and GPU.

---

