---
title: "What version of Ubuntu am I REALLY running?"
date: 2014-04-23
forum: General Help
---

### Post by HappyHoward on 2014-04-23
Hello. I'm confused. I upgraded to ubuntu 14.04 Beta about a week before the official release by running update-manager -d. As far as I could tell everything went fine.
I've been running apt-get update and apt-get upgrade pretty often.
Problem is I'm still at Linux kernel 3.11 (Ubuntu 14:04 is supposed to run 3.13):

```
user@Snoopy:~$ uname -a
Linux Snoopy 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
user@Snoopy:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

```

Also I noticed that Ubuntu Software Center reports 13.10 in it's about dialog.

My sources.list looks good as far as i can tell (it references trusty like this)
```

deb http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ trusty-updates main restricted

```

Do you guys know what's going on? Any help would be greatly appreciated.

---

### Post by oldos2er on 2014-04-23
Try ```
sudo apt-get update && sudo apt-get dist-upgrade
``` If you still aren't getting the 3.13.x kernel it may be the mirror you're using hasn't gotten the updates yet.

---

### Post by Impavidus on 2014-04-23
**sudo apt-get dist-upgrade** maybe? That's what you need to intall new packages.

---

### Post by deadflowr on 2014-04-23
```
dpkg -l linux-image*
```
should list the kernels you have
the 'ii" are those currently installed.
Perhaps a grub update is in order.
```
sudo update-grub
```

Is this by any chance a multi/dual boot system?

---

### Post by HappyHoward on 2014-04-24
Thank you for your suggestions. I have tried apt-get dist-upgrade and I have also tried different mirrors.

But it seems deadflowr is correct. I ran dpkg -l linux-image* and it listed the 3.13 kernel but a 3.11 kernel was marked as installed.

I had to run off to work but I'll try update-grub when I get home.

> [COLOR=#000000]Is this by any chance a multi/dual boot system?[/COLOR]

Yes it's a win7/ubuntu dual boot system. What did you have in mind?

Now when I think back on the installation I have in the back of my head a message about grub-update failing actually.

---

### Post by deadflowr on 2014-04-24
Please post the output for 
```
sudo update-grub
```
([USE CODE TAGS]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"))
From there we can see what and if any errors there are, and hopefully deliver a quick fix.

---

### Post by HappyHoward on 2014-04-24
Ok.

```

user@Snoopy:~$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                  Architecture             Description
+++-======================================-========================-========================-==================================================================================
un  linux-image                            <none>                   <none>                   (no description available)
un  linux-image-3.0                        <none>                   <none>                   (no description available)
rc  linux-image-3.11.0-12-generic          3.11.0-12.19             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-13-generic          3.11.0-13.20             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-14-generic          3.11.0-14.21             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-15-generic          3.11.0-15.25             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-17-generic          3.11.0-17.31             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic          3.11.0-18.32             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-19-generic          3.11.0-19.33             amd64                    Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-23-generic          3.13.0-23.45             amd64                    Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic    3.11.0-12.19             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-13-generic    3.11.0-13.20             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic    3.11.0-14.21             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic    3.11.0-15.25             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic    3.11.0-17.31             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic    3.11.0-18.32             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic    3.11.0-19.33             amd64                    Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-23-generic    3.13.0-23.45             amd64                    Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP

```

```

user@Snoopy:~$ sudo update-grub
[sudo] password for user: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1
done

```

---

### Post by mörgæs on 2014-04-24
You have a bunch of old kernels lying around. A reboot and **sudo apt-get autoremove** will free a lot of space.

---

### Post by deadflowr on 2014-04-24
You only have to 3.11 kernel installed, the rc in the dpkg output means those others were removed, but I believe the config files for them remain.

After running the autoremove command posted above, try
```
sudo apt-get update
```
and then 
```
sudo apt-get dist-upgrade
```

and when you do, look over the packages that it says willl be installed.
Hopefully, the 3.13 series kernel will be.

It's possible you might need to actually install the 3.13 series kernel.

If the output for dist-upgrade confuses you post it, using code tags again.
(you can abort the dist-upgrade by pressing "n")

---

### Post by HappyHoward on 2014-04-24
I think I only have one kernel installed, linux-image-3.11.0-19-generic. At least that's the only one marked ii when I run
```
dpkg -l linux-image*
```

Anyway the problem is it's the wrong kernel. Since I'm on 14.04 I should have linux-image-3.13.0-23-generic installed instead.

Edit: I didn't see your post there deadflowr. I'll try what you suggested.

---

### Post by HappyHoward on 2014-04-24
```

user@Snoopy:~$ sudo apt-get autoremove
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

user@Snoopy:~$ sudo apt-get update

output not included.

```

dist-upgrade only updated google-chrome.

```

user@Snoopy:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48,3 MB of archives.
After this operation, 223 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 34.0.1847.132-1 [48,3 MB]
Fetched 48,3 MB in 11s (4 076 kB/s)                                                                                                                                               
(Reading database ... 209702 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_34.0.1847.132-1_amd64.deb ...
Unpacking google-chrome-stable (34.0.1847.132-1) over (34.0.1847.116-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up google-chrome-stable (34.0.1847.132-1) ...

```

Btw I found out that I do have the package linux-headers-3.13.0-23-generic and linux-headers-3.13.0-24-generic installed

```

user@Snoopy:~$ ls /lib/modules
3.11.0-19-generic  3.13.0-23-generic  3.13.0-24-generic
user@Snoopy:~$ dpkg -S /lib/modules/3.13.0-23-generic/
linux-headers-3.13.0-23-generic: /lib/modules/3.13.0-23-generic
user@Snoopy:~$ dpkg -S /lib/modules/3.13.0-24-generic/
linux-headers-3.13.0-24-generic: /lib/modules/3.13.0-24-generic



```

---

### Post by mörgæs on 2014-04-24
> **deadflowr said:**
> You only have to 3.11 kernel installed, the rc in the dpkg output means those others were removed, but I believe the config files for them remain.


Ok, thanks for pointing that out. Makes more sense now.

---

### Post by deadflowr on 2014-04-24
You don't seem to have the linux-image-generic package installed.
Perhaps```

sudo apt-get install linux-image-generic linux-headers-generic
```
see if that helps.

Maybe post the output of that command, first to get a double check on what's going to be installed.
I would think it will pull in the 3.13.0.24 kernel, but you never know.

---

### Post by HappyHoward on 2014-04-25
That helped!

```

user@Snoopy:~$ uname -a
Linux Snoopy 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

Thank you very much for your help =)

---

