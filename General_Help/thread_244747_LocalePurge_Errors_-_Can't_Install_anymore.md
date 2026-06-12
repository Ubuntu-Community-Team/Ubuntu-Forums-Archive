---
title: "LocalePurge Errors - Can't Install anymore"
date: 2006-08-26
forum: General Help
---

### Post by PingunZ on 2006-08-26
```
kristof@Edgy:~$ Install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up localepurge (0.5.5) ...
cat: /tmp/fileZ6mAFk.locale.gen: No such file or directory
dpkg: error processing localepurge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 localepurge
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
 No /etc/locale.nopurge file present, exiting ...
Omg, Running Prelink ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
kristof@Edgy:~$ 
```

I can't install any software anymore :s 
I followed this guide :: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
to TIP #3

Please help !

Cheers

---

### Post by carla on 2007-03-11
Have you tried creating a blank file at /etc/locale.nopurge so that that part of the process will be pacified?

Also, try running ```
sudo dpkg-reconfigure localepurge
```, and you'll be given the shell GUI for choosing your locales again.

The info file for locales that localepurge makes nice with, by the by, is **/etc/locale.gen**, and the actual localepurge config file is **/etc/locale.nopurge**. The system uses the following as well:
> [B]
/usr/share/i18n/charmaps[/B]
Usual default charmap path.[B]
/usr/share/locale[/B]
Usual default output path. See the output from **localedef --help** for the paths used in your version.([source]("http://www.die.net/doc/linux/man/man1/localedef.1.html"))(For good measure, the man files explaining locale definitions in Linux:[LIST]
[*][http://www.die.net/doc/linux/man/man5/locale.5.html](http://www.die.net/doc/linux/man/man5/locale.5.html)
[*][http://www.die.net/doc/linux/man/man7/locale.7.html](http://www.die.net/doc/linux/man/man7/locale.7.html)
[*][http://www.die.net/doc/linux/man/man1/locale.1.html](http://www.die.net/doc/linux/man/man1/locale.1.html)
[*][http://www.die.net/doc/linux/man/man1/localedef.1.html)]("http://www.die.net/doc/linux/man/man1/localedef.1.html%29")[/LIST]Hope that helps!

---

