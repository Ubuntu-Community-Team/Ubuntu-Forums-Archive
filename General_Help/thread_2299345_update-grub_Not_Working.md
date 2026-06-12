---
title: "update-grub Not Working"
date: 2015-10-17
forum: General Help
---

### Post by cobalt2 on 2015-10-17
The update-grub command is not updating the grub. When I run update-grub I get the following output:
> Generating grub configuration file ...
Adding 40_Custom.
done
It says nothing about initramfs, images or headers. The only way to modify the grub is with the grub2 editor, but the changes are not persistent, when using this method.

---

### Post by sudodus on 2015-10-17
Are you running it with elevated permissions (with sudo)?

```
sudo update-grub
```

---

### Post by deadflowr on 2015-10-17
What does 
```
ls -la /etc/grub.d
```
show you?
all entries should be executable for the updater to run them.
the default should look something like this:
```
drwxr-xr-x   2 root root  4096 Jul 11 16:57 .drwxr-xr-x 144 root root 12288 Oct 17 07:53 ..
-rwxr-xr-x   1 root root  9424 Jun 26 06:16 00_header
-rwxr-xr-x   1 root root  6058 Apr 10  2014 05_debian_theme
-rwxr-xr-x   1 root root 11608 Apr 11  2014 10_linux
-rwxr-xr-x   1 root root 10412 Apr 11  2014 20_linux_xen
-rwxr-xr-x   1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x   1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x   1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Apr 11  2014 40_custom
-rwxr-xr-x   1 root root   216 Apr 11  2014 41_custom
-rw-r--r--   1 root root   483 Apr 11  2014 README



```

Or did you disable the usual entries at some point in favor of setting a custom menu entry.
In which case what you see is how it would output unless you add an echo command for the output to show something.

---

### Post by cobalt2 on 2015-10-17
Ofcourse. grub would refuse to work without it.

---

### Post by cobalt2 on 2015-10-17
ls -la /etc/grub.d:
```
total 92
drwxr-xr-x   2 root root  4096 Sep 19 10:51 .
drwxr-xr-x 145 root root 12288 Oct 17 14:55 ..
-rwxr-xr-x   1 root root  9424 Jun 26 07:16 00_header
-rwxr-xr-x   1 root root  6058 May 13 10:51 05_debian_theme
-rwxr-xr-x   1 root root 11608 Jun 26 07:16 10_linux
-rwxr-xr-x   1 root root 10412 Jun 26 07:16 20_linux_xen
-rwxr-xr-x   1 root root 11692 Jun 26 07:16 30_os-prober
-rwxr-xr-x   1 root root  1416 Jun 26 07:16 30_uefi-firmware
-rwxr-xr-x   1 root root   483 Sep 19 15:21 40_custom
-rwxr-xr-x   1 root root   455 Sep 19 10:48 40_custom~
-rwxr-xr-x   1 root root   216 Jun 26 07:16 41_custom
-rw-r--r--   1 root root   483 Jun 26 07:16 README
```

---

### Post by sudodus on 2015-10-17
What system is it?
- distro
- version
- installed or persistent live

Has it worked and stopped working, or is the system new (and has never worked)?

---

### Post by cobalt2 on 2015-10-17
I'm using Ubuntu 14.04.3 as a primary OS. update-grub was working just fine until I resized my lvm partition. Now I have these mysterious quirks. After performing the resize operation, when I booted, I noticed file system was corrupted, so I restarted, and went into recovery mode where I ran fsck. The fsck operation was successful, but there were some things that it couldn't fix.

---

### Post by sudodus on 2015-10-17
I see. This explains why it does not work. I think some file is not found or corrupted. I have very little experience of LVM (only from iso testing), and I don't know if it would be possible to repair the file system beyond what you have been doing already.

If it is possible to install and remove programs, you could try to remove and re-install **grub2-common**, the package that contains update-grub. But it is possible that something else is broken. You can also try to repair the system with the following commands

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

# added 2F4U's tips for Package Manager & Update Manager problems

Does executing these commands help?

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

This will rebuild the cache.

If it doesn't help, this forum post has additional suggestions:

http://ubuntuforums.org/showthread.php?t=1869890
```

---

### Post by cobalt2 on 2015-10-17
The lvm resize operation also relates to the problem I'm experiencing with update-initramfs mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=2299348](http://ubuntuforums.org/showthread.php?t=2299348).

---

### Post by sudodus on 2015-10-17
It is probably a similar problem with updating initramfs. I fear that several files are missing or damaged.

It is time to ***backup*** all your personal data, if you haven't done it already. Maybe also make a list of programs that you have added, and tweaks. Maybe the whole home directory or partition is good and possible to backup.

After that you can try the commands from the list in my previous post.

---

### Post by cobalt2 on 2015-10-17
After using apt-get upgrade, I get this error: 
```
grep: /boot/config-3.13.0-65-generic: No such file or directory
```
I'm going to remove config-3.13.0-65-generic. Is there a way to reinstall it without running boot-repair?

---

### Post by sudodus on 2015-10-17
Check carefully, that you are not removing the kernel version that you are using! Or at least, check if you can boot from older kernels before doing it.

We are approaching risky operations, so you should backup everything, that you cannot risk losing.

---

