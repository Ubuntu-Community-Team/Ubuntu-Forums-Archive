---
title: "I cannot upgrade because /boot is full"
date: 2017-05-31
forum: General Help
---

### Post by GreysonB on 2017-05-31
How can I get rid of the old kernels?    And, more important to my mind, why does Linux not do this itself?

---

### Post by deadflowr on 2017-05-31
try
```
sudo apt-get autoremove
```
first
if it doesn't remove old kernels, then we can move on to another method.

Also, what version of Ubuntu is it?

---

### Post by GreysonB on 2017-05-31
I'm on 16.04.

I got the message "N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension"  

I have seen this before and it appears to be the problem...

---

### Post by vasa1 on 2017-05-31
When you respond to a suggestion to run something, please post the entire command and the output it generates here. And use [CODE] tags to enclose your content. Thanks!

---

### Post by GreysonB on 2017-05-31
Sure, sorry about the omission.
```

thaumielx72@thaumielx72-MS-7593:~$ sudo apt-get autoremove
[sudo] password for thaumielx72: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
thaumielx72@thaumielx72-MS-7593:~$ 

```

That's the whole thing.

---

### Post by deadflowr on 2017-05-31
> **GreysonB said:**
> I'm on 16.04.

I got the message "N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension"  

I have seen this before and it appears to be the problem...

Not any problem at all.
It's only a notice that it's going to ignore the file and nothing more.
It's inconsequential to running apt.


EDIT:
adding, looks like no go for autoremove.
Now time to see how full everything is
```
ls /boot
```
and 
```
df -h
```
so we can see what boot has and how full the file system(s) are right now.


Also:
If you are currently on 16.04 why upgrade to a release that only has a few months left of support?

---

### Post by GreysonB on 2017-05-31
Understood, but my disk has gigs of space left and will not update anything...   thanks for the input.

```
thaumielx72@thaumielx72-MS-7593:~$ ls /boot
abi-3.13.0-108-generic         lost+found
abi-4.4.0-72-generic           memtest86+.bin
abi-4.4.0-77-generic           memtest86+.elf
config-3.13.0-108-generic      memtest86+_multiboot.bin
config-4.4.0-72-generic        System.map-3.13.0-108-generic
config-4.4.0-77-generic        System.map-4.4.0-72-generic
grub                           System.map-4.4.0-77-generic
initrd.img-3.13.0-108-generic  vmlinuz-3.13.0-108-generic
initrd.img-4.4.0-72-generic    vmlinuz-4.4.0-72-generic
initrd.img-4.4.0-77-generic    vmlinuz-4.4.0-77-generic
```
```
thaumielx72@thaumielx72-MS-7593:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         5.9G     0  5.9G   0% /dev
tmpfs                        1.2G  9.7M  1.2G   1% /run
/dev/mapper/ubuntu--vg-root  905G  596G  264G  70% /
tmpfs                        5.9G  405M  5.5G   7% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        5.9G     0  5.9G   0% /sys/fs/cgroup
/dev/sda1                    236M  153M   71M  69% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        1.2G   72K  1.2G   1% /run/user/1000
/home/thaumielx72/.Private   905G  596G  264G  70% /home/thaumielx72
thaumielx72@thaumielx72-MS-7593:~$
```

---

### Post by deadflowr on 2017-05-31
Only 3 is not bad or hard to try and remove with just apt-get
try removing the oldest kernel -72 with
```
sudo apt-get purge linux-image-4.4.0-72-generic linux-headers-4.4.0-72-generic
```
if that ends successful try removing the -77 kernel following the same commands but by replacing the -72 to -77.
If that makes sense.

STOP:
Forgot to add this little caution
first run 
```
uname -a
```
to see what kernel is currently in use.
(I would guess the -108 kernel, but you never know.)
If it's anything but the -108 hold off on running the apt-get purge command and try booting (rebooting) into the -108 kernel.
Best to be running the latest kernel,imo.
(and we do not want to remove or try to remove the running kernel.)

---

### Post by GreysonB on 2017-05-31
OK, deadflower they both ran successfully.  I'm gonna try and upgrade then reboot.  Wish me luck...

---

### Post by GreysonB on 2017-05-31
Deadflowr I sure wish I had seen that STOP first.  

thaumielx72@thaumielx72-MS-7593:~$ uname -a
Linux thaumielx72-MS-7593 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
thaumielx72@thaumielx72-MS-7593:~$ 


I changed the 72 to a 77 - do I have a chance of rebooting?

---

### Post by deadflowr on 2017-05-31
Do not reboot yet.
My mistake, somehow I saw what I wanted and did not realize the -108 kernel was not the 4.4 kernel and now see it as the 3.13 kernel.
If you did remove the 4.4.0-77 kernel, then reverse the command I posted and try installing those packages again
```
sudo apt-get install linux-image-4.4.0-77-generic linux-headers-4.4.0-77-generic
```

---

### Post by GreysonB on 2017-05-31
Goodness bless you sir.  It looks like it ran to completion.  Again, wish me luck...

---

### Post by GreysonB on 2017-05-31
OK, it finally ran the updates.  It says it's upgraded me to 78.  Thanks to all, especially deadflowr.   :guitar:

---

### Post by ajgreeny on 2017-05-31
It is also possible that you are beginning to run out of inode space, so let's see the output of command ```
df -i
dpkg -l | grep linux-headers*
```
As you had unwanted kernels you may also have had many unneeded **linux-headers** remaining and those can eat up inodes quickly with the same symptoms you saw.

---

### Post by deadflowr on 2017-05-31
I think now the thing that needs to be dealt with is ridding the system of that pesky 3.13 kernel.
I'm guessing this was an upgrade from 14.04, and that the 3.13 is the kernel from that system.
Currently it seems to be a phantom eating up valuable disk space and autoremove is not going to work on it like it should.
(In normal circumstances when you ran autoremove it would have seen 3 kernels and removed the oldest and kept the last two, but for whatever reason it did not or could not see the 3.13 properly)

I think if you ran a variant of ajgreeny's command we can see if the 3.13 kernel is seen as installed on the system and can then try a more manual approach to removing it.
try
```
dpkg -l | grep linux | awk '{print $1,$2}'
```
if the 3.13.0.108 kernel is listed, perhaps try running the apt-get purge command for it.

once you clear that out, the autoremove command should clear out any old kernels except for the last two, which should keep the system from botching updates being installed.


Sidenote:
getting back to the Notice that keeps appearing, you can delete the listed file if you do not need it, and by chances you do not need it if you do not know why it's there.
(To that, it's there because it's an old config file and the system got an updated config file but the system did not know what to do with the old one so it kept it and renamed it, but that's really just the short answer)
it's perfectly fine to delete the file
```
sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-old
```
and also perfectly fine to keep on ignoring it.

Hope it all helps

---

