---
title: "How safely remove my old kernels on my Kubuntu 18 ?"
date: 2021-08-08
forum: General Help
---

### Post by petrogromovo on 2021-08-08
Hello,
I search for some safe way to remove my old kernels to free some space on my Kubuntu 18,
but finding in net some possible(and safe) way to do it, I got unexpected results :

Firslty I got number of old kernels:
```
$ sudo dpkg --list | egrep -i --color "linux-image|linux-headers" | wc -l
10

```
Output them
```
$ sudo dpkg --list | egrep -i --color "linux-image|linux-headers"
ii  linux-headers-4.15.0-121                        4.15.0-121.123                                                     all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-121-generic                4.15.0-121.123                                                     amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-128                        4.15.0-128.131                                                     all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-128-generic                4.15.0-128.131                                                     amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                           4.15.0.128.115                                                     amd64        Generic Linux kernel headers
rc  linux-image-4.15.0-118-generic                  4.15.0-118.119                                                     amd64        Signed kernel image generic
ii  linux-image-4.15.0-121-generic                  4.15.0-121.123                                                     amd64        Signed kernel image generic
ii  linux-image-4.15.0-128-generic                  4.15.0-128.131                                                     amd64        Signed kernel image generic
rc  linux-image-4.15.0-20-generic                   4.15.0-20.21                                                       amd64        Signed kernel image generic
ii  linux-image-generic                             4.15.0.128.115                                                     amd64        Generic Linux kernel image

```

But trying to remove them nothing was found :
```
$ sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.

```

$ uname -a
```
Linux AtHome 4.15.0-128-generic #131-Ubuntu SMP Wed Dec 9 06:57:35 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

Why so and which is the valid way ?

---

### Post by ActionParsnip on 2021-08-08
What is the output of:
```

dpkg -l | awk {'print $2'} | grep linux-image | egrep -v 'header|extra' 

```
The headers aren't the kernels

---

### Post by Impavidus on 2021-08-08
You haven't got 10 old kernels. You've got 10 kernel-related packages (kernels, kernel headers, metapackages). Of those 10 packages, only 2 are old. Those are the packages marked as rc, which means they have already been removed, but some configuration files may be left. As it happens, kernel packages have no config files that get left behind, so purging those packages will only clear clutter, not disk space.

apt-get autoremove --purge will purge old kernel packages, but it won't purge packages that have already been removed. The easy way to get rid of those two packages is listing them manually on the command line:```
sudo apt purge linux-image-4.15.0-118-generic linux-image-4.15.0-20-generic
```That won't save a lot of space though.

---

### Post by TheFu on 2021-08-08
The easiest way for GUI people is to use Synaptic.  Find the installed kernels and purge all but the last 2.  Then do **sudo apt autoremove** to have the system remove any dependencies (headers, modules) to those now-gone kernels.

If you want to get fancy, you can use package name globbing and remove, but it you get the wrong names, like the kernels you didn't mean to remove/purge, it will be a bad day. If you don't put at least the current kernel back, your next boot will fail.

Synaptic is the GUI way and probably easiest. Use search or find to get the list.

I'm not a GUI person, so using Action's script:
```
$ dpkg -l | awk {'print $2'} | grep linux-image | egrep -v 'header|extra'
linux-image-5.4.0-7[COLOR="#FF0000"]0[/COLOR]-generic
linux-image-5.4.0-7[COLOR="#FF0000"]2[/COLOR]-generic
linux-image-5.4.0-7[COLOR="#FF0000"]3[/COLOR]-generic
linux-image-5.4.0-7[COLOR="#FF0000"]4[/COLOR]-generic
linux-image-5.4.0-77-generic
linux-image-5.4.0-80-generic
linux-image-generic-hwe-18.04
```
provides a list.  I want to purge 70-74.

```
sudo apt purge linux-image-5.4.0-70-generic  linux-image-5.4.0-72-generic  linux-image-5.4.0-73-generic  linux-image-5.4.0-74-generic
```

And they are gone.  There is a way to glob the package names.
```
sudo apt purge 'linux-image-5.4.0-7[0-4]-generic'
```
The single quotes are necessary.

---

### Post by petrogromovo on 2021-08-11
I got :
> $ dpkg -l | awk {'print $2'} | grep linux-image | egrep -v 'header|extra'
linux-image-4.15.0-118-generic
linux-image-4.15.0-121-generic
linux-image-4.15.0-128-generic
linux-image-4.15.0-20-generic
linux-image-generic


---

### Post by TheFu on 2021-08-11
```
sudo apt purge  linux-image-4.15.0-20-generic  linux-image-4.15.0-118-generic
```

Keep the last 2 kernels.

200MB is a little tight to have 3 kernels installed.

On a system here, 2 kernels is using 165MB in /boot/. I have my /boot partition sized to be 720MB, but 500MB would be what I use the next install.

You can also try 
```
sudo apt autoremove --purge
```
That might work.

---

