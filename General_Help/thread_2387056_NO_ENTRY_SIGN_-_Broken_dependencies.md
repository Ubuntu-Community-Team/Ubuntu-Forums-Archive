---
title: "NO ENTRY SIGN - Broken dependencies"
date: 2018-03-14
forum: General Help
---

### Post by flyinghigh2 on 2018-03-14
Hi I have packages with broken dependencies and it has brought up a no entry sign in the top right corner
Is this sloweing my machine down?
how do I delete the packags
I think it is robably from when I tried to get dvds to play

many thanks in advanced

Robert

---

### Post by coffeecat on 2018-03-14
Welcome to the forum.

Let's get you started by getting you to provide some information that will help forum members help you. Open a terminal and run these commands, and then copy and paste the output into your post. You can copy in the terminal by highlighting with your mouse and then right-click -> copy. Then please enclose the output in your post between BBCode code tags. There's a link in my sig that tells you how.

First command - information about your version of Ubuntu:

```
cat /etc/lsb-release 
```

Second command - information about your broken dependencies:

```
sudo apt-get update
```

Third command - I suspect you have several third-party repositories enabled which may be the cause of your problem. This is to list them:

```
ls /etc/apt/sources.list.d/
```

---

### Post by flyinghigh2 on 2018-04-03
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"

```



```

Get:1 [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) xenial InRelease [17.6 kB]
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:5 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease                     
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [302 kB] 
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [119 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [199 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [62.4 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [467 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [746 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [421 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [201 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.4 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [77.2 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [340 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [296 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [691 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [126 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [139 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [309 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [317 kB]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [224 kB]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [617 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [570 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [248 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [241 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [321 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,972 B]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,088 B]
Fetched 7,546 kB in 18s (397 kB/s)  
Reading package lists... Done

```

```

steam.list  ubuntu-mozilla-security-ubuntu-ppa-xenial.list

```

hi sorry i havent replied sooner,, I have actually posted about the same problem elsewhere but hope you can help me on this thread. many thanks

software doesnt appear to be updating or downloading software i want

---

### Post by oldos2er on 2018-04-03
What does ```
sudo apt upgrade
``` yield?

---

### Post by flyinghigh2 on 2018-04-04
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic : Depends: linux-headers-generic (= 4.4.0.104.109) but 4.4.0.103.108 is installed
E: Unmet dependencies. Try using -f.


```

I have commands like this in the shell history;;

```

sudo add-apt-repository ppa:dani.behzi/traktor

sudo apt-get install libdvd-pkg

 sudo dpkg-reconfigure libdvd-pkg

apt-get install-f

```

!!!

---

### Post by coffeecat on 2018-04-04
> **flyinghigh2 said:**
> I have commands like this in the shell history;;

```
apt-get install-f

```



And when you ran that, you would have seen this message:

```
E: Invalid operation install-f
```

Look at the output you posted in your post #6. I have highlighted part of it:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**You might want to run ‘apt-get -f install’ to correct these.**
The following packages have unmet dependencies.
 linux-generic : Depends: linux-headers-generic (= 4.4.0.104.109) but 4.4.0.103.108 is installed
E: Unmet dependencies. Try using -f.
```

Compare with what you ran. Have you tried to run the command correctly?

---

### Post by flyinghigh2 on 2018-04-04
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```



am I doing that right?
how do I become root?
is that what you meant
sorry Im a real noob; I  was just trying to follow some instructions online

doing sudo apt-get -f install

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dvgrab ftplib3 libfltk-images1.3 libircclient1 libllvm3.8 libmircommon5
  libquicktime2 libtar0 libtcl8.5 linux-headers-4.4.0-101
  linux-headers-4.4.0-101-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-92 linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-headers-4.4.0-97
  linux-headers-4.4.0-97-generic linux-headers-4.4.0-98
  linux-headers-4.4.0-98-generic linux-image-4.4.0-101-generic
  linux-image-4.4.0-72-generic linux-image-4.4.0-77-generic
  linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic
  linux-image-4.4.0-83-generic linux-image-4.4.0-87-generic
  linux-image-4.4.0-89-generic linux-image-4.4.0-92-generic
  linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-4.4.0-97-generic linux-image-4.4.0-98-generic
  linux-image-extra-4.4.0-101-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-77-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-87-generic linux-image-extra-4.4.0-89-generic
  linux-image-extra-4.4.0-91-generic linux-image-extra-4.4.0-92-generic
  linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic
  linux-image-extra-4.4.0-97-generic linux-image-extra-4.4.0-98-generic
  snap-confine vgrabbj yoshimi-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-generic linux-headers-4.4.0-116 linux-headers-4.4.0-116-generic
  linux-headers-generic linux-image-4.4.0-116-generic
  linux-image-extra-4.4.0-116-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-headers-4.4.0-116 linux-headers-4.4.0-116-generic
  linux-image-4.4.0-116-generic linux-image-extra-4.4.0-116-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 4 to newly install, 0 to remove and 300 not to upgrade.
1 not fully installed or removed.
Need to get 69.1 MB of archives.
After this operation, 301 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-116-generic amd64 4.4.0-116.140 [22.0 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-116-generic amd64 4.4.0-116.140 [36.4 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.116.122 [1,788 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.116.122 [2,532 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-116 all 4.4.0-116.140 [9,922 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-116-generic amd64 4.4.0-116.140 [774 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.116.122 [2,514 B]
Fetched 69.1 MB in 3min 1s (381 kB/s)                                          
Selecting previously unselected package linux-image-4.4.0-116-generic.
(Reading database ... 727576 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-116-generic_4.4.0-116.140_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-116-generic (4.4.0-116.140) ...
Selecting previously unselected package linux-image-extra-4.4.0-116-generic.
Preparing to unpack .../linux-image-extra-4.4.0-116-generic_4.4.0-116.140_amd64.deb ...
Unpacking linux-image-extra-4.4.0-116-generic (4.4.0-116.140) ...
Preparing to unpack .../linux-generic_4.4.0.116.122_amd64.deb ...
Unpacking linux-generic (4.4.0.116.122) over (4.4.0.104.109) ...
Preparing to unpack .../linux-image-generic_4.4.0.116.122_amd64.deb ...
Unpacking linux-image-generic (4.4.0.116.122) over (4.4.0.104.109) ...
Selecting previously unselected package linux-headers-4.4.0-116.
Preparing to unpack .../linux-headers-4.4.0-116_4.4.0-116.140_all.deb ...
Unpacking linux-headers-4.4.0-116 (4.4.0-116.140) ...
Selecting previously unselected package linux-headers-4.4.0-116-generic.
Preparing to unpack .../linux-headers-4.4.0-116-generic_4.4.0-116.140_amd64.deb ...
Unpacking linux-headers-4.4.0-116-generic (4.4.0-116.140) ...
Preparing to unpack .../linux-headers-generic_4.4.0.116.122_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.116.122) over (4.4.0.103.108) ...
Setting up linux-image-4.4.0-116-generic (4.4.0-116.140) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-116-generic
Found initrd image: /boot/initrd.img-4.4.0-116-generic
Found linux image: /boot/vmlinuz-4.4.0-104-generic
Found initrd image: /boot/initrd.img-4.4.0-104-generic
Found linux image: /boot/vmlinuz-4.4.0-103-generic
Found initrd image: /boot/initrd.img-4.4.0-103-generic
Found linux image: /boot/vmlinuz-4.4.0-101-generic
Found initrd image: /boot/initrd.img-4.4.0-101-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found initrd image: /boot/initrd.img-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-91-generic
Found initrd image: /boot/initrd.img-4.4.0-91-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
Setting up linux-image-extra-4.4.0-116-generic (4.4.0-116.140) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-116-generic /boot/vmlinuz-4.4.0-116-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-116-generic
Found initrd image: /boot/initrd.img-4.4.0-116-generic
Found linux image: /boot/vmlinuz-4.4.0-104-generic
Found initrd image: /boot/initrd.img-4.4.0-104-generic
Found linux image: /boot/vmlinuz-4.4.0-103-generic
Found initrd image: /boot/initrd.img-4.4.0-103-generic
Found linux image: /boot/vmlinuz-4.4.0-101-generic
Found initrd image: /boot/initrd.img-4.4.0-101-generic
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found initrd image: /boot/initrd.img-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-91-generic
Found initrd image: /boot/initrd.img-4.4.0-91-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
Setting up linux-image-generic (4.4.0.116.122) ...
Setting up linux-headers-4.4.0-116 (4.4.0-116.140) ...
Setting up linux-headers-4.4.0-116-generic (4.4.0-116.140) ...
Setting up linux-headers-generic (4.4.0.116.122) ...
Setting up linux-generic (4.4.0.116.122) ...

```





the no-entry sign seems to have gone!!
will it install software now?

i also did 

```

sudo apt autoremove


```


but my machine still wont shut down
& programs are not installing

---

### Post by coffeecat on 2018-04-04
> **flyinghigh2 said:**
> sorry Im a real noob; I  was just trying to follow some instructions online

No problem. We're here to help newcomers. 

> **flyinghigh2 said:**
> ```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

You get that message if you try to run two package managers at the same time. My guess is that you were attempting to run apt or apt-get in the terminal while you still had a GUI package manager such as Software Centre or Software Updater open. Make sure you have closed any GUI package managers before attempting to run any apt or apt-get commands in the terminal.

> **flyinghigh2 said:**
> the no-entry sign seems to have gone!!
will it install software now?

The output of apt-get -f install looks good - I'm sure someone else will comment if I've missed anything. The dependency problem involving a now-old version of the kernel appears to been resolved and you have a newer kernel installed. Unless there are any other problems with the package manager, you should be able to install software now - but see below.

> **flyinghigh2 said:**
> 
i also did 

```

sudo apt autoremove


```

You didn't post the output but, assuming there were no errors, that should have removed all the old and no longer needed kernels.

> **flyinghigh2 said:**
> 
but my machine still wont shut down
& programs are not installing

I don't recall you mentioning that you couldn't shut down before. More details are needed. How do you try to shut the machine down? Do you get any error messages? And what exactly do you mean by programs not installing? What are you trying to install and how? What error messages do you get?

---

### Post by flyinghigh2 on 2018-04-04
yes i have only just noticed my machine wont restart or shut down - no error message

i have tried to install x-chat gnome and it has an icon in the menu bar on the left but just says waiting to install
same for gtk-gnutella

---

### Post by oldos2er on 2018-04-04
Could you please run  ```
sudo apt install x-chat 
``` in a terminal and copy and paste all the text output here?

---

### Post by flyinghigh2 on 2018-04-04
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package x-chat

```

---

### Post by oldos2er on 2018-04-04
I just learned x-chat isn't available on 16.04x

Try ```
sudo apt install htop 
``` instead.

---

### Post by flyinghigh2 on 2018-04-04
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package x-chat

```

---

### Post by flyinghigh2 on 2018-04-04
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  htop
0 to upgrade, 1 to newly install, 0 to remove and 299 not to upgrade.
Need to get 76.4 kB of archives.
After this operation, 215 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 htop amd64 2.0.1-1ubuntu1 [76.4 kB]
Fetched 76.4 kB in 0s (153 kB/s)
Selecting previously unselected package htop.
(Reading database ... 311600 files and directories currently installed.)
Preparing to unpack .../htop_2.0.1-1ubuntu1_amd64.deb ...
Unpacking htop (2.0.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.7.5-1) ...
Setting up htop (2.0.1-1ubuntu1) ...


```

---

### Post by flyinghigh2 on 2018-04-04
yes i installed htop

---

### Post by oldos2er on 2018-04-04
So it seems to be working ok now.

---

### Post by flyinghigh2 on 2018-04-05
yes but i have another problem,

 the machine wont shut down or restart.

should I start another thread?

---

### Post by oldos2er on 2018-04-05
That would be best, yes.

---

