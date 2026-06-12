---
title: "Options for /host partition"
date: 2008-04-26
forum: General Help
---

### Post by mikegr on 2008-04-26
Hello, 

I would like to set options for the windows partition that is mounted on /host as described in thread
[http://ubuntuforums.org/showthread.php?t=428145](http://ubuntuforums.org/showthread.php?t=428145)
I think I need to set "locale=de_DE.UTF-8" to get German umlaute working. 
Currently I cannot save files with umlaute in its name and cannot see existing one. Unfortunately /host is not listed in /etc/fstab. 
Thanks for your help. 

Mike

---

### Post by mikegr on 2008-05-02
Hi, 

Nobody knows how to set options for /host in Wubi?

Mike

---

### Post by ago on 2008-05-02
mikegr that is not too trivial since for various reasons the /host partition cannot be remounted. And that is mounted very early on in the game. So the locale is not set when that is mounted. 

Please see:

[https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682)
[http://www.ntfs-3g.org/support.html#locale](http://www.ntfs-3g.org/support.html#locale)

> Why can't I see all filenames with national characters?
...
The OS configures the setting in a too late stage during the boot process, only after the NTFS volume was already mounted.
...
Workaround: ntfs-3g supports the 'locale' mount option which can be used to set the correct language value. You can see what locales you have on your system by using the following command:
locale -a


And in theory you can pass the locale at boot using the kernel argument:

rootflags=locale=de_DE.UTF-8

But it does not seem to work too well.

I would appreciate some experiments in this regard.

---

### Post by Christian Johansson on 2008-05-03
I hope there will be a solution soon since I have all my Windows files under "My Documents" (where you usually place files in Windows) and that directory is located under a directory called "Ägare" that I can't see from my Wubi-installed Xubuntu :( .

---

### Post by ago on 2008-05-03
Yes there is a solution. 

1) save this [http://launchpadlibrarian.net/14161445/ntfs_locale](http://launchpadlibrarian.net/14161445/ntfs_locale) as /usr/share/initramfs-tools/hooks/ntfs_locale

2) run: sudo update-initramfs -u

3) edit /boot/grub/menu.lst and add rootflags=locale=XXX (XXX is your locale) to kopt

4) run: sudo update-grub

5) reboot

If it works Tormod is the guy to thank ([https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682))

---

### Post by Christian Johansson on 2008-05-04
I just tested that solution but unfortunately it didn't solve the problem.

---

### Post by ago on 2008-05-04
I am quite positive it works. One step I forgot:

1.5: sudo chmod a+x /usr/share/initramfs-tools/hooks/ntfs_locale

---

