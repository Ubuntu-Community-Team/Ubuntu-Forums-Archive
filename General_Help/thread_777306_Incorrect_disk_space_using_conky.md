---
title: "Incorrect disk space using conky"
date: 2008-05-01
forum: General Help
---

### Post by aiqbal on 2008-05-01
Hi all, 
For few days I am learning and trying to setup conky. Every thing works now except the disk space. For some reason I am getting same value for all the folders ie root, /home and /usr. Can some one please help. Conky config is 

${color #e9c703}File systems:
$color ROOT:  $color ${fs_used /}/${fs_size /}
$color / ${alignc}${color green}${fs_used_perc /}% ${color #888888}${fs_bar /}
$color HOME:  $color ${fs_used /home}/${fs_size /home}
$color /home ${alignc}${color green}${fs_used_perc /home}% ${color #888888}${fs_bar /home}

Ubuntu is installed on second hard disk in my computer and it shows up as /dev/sdb1. I even tried to put this in conky but it did not help. Please note that I am one week old Ubuntu user. 

Also is it normal for conky to use around 5% CPU. 

Regards,
Ather

---

### Post by aiqbal on 2008-05-02
Any ideas or suggestions please..

I donot know if this is relevant but here is my:
abc@xyz-1:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            471049580   4213080 442908488   1% /
varrun                 2026760       112   2026648   1% /var/run
varlock                2026760         0   2026760   0% /var/lock
udev                   2026760        68   2026692   1% /dev
devshm                 2026760        12   2026748   1% /dev/shm
lrm                    2026760     43044   1983716   3% /lib/modules/2.6.24-16-generic/volatile
/dev/scd0              4546392   4546392         0 100% /media/cdrom0

---

### Post by aiqbal on 2008-05-04
Bump

---

### Post by Kitheme on 2009-03-12
I've been having the same problem with fs_used not returning the correct value... it's as if the variable does not pass the argument.

The relevant portion of my .conkyrc file:

[INDENT]${offset 6}${color slate grey}MEM:  ${color }$mem / $memmax - $memperc%
${offset 6}${color slate grey}SWAP: ${color }$swap / $swapmax - $swapperc%
${offset 6}${color slate grey}ROOT: ${color }${fs_used /} / ${fs_size /}
${offset 6}${color slate grey}HOME: ${color }${fs_used /home} used[/INDENT]

The version of Conky I'm running is from the Ubuntu repositories... wonder if this might be part of the issue? Perhaps I need to roll my own?

---

