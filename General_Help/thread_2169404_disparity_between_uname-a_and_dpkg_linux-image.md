---
title: "disparity between uname-a and dpkg linux-image"
date: 2013-08-21
forum: General Help
---

### Post by Bashing-om on 2013-08-21
Good people;

This I fail to understand :
> 
sysop1@1204-a:~$ uname -a
Linux 1204-a 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sysop1@1204-a:~$ uname -r
3.8.0-29-generic
sysop1@1204-a:~$ dpkg -l | grep linux-image-
ii  linux-image-3.2.0-49-generic           3.2.0-49.75                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic           3.2.0-52.78                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.52.62                             Generic Linux kernel image
sysop1@1204-a:~$ 


I have always understood that "uname -a"'s output indicated the kernel that was in use. However;
I am booting version 12.04 and showing that the boot kernel is from raring ! As related by the output of "dpkg" that kernel is not installed.

Background:
I discovered this discrepancy while doing normal housecleaning - removing old kernels, ect. after doing today's updates. Be aware I am triple booting on this box with version 13.04 minimal install, precise 12.04 as standard install and lubuntu version 12.04 standard install. Lubuntu also related the same anomaly !

If one can not trust "uname", what other means is there to know what kernel is booted ?

How can "uname" report a kernel in use from a operating system not mounted ?

Where does "uname" acquire the information ? Is the related database corrupt ?

Possibly related is in the lubuntu update for grub .. that update broke my custom boot options screen . I will repair that at my earliest convenience, as to now has not hampered operations.

This totally throws me for a loop and I certainly want to know the whys and where ofs as to how this could be.

[INDENT][INDENT]insight and thoughts ??[/INDENT][/INDENT]

---

### Post by coldraven on 2013-08-22
Yesterday I was using "sudo apt-get purge linux-image-3.5.0-34-generic" to free up space in /boot.
I noticed that it re-writes grub so I guess that is where uname is looking for the info.

---

### Post by Bashing-om on 2013-08-22
Agreed ! // I restored my grubs (re-)installing and update-grub to the related systems/drives MBR ...
Now "uname" reports the correct booting kernel, in all instances.
At some point "uname" must be reading the grub.cfg file.

Discovering where why and how will keep me occupied for a long time.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-08-23
> **Bashing-om said:**
> How can "uname" report a kernel in use from a operating system not mounted ?

It cannot.
Uname does not read from grub. If I recall correctly, it uses the uname() syscall, meaning that it queries the kernel directly.

Compare the output of **uname -a** with the output of **cat /proc/version** (kernel's self-reporting) and/or with the output of **cat /var/log/dmesg | grep Linux** (kernel's boot output). You may need to go back to stored dmesg log if you have long uptime.

In other words, it's more likely that you are booting from a different kernel than you expect.

---

### Post by Bashing-om on 2013-08-23
@ ian-weisser; Thanks .. I do appreciate the guidance and the education !

It does blow my thinking away in that I may even boot 12.04's ubuntu and lubuntu on raring 13.04 kernel to a fully functional desk top. I was not aware that such a thing - with out (re-)compiling was even possible. 

All I have done after the updates broke grub is verify grub's config files and (re)install grub ...now as I say, "uname" reports booting the kernel I expect it to boot in each instance of the system I am booting. Grub is a wonder to behold.

I will continue to investigate the process in the light of your advisement.

[INDENT][INDENT]still learning even after all these years
[/INDENT][/INDENT]

---

