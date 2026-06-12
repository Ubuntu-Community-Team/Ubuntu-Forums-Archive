---
title: "Updating the system and kernels the old way plus some tips"
date: 2017-07-21
forum: General Help
---

### Post by Cavsfan on 2017-07-21
If you're like some of us that do not want things to be automagically updated behind the scenes and have purged or disabled **unattended-upgrades**.

When a new kernel gets installed before I do a reboot, I purge the 3rd oldest kernel.
I prefer a purge of the kernel instead of letting auto-remove do it because that will leave config files, while purging the kernel takes the config files too.
If I do this after a reboot, another reboot will be required and this method saves that 2nd reboot.

So, I added an alias to **~/.bashrc** that lists the kernels so I know for sure which one to delete.
I also keep a text file of the kernels making this command easier to enter when the kernel is initially installed

I added this alias:
```
alias list-kernels='dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"'

```

All you have to do it edit the ~/.bashrc file and close the terminal if you have one open, then once you re-open it, the alias will work.
So since the latest kernel was just installed:
```
4.10.0-28-generic
```

The output of that alias looks like this:
```
cavsfan@cavsfan-Le-Beast:~$ list-kernels
ii  linux-generic                                 4.10.0.28.29                             amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.10.0-24                       4.10.0-24.28                             all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-24-generic               4.10.0-24.28                             amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-26                       4.10.0-26.30                             all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-26-generic               4.10.0-26.30                             amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-28                       4.10.0-28.32                             all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-28-generic               4.10.0-28.32                             amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.10.0.28.29                             amd64        Generic Linux kernel headers
ii  linux-image-4.10.0-24-generic                 4.10.0-24.28                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-26-generic                 4.10.0-26.30                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-28-generic                 4.10.0-28.32                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-24-generic           4.10.0-24.28                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-26-generic           4.10.0-26.30                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic           4.10.0-28.32                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.10.0.28.29                             amd64        Generic Linux kernel image


```

Notice only ii (installed) and no rc (residual config)is in the first column indicating a config file.

Then I know to purge the 24 kernel.

```
sudo apt purge linux-headers-4.10.0-24 linux-headers-4.10.0-24-generic linux-image-4.10.0-24-generic linux-image-extra-4.10.0-24-generic
```

This is the magic line I like seeing in the terminal output:
> Purging configuration files for linux-image-4.10.0-24-generic (4.10.0-24.28) ...

So, now I have just 2 kernels: one current and one backup:
```
cavsfan@cavsfan-Le-Beast:~$ list-kernels
ii  linux-generic                                 4.10.0.28.29                             amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.10.0-26                       4.10.0-26.30                             all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-26-generic               4.10.0-26.30                             amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-28                       4.10.0-28.32                             all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-28-generic               4.10.0-28.32                             amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.10.0.28.29                             amd64        Generic Linux kernel headers
ii  linux-image-4.10.0-26-generic                 4.10.0-26.30                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-28-generic                 4.10.0-28.32                             amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-26-generic           4.10.0-26.30                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic           4.10.0-28.32                             amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.10.0.28.29                             amd64        Generic Linux kernel image


```

I can't take credit for this as I learned the majority of this from people in this forum.

---

### Post by #&amp;thj^% on 2017-07-22
> **Cavsfan said:**
> If you're like some of us that do not want things to be automagically updated behind the scenes and have purged or disabled **unattended-upgrades**.

When a new kernel gets installed before I do a reboot, I purge the 3rd oldest kernel.
[B]I prefer a purge of the kernel instead of letting auto-remove do it because that will leave config files, while purging the kernel takes the config files too.
If I do this after a reboot, another reboot will be required and this method saves that 2nd reboot.[/B]

This is the magic line I like seeing in the terminal output:
> Purging configuration files for linux-imageXXX




I can't take credit for this as I learned the majority of this from people in this forum.
I also prefer this method, makes for a continual  healthy system.;)
We've used this for some time now with good results.:) (Haven't we Cavsfan? :D)

---

### Post by Cavsfan on 2017-07-22
> **1fallen said:**
> I also prefer this method, makes for a continual  healthy system.;)
We've used this for some time now with good results.:) (Haven't we Cavsfan? :D)

Yes we have :P !

Seeing those residual config files listed with the installed kernel packages used to confuse the heck out of me!
I think autoremove is a good idea but, I never use it because of that. :)

Maybe one day the programmers that maintain that will consider taking out the rc files too.
I cannot see any use for them anyway once the packages have been deleted.

---

### Post by Cavsfan on 2017-08-16
The magic I like seeing in terminal output when I purge a kernel: 

```
Purging configuration files for linux-image-extra-4.11.0-10-generic (4.11.0-10.15) ...
Purging configuration files for linux-image-4.11.0-10-generic (4.11.0-10.15) ...



```

:guitar:

---

### Post by Tadaen_Sylvermane on 2017-08-16
Could just do

```
apt --purge autoremove 
```

Saves a bit, works great.

---

