---
title: "How can I make terminal print better organized text?"
date: 2021-06-07
forum: General Help
---

### Post by sofasurfer on 2021-06-07
Sometimes when I use a terminal command to print out some info the text is not placed properly under accompanying headers. As if "text wrap" is not being properly executed. 
Example:
```
  
 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

[31;01m error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'[0m
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.50            OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 
```

Notice the headers at the top do not align with the columns

---

### Post by scorp123 on 2021-06-07
There are commands such as "column" that you can pipe output through. Example with e.g. /etc/fstab :

Without:
```
cat /etc/fstab

UUID=1574-AAD2  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub  /boot/grub      none    defaults,bind   0       0
UUID=5c832f69-37c1-4a83-a1fd-f5ef56ba2a4c       none    swap    discard 0       0
```

With:
```
cat /etc/fstab | column -t

UUID=1574-AAD2                             /boot/efi    vfat     umask=0022,fmask=0022,dmask=0022  0          1
/boot/efi/grub                             /boot/grub   none     defaults,bind                     0          0
UUID=5c832f69-37c1-4a83-a1fd-f5ef56ba2a4c  none         swap     discard                           0          0
```

---

### Post by sudodus on 2021-06-07
Thanks for telling us about [FONT=Courier New]**column**[/FONT],  scorp123 :-)

---

### Post by TheFu on 2021-06-07
> **sudodus said:**
> Thanks for telling us about [FONT=Courier New]**column**[/FONT],  scorp123 :-)


Sadly, the killer use for column is the terrible format from the **ip** command.

Remember - **route -n**?  Nice columns.
Now we're supposed to use **ip route**.  Ugly output and 50% of the columns are useless.
**ip route|column -t** is a little better, but still not as good as **route -n** which has all the useful output.

For the OP, some commands just don't output nice formatted text.  Column is certainly helpful or we can build a quick filter in whatever scripting language we like. Also, don't forget that **sort** can make for very useful output.

```
$ du -sh /var/log/*  |   sort -h
....
636K    /var/log/libvirt
912K    /var/log/cloud-init.log
1.1M    /var/log/munin
1.6M    /var/log/auth.log.1
1.7M    /var/log/btmp.1
15M     /var/log/installer
553M    /var/log/journal
```

The largest files are at the bottom. We can pick a different column to sort on.
```
$ atq | sort -hk4 -k5
2356    Mon Jun  7 19:58:00 2021 a thefu
2357    Tue Jun  8 03:28:00 2021 a thefu
2366    Tue Jun  8 09:58:00 2021 a thefu
2358    Wed Jun  9 19:58:00 2021 a thefu
2359    Thu Jun 10 03:28:00 2021 a thefu
2360    Thu Jun 10 19:58:00 2021 a thefu
2365    Fri Jun 11 02:58:00 2021 a thefu
2361    Fri Jun 11 03:28:00 2021 a thefu
2362    Sat Jun 12 06:28:00 2021 a thefu
2363    Sat Jun 12 15:58:00 2021 a thefu
2364    Sat Jun 12 19:58:00 2021 a thefu
```

Sort knows that Jun comes before Jul and how numbers/letters are ordered. Without the sort, that list of future jobs is almost randomly output. Not even sorted by the first column.

---

