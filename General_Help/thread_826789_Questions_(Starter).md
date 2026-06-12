---
title: "Questions (Starter)"
date: 2008-06-12
forum: General Help
---

### Post by HawKutu on 2008-06-12
Hello,

I've just migrate from Windows XP and still didn't know much about Unix/Linux and its stuff. Currently i've got three questions:

1. When doing 'ls -a' on the shell, it shows two files like this,
file.txt and file.txt~
What i didn't understand is the latter one having the ~ prefix and how to get rid of it.

2. I've installed AptonCD and backup and burnt the files/packages. But what will happen if when re-installing Ubuntu again, the system doesnt have AptonCD installed or does not have a network/internet connection.

3. I install both Windows XP and ubuntu 7.10 on the same machine, but unluckily Windows XP needs to be reinstalled. What will happen if i re-installed Windows XP? Will i still be able to use Ubuntu after the installation because i've heard rumors that Windows XP needs to be installed first and after that a Linux/Unix operating system. I would be very thankful if someone could explain this and suggests.

Lastly, I want to install Ubuntu from a USB drive in the future (which i don't GOOGLED yet! :p ) any relative links will be helpful.

Thank you and waiting anxiously.

---

### Post by drs305 on 2008-06-12
> **HawKutu said:**
> Hello,

I've just migrate from Windows XP and still didn't know much about Unix/Linux and its stuff. Currently i've got three questions:

1. When doing 'ls -a' on the shell, it shows two files like this,
file.txt and file.txt~
What i didn't understand is the latter one having the ~ prefix and how to get rid of it.

The ~ (tilde) symbol is usually added to files that have been automatically backed up during editing or were left by the premature termination of an application. Some editors will make a temporary backup in case something goes wrong. If the program is terminated normally and the file is either saved or discarded during exit, the file~ will be deleted. The auto-backup setting is usually found in your text editor's preferences section and seeing files with the ~ ending probably means that an 'autobackup' feature has been enabled. You can delete these files without impacting system performance but of course you lose the 'backup' file.

> 2. I've installed AptonCD and backup and burnt the files/packages. But what will happen if when re-installing Ubuntu again, the system doesnt have AptonCD installed or does not have a network/internet connection. You won't need an internet connection to restore the files on the APTonCD cd. The reinstall instructions are found here:
[User's Manual]("http://aptoncd.sourceforge.net/doc-manual.html")


> 3. I install both Windows XP and ubuntu 7.10 on the same machine, but unluckily Windows XP needs to be reinstalled. What will happen if i re-installed Windows XP? Will i still be able to use Ubuntu after the installation because i've heard rumors that Windows XP needs to be installed first and after that a Linux/Unix operating system. I would be very thankful if someone could explain this and suggests.

Reinstalling XP will mess up your grub menu. It will have to be reinstalled but there are many posts on how to fix this. Here is a link to one of them:
[How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by skymera on 2008-06-12
I believe the files with ~ are harmless backups and are hidden by default. 

I don't know about AptOnCD, sorry.

When you reinstall XP make sure it's on a new parition and not to overwrite Ubuntu.
XP WILL overwrite your MBR, it is dumb and totally ignores ohter OS's. Nice one Bill.

There are plenty of guides on how to restore GRUB, here's how to do it:

First boot the LiveCD, any live CD, 7.04, 7.10, 8.04 whatever.

Open the terminal and type

```
 grub 
```
Next you will taken to a GRUB prompt

```
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

```

That's it restart! Im not sure if you need sudo or not, give it a shot.
That little guide was for HardDisk 1 Parition 1. 

If your Ubuntu is partition 2! you will need (hd0,1).
Change accordingly.

Install Ubuntu from USB?
Like a memory stick?
I know it's possible: [ HERE ](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

I think that will put Ubuntu LiveCD on your USB which you can boot from, then install Ubuntu on any PC you like without burning CDs

Hope i helped in some way.

---

### Post by HawKutu on 2008-06-12
Thank you **drs305** and **skymera **for your time. I saved this page and all the links suggested which i'll read them later. :popcorn:

---

