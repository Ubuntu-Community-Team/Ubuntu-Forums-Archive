---
title: "Symbolic link question"
date: 2017-09-01
forum: General Help
---

### Post by raleigh3 on 2017-09-01
Learning is generally fun. :-)

```
-rwxrw-r-- 1   hope   hopestaff  123   Feb 03 15:36   file.txt Here's what each part of this information means:
   [TABLE="class: mtable3 tab"]
[TR="class: tcw"]
[TD]**-**
[/TD]
 [TD]The first character represents the file type: "**-**" for a regular file, "**d**" for a directory, "**l**" for a symbolic link.
[/TD]
[/TR]
[/TABLE]

```

I only found symbolic links in 
```

lrwxrwxrwx   1 root    29 08-28-2017 vmlinuz -> boot/vmlinuz-4.4.0-93-generic
lrwxrwxrwx   1 root    32 08-28-2017 initrd.img -> boot/initrd.img-4.4.0-93-generic
lrwxrwxrwx   1 root    29 08-15-2017 vmlinuz.old -> boot/vmlinuz-4.4.0-92-generic
lrwxrwxrwx   1 root    32 08-15-2017 initrd.img.old -> boot/initrd.img-4.4.0-92-generic
```

Is it because they are rarely needed ?

---

### Post by Impavidus on 2017-09-02
They're quite common. You can find a lot of them in some directories and you can make them yourself. Take for example a look in /usr/lib:```
$ ls -l /usr/lib | grep '^l'
lrwxrwxrwx  1 root root      30 okt 14  2016 libblas.so.3 -> /etc/alternatives/libblas.so.3
lrwxrwxrwx  1 root root      15 dec 30  2013 libchm.so.1 -> libchm.so.1.0.0
lrwxrwxrwx  1 root root      15 feb  3  2017 libcpgplot.so -> libcpgplot.so.5
lrwxrwxrwx  1 root root      19 feb  3  2017 libcpgplot.so.5 -> libcpgplot.so.5.2.2
lrwxrwxrwx  1 root root      23 mrt  4 22:15 libgimp-2.0.so.0 -> libgimp-2.0.so.0.800.20
lrwxrwxrwx  1 root root      27 mrt  4 22:15 libgimpbase-2.0.so.0 -> libgimpbase-2.0.so.0.800.20
lrwxrwxrwx  1 root root      28 mrt  4 22:15 libgimpcolor-2.0.so.0 -> libgimpcolor-2.0.so.0.800.20
lrwxrwxrwx  1 root root      29 mrt  4 22:15 libgimpconfig-2.0.so.0 -> libgimpconfig-2.0.so.0.800.20
lrwxrwxrwx  1 root root      27 mrt  4 22:15 libgimpmath-2.0.so.0 -> libgimpmath-2.0.so.0.800.20
lrwxrwxrwx  1 root root      29 mrt  4 22:15 libgimpmodule-2.0.so.0 -> libgimpmodule-2.0.so.0.800.20
lrwxrwxrwx  1 root root      28 mrt  4 22:15 libgimpthumb-2.0.so.0 -> libgimpthumb-2.0.so.0.800.20
lrwxrwxrwx  1 root root      25 mrt  4 22:15 libgimpui-2.0.so.0 -> libgimpui-2.0.so.0.800.20
lrwxrwxrwx  1 root root      30 mrt  4 22:15 libgimpwidgets-2.0.so.0 -> libgimpwidgets-2.0.so.0.800.20
lrwxrwxrwx  1 root root      26 nov  8  2016 libgoffice-0.10.so.10 -> libgoffice-0.10.so.10.0.32
lrwxrwxrwx  1 root root      20 okt 14  2016 libgtkspell.so.0 -> libgtkspell.so.0.0.0
lrwxrwxrwx  1 root root      21 okt 14  2016 libkeybinder.so.0 -> libkeybinder.so.0.1.0
lrwxrwxrwx  1 root root      32 okt 14  2016 liblapack.so.3 -> /etc/alternatives/liblapack.so.3
lrwxrwxrwx  1 root root      17 okt 14  2016 libnetpbm.so.10 -> libnetpbm.so.10.0
lrwxrwxrwx  1 root root      18 okt 14  2016 liboobs-1.so.5 -> liboobs-1.so.5.0.1
lrwxrwxrwx  1 root root      14 feb  3  2017 libpgplot.so -> libpgplot.so.5
lrwxrwxrwx  1 root root      18 feb  3  2017 libpgplot.so.5 -> libpgplot.so.5.2.2
lrwxrwxrwx  1 root root      14 jul 26  2016 libpx.so.0 -> libpx.so.0.6.6
lrwxrwxrwx  1 root root      18 sep  3  2014 librarian.so.0 -> librarian.so.0.0.0
lrwxrwxrwx  1 root root      20 dec  9  2016 libsmbios_c.so.2 -> libsmbios_c.so.2.2.1
lrwxrwxrwx  1 root root      18 dec  9  2016 libsmbios.so.2 -> libsmbios.so.2.1.0
lrwxrwxrwx  1 root root      25 okt 24  2016 libspreadsheet.so -> libspreadsheet-1.12.32.so
lrwxrwxrwx  1 root root      15 nov  7  2016 libtcd.so.0 -> libtcd.so.0.0.2
lrwxrwxrwx  1 root root      16 aug  4  2016 libtidy.so.5 -> libtidy.so.5.2.0
lrwxrwxrwx  1 root root      24 okt 14  2016 libunique-1.0.so.0 -> libunique-1.0.so.0.100.6
lrwxrwxrwx  1 root root      18 okt 14  2016 libvte.so.9 -> libvte.so.9.2800.2
lrwxrwxrwx  1 root root      16 jul  6  2016 sendmail -> ../sbin/sendmail
```
In /etc/alternatives you'll find nothing but symlinks (and a README file).

---

### Post by deadflowr on 2017-09-02
I think the entire /var/run directory is one big symlink...

The symlinks in post #1 are a design of linking the latest kernel to a generic file in the top level of the root file system.
so /vmlinuz will always link to /boot/vmlinuz-latest kernel as does the initrd.img will also link to it's corresponding newest verion in boot.
It also sets links to the next newest(?) with the vmlinuz.old initrd.img.old linking to the kernel installed previous to the newest.

I cannot remember if this is an Ubuntu thing or something else.

I do know it makes setting up a custom grub a breeze since you can set the custom grub entry to look for the /vmlinuz\/initrd.img files instead of the /boot file name.
And it'll always boot the latest kernel you have installed.
Which works well if you run multi boot systems, since a multi boot system would otherwise require you to run update-grub from which ever system has grub installed. 
( which can be a total pain of extraneous work, if all you want it to reboot into which system you were just using. otherwise you might reboot into the previous kernel indefinitely)

---

