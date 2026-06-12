---
title: "Cinnamon 64bit, update manager sez error broken count &gt; 0"
date: 2015-04-20
forum: General Help
---

### Post by jeannacav on 2015-04-20
I ran the update meneger last week and got notified there is a problem.

I think I did what it suggested and I was told there is not enough room to do it (or something).
I checked today and there is 7.8G left in the os partition and 78 G left in the data partition so there IS plenty of room. 
I am afraid this might be a lot of work to fix.

Thing is... I am a lousy typer and dyslexic as well so typing terminal commands is troublesome. ( will try anyway...)

I made a screenshot of the return from the terminal when I did as directed so you can see.

My question is,

Is there an easy and obvious fix that anyone can see?

Will it be likely to fix this easily if I reinstall the whole thing (with updates , of course)?
I am inclined to fresh install since I have that os partition.


thanks,

jeanna

[ATTACH=CONFIG]261439[/ATTACH]

---

### Post by matt_symes on 2015-04-20
Hi

This may be an inode problem as that will also cause that error message.

As you don't like typing, copy and paste these commands into your terminal from this post.

Highlight the command in this post -> right click-> copy. In the terminal -> right click->paste to paste the command and then hit enter. Then you only need to enter your password. You can also copy and paste from the terminal into your post by highlighting the text in the terminal-> right click-> copy .......

First of all, let's try to clean up your system. This command will remove the old packages that are no longer required.

```
sudo apt-get autoremove
```

After that, copy and paste this into the terminal and copy and paste the results back into your next post.

```
df -h && df -i
```

Kind regards

---

### Post by jeannacav on 2015-04-20
> **matt_symes said:**
> Hi

This may be an inode problem as that will also cause that error message.

First of all, let's try to clean up your system. This command will remove the old packages that are no longer required.

```
sudo apt-get autoremove
```


OK thanks
the remove part first...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-3.2.0-80-generic : Depends: linux-headers-3.2.0-80 but it is not installed
E: Unmet dependencies. Try using -f.

> 
After that, copy and paste this into the terminal and copy and paste the results back into your next post.

```
df -h && df -i
```

Kind regards

And here is the second part.


:~$ df -h && df -i
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   12G  6.4G  64% /
udev            866M  4.0K  866M   1% /dev
tmpfs           175M  796K  175M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            874M  176K  874M   1% /run/shm
/dev/sda2       125G   60G   59G  51% /home
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      1224000 1218737    5263  100% /
udev            221533     470  221063    1% /dev
tmpfs           223732     389  223343    1% /run
none            223732       3  223729    1% /run/lock
none            223732      12  223720    1% /run/shm
/dev/sda2      8306688   22825 8283863    1% /home

---

### Post by jeannacav on 2015-04-20
Hi Matt,
My online time is running out for today.
I will be back on friday to try the things you might suggest.
I very much appreciate your help.

jeanna

---

### Post by matt_symes on 2015-04-20
Hi

> /dev/sda1      1224000 1218737    5263  **100%** /

The problem is that you don't have enough inodes to install the headers.

As we cannot use apt, we'll have to use dpkg.

Open a terminal and copy and paste this into it. This will remove some header files and free up a number of inodes.

```
sudo dpkg -P linux-headers-3.2.0-5{1,7}{,-generic}
```

Then enter the command below to fix the unhandled dependencies problem.

```
sudo apt-get install -f
```

After that enter this to remove unwanted packages.

```
sudo apt-get autoremove
```

Finally post the output of this command to see what kernel headers and images you have installed as i am wondering where your inodes have been used up.

```
dpkg -l | egrep "linux-headers|linux-image|linux-signed"
```

Kind regards

---

### Post by jeannacav on 2015-04-24
> **matt_symes said:**
> Hi



The problem is that you don't have enough inodes to install the headers.

As we cannot use apt, we'll have to use dpkg.

Open a terminal and copy and paste this into it. This will remove some header files and free up a number of inodes.

```
sudo dpkg -P linux-headers-3.2.0-5{1,7}{,-generic}
```

Then enter the command below to fix the unhandled dependencies problem.

```
sudo apt-get install -f
```

After that enter this to remove unwanted packages.

```
sudo apt-get autoremove
```

Finally post the output of this command to see what kernel headers and images you have installed as i am wondering where your inodes have been used up.

```
dpkg -l | egrep "linux-headers|linux-image|linux-signed"
```

Kind regards

OK here it is:
```

xxxxxxxxxxxxxx-Aspire-5517:~$ dpkg -l | egrep "linux-headers|linux-image|linux-signed"
ii  linux-headers-3.2.0-61                 3.2.0-61.93                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63                 3.2.0-63.95                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic         3.2.0-63.95                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-64                 3.2.0-64.97                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic         3.2.0-64.97                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-65                 3.2.0-65.99                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-65-generic         3.2.0-65.99                             Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-67                 3.2.0-67.101                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-68                 3.2.0-68.102                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-68-generic         3.2.0-68.102                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-69                 3.2.0-69.103                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-69-generic         3.2.0-69.103                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-70                 3.2.0-70.105                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-72                 3.2.0-72.107                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-72-generic         3.2.0-72.107                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-74                 3.2.0-74.109                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-74-generic         3.2.0-74.109                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-75                 3.2.0-75.110                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-75-generic         3.2.0-75.110                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-76                 3.2.0-76.111                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-76-generic         3.2.0-76.111                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-77                 3.2.0-77.114                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-77-generic         3.2.0-77.114                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-79                 3.2.0-79.115                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-80                 3.2.0-80.116                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.80.94                             Generic Linux kernel headers
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-65-generic           3.2.0-65.99                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic           3.2.0-67.101                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-68-generic           3.2.0-68.102                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-69-generic           3.2.0-69.103                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-70-generic           3.2.0-70.105                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-72-generic           3.2.0-72.107                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-74-generic           3.2.0-74.109                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-75-generic           3.2.0-75.110                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-76-generic           3.2.0-76.111                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-77-generic           3.2.0-77.114                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.80.94                             Generic Linux kernel image
xxxxx-Aspire-5517:~$
```

Thank you so much.

update manager gave me a notice in the middle of all this.
I think I will reboot before doing the update.

If there is anything really interesting about what happened please post your comments about it here. I am interested. (even though I can't type!)

Flowers and chocolate to you, Matt.
Thanks sooo much.

jeanna

---

### Post by matt_symes on 2015-04-24
Hi

> **jeannacav said:**
> update manager gave me a notice in the middle of all this.
I think I will reboot before doing the update. If there is anything really interesting about what happened please post  your comments about it here. I am interested. (even though I can't  type!)

If the commands in my last post produced any errors then please post the errors back here and don't run the commands below or at least tell me that they errorred.

However if all the previous commands were successfully then....

...first we'll remove the extra kernels to leave your oldest one (.59) and the newest one (.80)

Open a terminal and copy and paste this in to it

```
sudo apt-get purge linux-image-3.2.0-[6,7].-generic
```

If that completes successfully then to remove the header, copy and paste this into a terminal. This will remove all the headers bar the newest ones.

```
sudo apt-get purge linux-headers-3.2.0-[6-7].*
```

Both of the above command may take a while to complete so be patient. If there are any errors then post them back here.

If the above commands complete sucessfully then post the output of these commands just so we can check your system.

```
dpkg -l | egrep "linux-headers|linux-image" && df -i | grep "/$"
```

> Flowers and chocolate to you, Matt.
Thanks sooo much.

jeanna

Awww. Sweetie :p

EDIT: I added a " i missed so double check my commands.

Kind regards

---

### Post by jeannacav on 2015-04-24
```
xxxxxxxxx-Aspire-5517:~$ dpkg -l | egrep "linux-headers|linux-image" && df -i | grep "/$"
ii  linux-headers-3.2.0-80                 3.2.0-80.116                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.80.94                             Generic Linux kernel headers
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.80.94                             Generic Linux kernel image
/dev/sda1      1224000 821584  402416   68% /
xxxxxxxxxxxxx-Aspire-5517:~$ 

```

I guess I made a lot of changes at one time.
I held onto lynx which was 32 bit for  extra long and when I changed to cinnamon, I did it as an upgrade and switched to 64 bit at the same time.
I wonder if because I did the upgrade it kept all those old 32 bit kernels and headers?
(I wonder if the system settings will work better now?)

Thanks again.
I will check in again before I leave to see if you have more suggestions.

jeanna

---

### Post by jeannacav on 2015-04-24
OK It is time to go.
I will check in on monday and mark it solved if it is so.

jeanna

---

### Post by matt_symes on 2015-04-25
Hi

> **jeannacav said:**
> ```
xxxxxxxxx-Aspire-5517:~$ dpkg -l | egrep "linux-headers|linux-image" && df -i | grep "/$"
ii  linux-headers-3.2.0-80                 3.2.0-80.116                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                            Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                  3.2.0.80.94                             Generic Linux kernel headers
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                            Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.2.0.80.94                             Generic Linux kernel image
/dev/sda1      1224000 821584  402416   68% /
xxxxxxxxxxxxx-Aspire-5517:~$ 

```

That looks much better.

> I guess I made a lot of changes at one time.
I held onto lynx which was 32 bit for  extra long and when I changed to cinnamon, I did it as an upgrade and switched to 64 bit at the same time.
I wonder if because I did the upgrade it kept all those old 32 bit kernels and headers?
(I wonder if the system settings will work better now?)

Thanks again.
I will check in again before I leave to see if you have more suggestions.

jeanna

You may want to clean out the old package cache as that may free up more space but not a large number of inodes so open a terminal....

```
sudo apt-get clean
```

From there you are pretty much good to go.

Kind regards

---

