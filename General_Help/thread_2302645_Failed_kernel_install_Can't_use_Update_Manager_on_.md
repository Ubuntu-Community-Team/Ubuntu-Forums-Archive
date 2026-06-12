---
title: "Failed kernel install: Can't use Update Manager on 12.04"
date: 2015-11-11
forum: General Help
---

### Post by aa5kv on 2015-11-11
I've been using Ubuntu 12.04, 64 bit, for three years.  During that time I have had umpteen kernel updates.  A year or so ago, I installed version 4.2 of VirtualBox and have used it successfully ever since.  All was well until yesterday.  I noticed the Update Manager had another kernel update, so  I clicked install and walked away from the computer.  When I returned, I noticed a message that the installation had "failed".  When I read the message, it said that the installation failed because of "dependencies".  The message went on to recommend that I disable any 3rd party repositories, since they were often the source dependency issues.  The message suggested that I run 'apt-get -f install' to see what the problem was.  I do remember reading a message that contained "VirtualBox", so I assume the source of the problem is somehow related to VirtualBox (I had the Oracle repository checked, foolishly since VB runs fine on my machine).  I had a stronger indication that VirtualBox was involved, when it failed to run.  I have resolved the VirtualBox issue (see below).


But the update manager is still broken.  Currently it displays a red balloon on the desktop menu bar and when opened, the box displays "Header files related to Linux kernel version 3.2.0 (linux-headers-3.2.0-94 (New install) Size 11.7 MB) checked and ready to install. It also says that "the update has already been downloaded but not installed".  The update manager GUI darkens and lightens several times once opened.  Clicking "install updates" does nothing. Instead I get the following message:

'The following packages have unmet dependencies:

linux-headers-3.2.0-94-generic: Depends: linux-headers-3.2.0-94 but it is not installed'


Attempting to manually install the header file gives the following output:
```

jjs@Desktop:/$ sudo apt-get install linux-headers-3.2.0-94
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-77 linux-headers-3.2.0-77-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.2.0-94
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/11.7 MB of archives.
After this operation, 56.4 MB of additional disk space will be used.
(Reading database ... 1500118 files and directories currently installed.)
Unpacking linux-headers-3.2.0-94 (from .../linux-headers-3.2.0-94_3.2.0-94.134_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-94_3.2.0-94.134_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-94/arch/arm/mach-bcmring/include/mach/memory_settings.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-94/arch/arm/mach-bcmring/include/mach/memory_settings.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-94_3.2.0-94.134_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


When I ask for a dpkg --listing, I get this for the kernels/header files:

```


iU  linux-headers-3.2.0-94-gene 3.2.0-94.134                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
iU  linux-headers-generic       3.2.0.94.108                Generic Linux kernel headers


```

Here's what I've done so far:

1. I am now using a previous kernel available in GRUB, figuring that the one partially updated is probably broken.

2. I turned off the VirtualBox repository.
3.  I did get VirtualBox to run by doing the following:

sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

I tried the following:

4. to install the headers manually (see above).
5. ran 'sudo apt-get install -f'.
6. 'apt-get autoremove'
7. sudo apt-get update &#8211;fix-missing
8. dpkg &#8211;configure -a


I tried to purge one unused kernel and got the following:
```

jjs@Desktop:~$ sudo apt-get purge linux-image-3.2.0-79-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-94-generic : Depends: linux-headers-3.2.0-94 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Can I simply roll back the update?

Thanks for your help, jjs

---

### Post by ian-weisser on 2015-11-14
You cannot roll back updates. Well, you can...but it's not supported...and the update isn't your real problem anyway.

Look at the very end of the error line.
> **aa5kv said:**
> 
```

jjs@Desktop:/$ sudo apt-get install linux-headers-3.2.0-94
[...]
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-94_3.2.0-94.134_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-94/arch/arm/mach-bcmring/include/mach/memory_settings.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-94/arch/arm/mach-bcmring/include/mach/memory_settings.h'): [COLOR=#ff0000]**No space left on device**[/COLOR]
[...]

```


Use 'df' and 'df -i' to confirm the problem. Post the output of both here.

---

### Post by aa5kv on 2015-11-15
First, thanks for your reply. 

I did see that "no space left on device" and I "assumed" is was referring to my /Boot partition.  That's very possible since I often forget to remove old kernels.  I was able to remove two old kernels after I wrote my post, but my update still did not work.  Then, yesterday I started Software Center and it remained blank for a while and said that it had to refresh some files.  Immediately after Software Center completed its task, my updates installed and everything appears normal at this time.

```

jjs@Desktop:~/Downloads$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda7       1525920 1525019      901  100% /
udev             979574     594   978980    1% /dev
tmpfs            990014     520   989494    1% /run
none             990014       4   990010    1% /run/lock
none             990014       9   990005    1% /run/shm
/dev/sda5        121920     287   121633    1% /boot
/dev/sda8      15261696   54024 15207672    1% /home


```

```

jjs@Desktop:~/Downloads$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        23G   12G   10G  55% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           774M  944K  773M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  472K  3.8G   1% /run/shm
/dev/sda5       461M  279M  159M  64% /boot
/dev/sda8       230G   72G  146G  34% /home


```

Thanks, jjs

---

### Post by ian-weisser on 2015-11-16
The weather is about to turn stormy for you again, very soon:

> **aa5kv said:**
> jjs@Desktop:~/Downloads$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda7       1525920 1525019      901  [COLOR=#ff0000]**100%**[/COLOR] /

It's not your /boot, it's your root (/)
It's not space, it's inodes.

Perhaps you still have a few extra kernel packages lurking about?

---

### Post by aa5kv on 2015-11-16
> **ian-weisser said:**
> The weather is about to turn stormy for you again, very soon:



It's not your /boot, it's your root (/)
It's not space, it's inodes.

Perhaps you still have a few extra kernel packages lurking about?

Wow, I missed that!!  OK, I'll delete more kernels.  To delete kernels I've been using 'apt-get purge linux-image_xxxxx-generic'.  Is there a better way or more complete way?  I understand that as long as I don't delete my current kernel this is OK.  

I do have Synaptic installed.  I guess I could do it from there.

What might I do besides deleting kernels to avoid this problem in the future?  

Thanks for pointing this out!!  jjs

---

### Post by ian-weisser on 2015-11-16
Generally, you should be able to simply 'sudo apt-get autoremove' old kernels. Run it whenever your inode availability starts to get low, or on a schedule (like every few months)...whatever makes you comfortable.

A script that runs during each kernel install automatically marks older kernels eligible for autoremoval. As long as you haven't defeated the script, nor undermined it's work, autoremove should be all you need.

Removing older kernels using apt (as you have been doing) or Synaptic are also perfectly acceptable and supported ways to clean up old kernels.

---

### Post by aa5kv on 2015-11-16
Thanks for the info.

Here are my new parameters via df -i:


```


Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda7       1525920 1487357    38563   98% /
udev             979574     588   978986    1% /dev
tmpfs            990014     504   989510    1% /run
none             990014       4   990010    1% /run/lock
none             990014       6   990008    1% /run/shm
/dev/sda5        121920     242   121678    1% /boot
/dev/sda8      15261696   53125 15208571    1% /home


```

I have several additional kernels to delete.  I also notice that I have many linux-header files....named both linux-header-generic AND linux-header, associated with all of the kernels I have deleted.  I never 'purged' these, just kernels.  I assume I can also 'sudo apt-get purge linux-header-xxxx-generic them too, is that correct?  

I do have a separate /Boot partition on this machine.  I also have a Win7 install on this machine too, which I never use.  Is there any reason you can think of that there's such a disparity between my file space and inode number on the /root?  Notice that my other partitions have more than adequate inodes.  It's only the /root that has so few.  How strange.

I'm not adverse to installing a newer version of Ubuntu, but I would just as soon continuing using 12.04.  I'm a 'high mileage guy' and don't like to change things unless they're broke.  

Thanks again for all your help.  I see have a lot of reading to do.  Take care, jjs

---

### Post by sandyd on 2015-11-16
> **aa5kv said:**
> Thanks for the info.

Here are my new parameters via df -i:


```


Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda7       1525920 1487357    38563   98% /
udev             979574     588   978986    1% /dev
tmpfs            990014     504   989510    1% /run
none             990014       4   990010    1% /run/lock
none             990014       6   990008    1% /run/shm
/dev/sda5        121920     242   121678    1% /boot
/dev/sda8      15261696   53125 15208571    1% /home


```

I have several additional kernels to delete.  I also notice that I have many linux-header files....named both linux-header-generic AND linux-header, associated with all of the kernels I have deleted.  I never 'purged' these, just kernels.  I assume I can also 'sudo apt-get purge linux-header-xxxx-generic them too, is that correct?  

I do have a separate /Boot partition on this machine.  I also have a Win7 install on this machine too, which I never use.  Is there any reason you can think of that there's such a disparity between my file space and inode number on the /root?  Notice that my other partitions have more than adequate inodes.  It's only the /root that has so few.  How strange.

I'm not adverse to installing a newer version of Ubuntu, but I would just as soon continuing using 12.04.  I'm a 'high mileage guy' and don't like to change things unless they're broke.  

Thanks again for all your help.  I see have a lot of reading to do.  Take care, jjs
You probably have a large number of small files.

Run the following
```

sudo find / -xdev -printf '%h\n' | sort | uniq -c | sort -k 1 -n

```
The folder with the largest amount of files will be at the very bottom.

---

### Post by aa5kv on 2015-11-17
Thanks for the info.

Yes, indeed.  Lots of small files.  Here's a sample of my output:

```

 1151 /usr/src/linux-headers-3.2.0-23-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-26-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-27-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-29-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-30-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-31-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-32-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-33-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-34-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-35-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-36-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-37-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-38-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-39-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-40-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-41-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-43-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-44-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-45-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-48-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-49-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-51-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-52-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-53-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-54-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-55-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-56-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-57-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-58-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-59-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-60-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-61-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-63-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-64-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-65-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-67-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-68-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-69-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-70-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-72-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-74-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-75-generic/include/linux
   1151 /usr/src/linux-headers-3.2.0-76/include/linux
   1151 /usr/src/linux-headers-3.2.0-77/include/linux
   1151 /usr/src/linux-headers-3.2.0-79/include/linux
   1151 /usr/src/linux-headers-3.2.0-80/include/linux
   1151 /usr/src/linux-headers-3.2.0-82/include/linux
   1151 /usr/src/linux-headers-3.2.0-83/include/linux
   1151 /usr/src/linux-headers-3.2.0-84/include/linux
   1151 /usr/src/linux-headers-3.2.0-85/include/linux
   1151 /usr/src/linux-headers-3.2.0-86/include/linux
   1151 /usr/src/linux-headers-3.2.0-87/include/linux
   1151 /usr/src/linux-headers-3.2.0-88/include/linux
   1151 /usr/src/linux-headers-3.2.0-89/include/linux
   1151 /usr/src/linux-headers-3.2.0-90/include/linux
   1151 /usr/src/linux-headers-3.2.0-91/include/linux
   1151 /usr/src/linux-headers-3.2.0-92/include/linux
   1151 /usr/src/linux-headers-3.2.0-93/include/linux
   1151 /usr/src/linux-headers-3.2.0-94/include/linux
   1152 /usr/src/linux-headers-3.2.0-76-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-77-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-79-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-80-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-82-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-83-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-84-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-85-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-86-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-87-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-88-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-89-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-90-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-91-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-92-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-93-generic/include/linux
   1152 /usr/src/linux-headers-3.2.0-94-generic/include/linux
   1188 /usr/src/linux-headers-3.2.0-23-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-26-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-27-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-29-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-30-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-31-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-32-generic/include/config
   1188 /usr/src/linux-headers-3.2.0-33-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-34-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-35-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-36-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-37-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-38-generic/include/config
   1189 /usr/src/linux-headers-3.2.0-39-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-40-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-41-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-43-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-44-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-45-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-48-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-49-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-51-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-52-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-53-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-54-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-55-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-56-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-57-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-58-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-59-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-60-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-61-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-63-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-64-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-65-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-67-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-68-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-69-generic/include/config
   1190 /usr/src/linux-headers-3.2.0-70-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-72-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-74-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-75-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-76-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-77-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-79-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-80-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-82-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-83-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-84-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-85-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-86-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-87-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-88-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-89-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-90-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-91-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-92-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-93-generic/include/config
   1192 /usr/src/linux-headers-3.2.0-94-generic/include/config
   1604 /usr/bin
   1680 /usr/share/man/man1
   1986 /usr/share/doc
   2209 /usr/share/app-install/icons
   2588 /usr/share/app-install/desktop
   3880 /usr/share/foomatic/db/source/printer
   5021 /usr/share/man/man3
   8619 /var/lib/dpkg/info


```

I guess this means that 'purging' my old kernels from the /Boot does not necessarily remove config files from /usr (i.e. /root).  Strange.

Thanks again, jjd

---

### Post by J_Me on 2015-11-17
These are the steps I take if I need to manually remove kernels. From my notes ```
dpkg --list | grep linux-image
```NOTE rc  linux-image-3.13.0-24-generic 'rc' means its removed  ii  linux-image-3.13.0-24-generic 'ii' means its still on hard drive. You also need to remove the packages that are tide to the linux-image version, find them with```
dpkg -l | grep ^ii | grep x.x.x-xx | awk -F' ' '{ print $2 }'
```Now just remove the linux-image and linux-headers with apt-get  NOTE Remove the linux-image-x.x.x-xx first before removing  linux-headers-x.x.x-xx  Many times you get a few linux-images with the same version number but with extra bits like -extras and -generic on the end just remove the most basic one first and the rest will be autoselected for deletion but check to make sure. Finally Update grub ```
sudo update-grub
```

---

### Post by J_Me on 2015-11-17
Things bunched up on my post also I copy/pasted from my notes so just to clarify x.x.x-xx means the linux image number.

---

### Post by aa5kv on 2015-11-17
Thanks everyone for your help.

This is the output from df -i:

```


Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda7       1525920 297348  1228572   20% /
udev             979574    592   978982    1% /dev
tmpfs            990014    517   989497    1% /run
none             990014      4   990010    1% /run/lock
none             990014      7   990007    1% /run/shm
/dev/sda5        121920    242   121678    1% /boot
/dev/sda8      15261696  54058 15207638    1% /home

```

Thanks to everyone.  I appreciate your help.  I learned a bunch from this experience.  Thanks again, jjs

---

