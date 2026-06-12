---
title: "inodes are full again Please check me"
date: 2016-02-08
forum: General Help
---

### Post by jeannacav on 2016-02-08
I had this problem about a year ago and did not expect it to re-happen.
Following advice given on another thread, I have produced the following information:
```
ginala@ginala-Aspire-5517:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   12G  6.0G  66% /
udev            866M  4.0K  866M   1% /dev
tmpfs           175M  788K  175M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            874M  232K  874M   1% /run/shm
/dev/sda2       125G   66G   53G  56% /home
ginala@ginala-Aspire-5517:~$ df -i
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1224000 1219234    4766  100% /
udev            221532     470  221062    1% /dev
tmpfs           223728     389  223339    1% /run
none            223728       3  223725    1% /run/lock
none            223728      12  223716    1% /run/shm
/dev/sda2      8306688   27675 8279013    1% /home
```

and then

```
ginala@ginala-Aspire-5517:~$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-57-generic               3.2.0-57.87                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-80-generic               3.2.0-80.116                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-82-generic               3.2.0-82.119                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-83-generic               3.2.0-83.120                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-84-generic               3.2.0-84.121                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-85-generic               3.2.0-85.122                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-86-generic               3.2.0-86.124                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-87-generic               3.2.0-87.125                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-88-generic               3.2.0-88.126                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-89-generic               3.2.0-89.127                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-90-generic               3.2.0-90.128                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-91-generic               3.2.0-91.129                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-92-generic               3.2.0-92.131                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-93-generic               3.2.0-93.133                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-94-generic               3.2.0-94.134                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-95-generic               3.2.0-95.135                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-97-generic               3.2.0-97.137                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-98-generic               3.2.0-98.138                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                        3.2.0.98.114                            Generic Linux kernel image
ginala@ginala-Aspire-5517:~$ 

```

So, now is where I need help.
I don't know which to eliminate or how.

Please type it for me so I know it is correct!

thanks
jeanna

---

### Post by dragonfly41 on 2016-02-08
This is a bookmarked site re: inodes ...

[http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](http://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)

---

### Post by jeannacav on 2016-02-08
Hi
I got no reply from the first line.
I need typing help so I need to be able to copy and paste when I use a terminal.

thanks for your suggestion.

jeanna

---

### Post by ian-weisser on 2016-02-08
Try
```
sudo apt-get autoremove
```
If it does not work, please show us the entire output so we will understand why.

---

### Post by jeannacav on 2016-02-08
> **ian-weisser said:**
> Try
```
sudo apt-get autoremove
```
If it does not work, please show us the entire output so we will understand why.

Hi
```
ginala@ginala-Aspire-5517:~$ sudo apt-get autoremove         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-98-generic but it is not installed
E: Unmet dependencies. Try using -f.
ginala@ginala-Aspire-5517:~$ 

```
and then
```
ginala@ginala-Aspire-5517:~$ -f
-f: command not found
ginala@ginala-Aspire-5517:~$ 

```
jeanna

---

### Post by jeannacav on 2016-02-08
No wait!

```
ginala@ginala-Aspire-5517:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-98 linux-headers-3.2.0-98-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-98 linux-headers-3.2.0-98-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

maybe that will tell you something helpful??

jeanna

---

### Post by matt_symes on 2016-02-08
Hi

Please post the output of

```
dpkg -l | grep linux-headers
```

If you have many old header files, they'll use up plenty of inodes.

We can then remove your old kernel images and header files using dpkg.

Kind regard

---

### Post by jeannacav on 2016-02-08
Hi

```
ginala@ginala-Aspire-5517:~$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-80                     3.2.0-80.116                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic             3.2.0-80.116                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-82                     3.2.0-82.119                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-82-generic             3.2.0-82.119                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-83                     3.2.0-83.120                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic             3.2.0-83.120                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-84                     3.2.0-84.121                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-84-generic             3.2.0-84.121                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-85                     3.2.0-85.122                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-85-generic             3.2.0-85.122                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-86                     3.2.0-86.124                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-86-generic             3.2.0-86.124                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-87                     3.2.0-87.125                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-87-generic             3.2.0-87.125                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-88                     3.2.0-88.126                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic             3.2.0-88.126                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-89                     3.2.0-89.127                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic             3.2.0-89.127                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-90                     3.2.0-90.128                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-90-generic             3.2.0-90.128                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-91                     3.2.0-91.129                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-91-generic             3.2.0-91.129                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-92                     3.2.0-92.131                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-92-generic             3.2.0-92.131                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-93                     3.2.0-93.133                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-93-generic             3.2.0-93.133                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-94                     3.2.0-94.134                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-94-generic             3.2.0-94.134                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-95                     3.2.0-95.135                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-95-generic             3.2.0-95.135                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-97                     3.2.0-97.137                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-97-generic             3.2.0-97.137                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
iU  linux-headers-generic                      3.2.0.98.114                            Generic Linux kernel headers
ginala@ginala-Aspire-5517:~$ 

```

jeanna

---

### Post by matt_symes on 2016-02-08
Hi

Copy and paste this command into the terminal to purge you old kernel images
```
sudo dpkg -P linux-image-3.2.0-{57,80,82,83,84,85,86,87,88,89,90,91,92,93,94}-generic
```

Copy and paste this command into the terminal to purge you old kernel headers
```
sudo dpkg -P linux-headers-3.2.0-{57,80,82,83,84,85,86,87,88,89,90,91,92,93,94}{,-generic}
```

Run this command to fix your broken package system.
```
sudo apt-get -f install
```

Finally copy and paste this command into the terminal to enable auto-removal of packages. It should help a bit i think.
```
sudo sed -i 's/^[\/]*\(.*Remove-Unused.*\) "false";/\1 "true";/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

If this fixes the problem for you then please mark this thread as SOLVED using the thread tools menu above post #1.

Post back any errors.

Kind regards

---

### Post by jeannacav on 2016-02-08
wow!

That was a lot of stuff.
The sed command didn't DO anything. I assume that is all right, but just in case it was supposed to confirm or something, it didn't.
(It just gave me a new $ line ready to get input.)

Thank you so much. It is also great to think it won't happen again in another ten months.

More smiles and chocolate to you Matt!

jeanna

---

### Post by Vladlenin5000 on 2016-02-08
That's normal for that command. Any other message would otherwise be an error and a motive for concern. As is it just edited a configuration file.

---

### Post by jeannacav on 2017-01-10
Same time next year...

Well, it did happen again.
Using last year's form, I was able to go through this procedure by myself.
I went through all the paces you set me last year changing the numbers as it seemed right, and I am through. 
The red stop warning is gone, so I assume I am good to go now. 
But since it DID run out me out of room after 12 or so new kernels etc. I see that last command did not do the trick.

Is there a new improved command to remove the unneeded kernels and headers so I don't run out of space next year?

Thanks,

jeanna

---

