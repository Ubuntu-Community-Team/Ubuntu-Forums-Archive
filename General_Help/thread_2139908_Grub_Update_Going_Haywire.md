---
title: "Grub Update Going Haywire"
date: 2013-04-28
forum: General Help
---

### Post by jim_deadlock on 2013-04-28
I have one Ubuntu 13.04 and one Win7 on my system, but grub seems to be detecting them multiple times for some reason (see below) and I end up with two Ubuntus on my grub menu. It's not a major problem but I would like to get to the bottom of it if anyone knows why this is happening.

```
# sudo update-grub
[sudo] password for jim: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 7 (loader) on /dev/sdd1
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 7 (loader) on /dev/sdd1
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1
done



```

---

### Post by oldfred on 2013-04-28
Did you at any point edit or modify the grub scripts in/etc/grub.d?
If you made copies or backups and left the executable flag on it runs the back up also which would create duplicate entries.
Or if you renamed scripts and then a grub update restored defaults you may have both?

Post this:
ls -l /etc/grub.d

---

### Post by jim_deadlock on 2013-04-28
I've never touched /etc/grub.d in my life...

```
# ls -l /etc/grub.d
total 84
-rwxr-xr-x 1 root root  7541 Oct 14  2012 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 09:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 10:29 10_linux
-rwxr-xr-x 1 root root   242 Nov 20 04:00 10_linux_proxy
-rwxr-xr-x 1 root root   288 Nov 20 04:00 11_os-prober_proxy
-rwxr-xr-x 1 root root   683 Nov 20 04:00 12_linux_proxy
-rwxr-xr-x 1 root root 10258 Oct 14  2012 15_linux_xen
-rwxr-xr-x 1 root root   265 Nov 20 04:00 16_memtest86+_proxy
-rwxr-xr-x 1 root root   288 Nov 20 04:00 17_os-prober_proxy
-rwxr-xr-x 1 root root  1426 Oct 14  2012 18_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 17  2012 19_custom
-rwxr-xr-x 1 root root   216 Oct 14  2012 20_custom
drwxr-xr-x 2 root root  4096 Nov 17 15:12 bin
drwxr-xr-x 2 root root  4096 Nov 20 04:00 proxifiedScripts
-rw-r--r-- 1 root root   483 Apr 17  2012 README

```

---

### Post by oldfred on 2013-04-29
You have used grub customizer as all the proxy versions are from grub customizer. I have not used it, but it looks like all files are executeable. So you are getting doubles.

Grub customizer must add its own files and probably turns off execution of the standard files. Then when grub is updated, new files with executeable set are restored and you get duplicates.

I might just run grub customizer.

Or you can turn off executeable bit on the duplicates, but it looks like they also renumber some, so it is hard to tell which is the equivalent.

You would have to run this on each file.
 turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

But it looks like the standard 30_ verson of os_prober may be now 11_ and 17_ with os_prober in the name? Script runs all files with two digits and an underscore with the execute bit set.

Perhaps someone that knows grub_customizer better can comment.

Another choice is just a full uninstall of grub2 and then reinstall.
If you can boot into your install, you do not have to chroot.
 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by jim_deadlock on 2013-04-29
Thanks, Grub Customizer cleaned it up nicely! Should have thought of that myself.


Can we still mark threads as solved? Option seems to be missing...

---

### Post by oldfred on 2013-04-29
Glad that worked.

See my signature.
New screenshot version
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

