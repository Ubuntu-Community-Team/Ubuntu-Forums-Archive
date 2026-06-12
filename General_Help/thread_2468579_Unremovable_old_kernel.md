---
title: "Unremovable old kernel"
date: 2021-11-03
forum: General Help
---

### Post by rsteinmetz70112 on 2021-11-03
This Afternoon I updated one of my computers running 20.04.3. It had a little problem during the update and the Linux firmware didn't update. I ran the update again and it installed the Linux firmware update. 

That left me with 3 kernels installed 5.4.0-84-generic   5.4.0-88-generic   5.4.0-89-generic. 

Normally in this situation [[FONT=Courier New]**# apt autoremove**[/FONT]] would offer to remove the oldest kernel, but it's not doing that. It seems something must be out of sync, but what and how can I get it back in sync?

Running [[FONT=Courier New]**#apt update**[/FONT]] or [[FONT=Courier New]**#apt upgrade**[/FONT]] reports that all packages are up to date.

---

### Post by deadflowr on 2021-11-03
See which is running
```
uname -r
```
My guess would be it's 5.4.0.84

Makes sense as autoremove is designed to never remove the latest two kernels installed, which would be the -88 and -89 kernels.
And it will never ever remove the running kernels.

---

### Post by ActionParsnip on 2021-11-04
Autoremove doesn't remove old kernels. It removes packages that are no longer needed once you remove other packages.

What is the output of
```

uname -a; dpkg -l | grep linux-image

```

---

### Post by rsteinmetz70112 on 2021-11-04
Here you go.

```
# uname -r
5.4.0-89-generic
```

```
# uname -a; dpkg -l | grep linux-image
Linux romulus 5.4.0-89-generic #100-Ubuntu SMP Fri Sep 24 14:50:10 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
rc  linux-image-2.6.17-10-generic              2.6.17.1-10.34                                  amd64        Linux kernel image for version 2.6.17 on x86/x86_64
rc  linux-image-2.6.20-16-generic              2.6.20-16.35                                    amd64        Linux kernel image for version 2.6.20 on x86/x86_64
rc  linux-image-2.6.24-19-server               2.6.24-19.41                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-21-generic              2.6.24-21.43                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-22-generic              2.6.24-22.45                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-23-generic              2.6.24-23.52                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-24-generic              2.6.24-24.61                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-25-generic              2.6.24-25.63                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-26-generic              2.6.24-26.64                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-28-generic              2.6.24-28.71                                    amd64        Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.32-24-generic              2.6.32-24.43                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-25-generic              2.6.32-25.45                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-26-generic              2.6.32-26.48                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-27-generic              2.6.32-27.49                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-28-generic              2.6.32-28.55                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-30-generic              2.6.32-30.59                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-32-generic              2.6.32-32.62                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-33-generic              2.6.32-33.72                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-34-generic              2.6.32-34.77                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-35-generic              2.6.32-35.78                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-36-generic              2.6.32-36.79                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-38-generic              2.6.32-38.83                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-41-generic              2.6.32-41.94                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-42-generic              2.6.32-42.96                                    amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-45-generic              2.6.32-45.104                                   amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.32-46-generic              2.6.32-46.108                                   amd64        Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-3.13.0-49-generic              3.13.0-49.83                                    amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic              3.13.0-62.102                                   amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-41-generic               3.2.0-41.66                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-45-generic               3.2.0-45.70                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-48-generic               3.2.0-48.74                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-49-generic               3.2.0-49.75                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-51-generic               3.2.0-51.77                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-57-generic               3.2.0-57.87                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-58-generic               3.2.0-58.88                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-59-generic               3.2.0-59.90                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-65-generic               3.2.0-65.99                                     amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-67-generic               3.2.0-67.101                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-69-generic               3.2.0-69.103                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-75-generic               3.2.0-75.110                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-80-generic               3.2.0-80.116                                    amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-4.15.0-101-generic             4.15.0-101.102                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-106-generic             4.15.0-106.107                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-108-generic             4.15.0-108.109                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-109-generic             4.15.0-109.110                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-111-generic             4.15.0-111.112                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-112-generic             4.15.0-112.113                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-117-generic             4.15.0-117.118                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-118-generic             4.15.0-118.119                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-122-generic             4.15.0-122.124                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-123-generic             4.15.0-123.126                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-126-generic             4.15.0-126.129                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-129-generic             4.15.0-129.132                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-132-generic             4.15.0-132.136                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-135-generic             4.15.0-135.139                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-136-generic             4.15.0-136.140                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-140-generic             4.15.0-140.144                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-142-generic             4.15.0-142.146                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-143-generic             4.15.0-143.147                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-144-generic             4.15.0-144.148                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-151-generic             4.15.0-151.157                                  amd64        Signed kernel image generic
rc  linux-image-4.15.0-50-generic              4.15.0-50.54                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-55-generic              4.15.0-55.60                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-58-generic              4.15.0-58.64                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-64-generic              4.15.0-64.73                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-65-generic              4.15.0-65.74                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-66-generic              4.15.0-66.75                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-70-generic              4.15.0-70.79                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-72-generic              4.15.0-72.81                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-74-generic              4.15.0-74.84                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-76-generic              4.15.0-76.86                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-88-generic              4.15.0-88.88                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-91-generic              4.15.0-91.92                                    amd64        Signed kernel image generic
rc  linux-image-4.15.0-96-generic              4.15.0-96.97                                    amd64        Signed kernel image generic
hi  linux-image-4.4.0-103-generic              4.4.0-103.126                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic              4.4.0-104.127                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-109-generic              4.4.0-109.132                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-112-generic              4.4.0-112.135                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-121-generic              4.4.0-121.145                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-122-generic              4.4.0-122.146                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-124-generic              4.4.0-124.148                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-127-generic              4.4.0-127.153                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-128-generic              4.4.0-128.154                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-131-generic              4.4.0-131.157                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-137-generic              4.4.0-137.163                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-138-generic              4.4.0-138.164                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-142-generic              4.4.0-142.168                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-145-generic              4.4.0-145.171                                   amd64        Signed kernel image generic
rc  linux-image-4.4.0-146-generic              4.4.0-146.172                                   amd64        Signed kernel image generic
rc  linux-image-4.4.0-148-generic              4.4.0-148.174                                   amd64        Signed kernel image generic
rc  linux-image-4.4.0-64-generic               4.4.0-64.85                                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic               4.4.0-66.87                                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-77-generic               4.4.0-77.98                                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic               4.4.0-79.100                                    amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic               4.4.0-83.106                                    amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-98-generic               4.4.0-98.121                                    amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-5.4.0-80-generic               5.4.0-80.90                                     amd64        Signed kernel image generic
rc  linux-image-5.4.0-81-generic               5.4.0-81.91                                     amd64        Signed kernel image generic
ii  linux-image-5.4.0-84-generic               5.4.0-84.94                                     amd64        Signed kernel image generic
ii  linux-image-5.4.0-88-generic               5.4.0-88.99                                     amd64        Signed kernel image generic
ii  linux-image-5.4.0-89-generic               5.4.0-89.100                                    amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-49-generic        3.13.0-49.83                                    amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic        3.13.0-62.102                                   amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
hi  linux-image-extra-4.4.0-103-generic        4.4.0-103.126                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-generic        4.4.0-104.127                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic        4.4.0-109.132                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic        4.4.0-112.135                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-121-generic        4.4.0-121.145                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-122-generic        4.4.0-122.146                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-124-generic        4.4.0-124.148                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-127-generic        4.4.0-127.153                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-128-generic        4.4.0-128.154                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-131-generic        4.4.0-131.157                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-137-generic        4.4.0-137.163                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-138-generic        4.4.0-138.164                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-142-generic        4.4.0-142.168                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic         4.4.0-64.85                                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic         4.4.0-66.87                                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-generic         4.4.0-77.98                                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic         4.4.0-79.100                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic         4.4.0-83.106                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-98-generic         4.4.0-98.121                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        5.4.0.89.93                                     amd64        Generic Linux kernel image
```

---

### Post by deadflowr on 2021-11-04
Wow, you actually have 5 kernels installed.

I'd just remove the older ones manually, but first unhold the *linux-image-4.4.0-103-generic* and *linux-image-extra-4.4.0-103-generic* packages.
(The older kernels being the linux-image-4.4.0-109-generic and the linux-image-5.4.0-84-generic, along with those two held  *-4.4.0-103-generic packages)

Also,
Do you want to keep all those pesky leftover configuration files?

---

### Post by rsteinmetz70112 on 2021-11-04
I don't really need them. This system has been in place for about 15 years and been through 4 motherboards and 3 sets of hard drives. 

I've never noticed left over initram files before so I haven't really bothered checking deeper since everything worked. 

How does one safely unhold the kernels? 
How does one safely remove configuration files? 

I assume it is probably dpkg, but I stay as far away of that as I can because of the consequences of doing something wrong.

---

### Post by deadflowr on 2021-11-04
> How does one safely unhold the kernels?

```
sudo apt-mark unhold *package-name*
```
(Replace package-name with the correct package name(s))
> How does one safely remove configuration files?
There are a couple methods, and yes they use typically use dpkg. 

I use this command to purge those on occasion
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```
You can do some double checking too.
1)By adding $1 to the print field it'll show the status of the packages, so you know it's only listing the rc'd packages like so
```
dpkg -l | awk '/^rc/{print **$1**,$2}'
```

2) You can run the command as a dry-run/simulation first, which will show what will happen, but not actually do it.
Like this
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -s
```
Basically simply switch the -y option for the -s option.


FWIW, apt's purge command will always remove the leftover config files.
It's apt's remove command which leaves them behind. 
(apt's autoremove is basically a variation of remove so it too leaves old configs behind)

You can use purge as an option when running autoremove like
```
sudo apt autoremove --purge
```
Which will clear out all the files.

Hope it helps or makes sense.

---

### Post by rsteinmetz70112 on 2021-11-04
I think something might be wrong with this command:
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -s
```

It seems to want to purge a lot of packages I don't want purged.

---

### Post by Yellow Pasque on 2021-11-04
Use Synaptic if you're struggling with commands. It makes thing much easier. Just be careful not to remove anything you don't want to.

---

### Post by rsteinmetz70112 on 2021-11-04
Thanks to those who commented. 

I'm not done yet, but I think I've solved the immediate problem.

I've been carefully moving through using the command line, avoiding mass removals and removing select classes of files. So far I've been successful. 

I need to do some more work and look into the number of packages marked as "rc" many may be very old.

---

### Post by TheFu on 2021-11-05
**apt-get** can use pattern matching, btw.
```
sudo apt-get remove --purge 'linux-image-[234]*'
```
will clear up most of the those 'rc' lines in the list.  Then autoremove should deal with headers and modules ... if not, do a similar pattern with apt-get for them too.
It is hard to see what's important with all the cruft.

I think **apt** can do patterns now too - about the last year. For example:
```
sudo apt purge 'linux-image-extra-[234]*'
sudo apt purge 'linux-image-5.4.0-8[01]*'

```

In the old days, we'd use **awk** and **xargs** - nothing wrong with that, but the apt and apt-get people realised the need for better pattern matching.

---

### Post by ActionParsnip on 2021-11-05
The command deadflower gave will purge all the residual config for each package and cleanup the OS some.

---

### Post by rsteinmetz70112 on 2021-11-05
Thanks everyone.

I have worked through all of the linux-image files and they are gone. I've removed all of the extra kernels so autoremove is now working correctly. I probably need to remove some more of the old configuration files but I'll put that off for another day.

---

### Post by TheFu on 2021-11-05
> **rsteinmetz70112 said:**
> Thanks everyone.

I have worked through all of the linux-image files and they are gone. I've removed all of the extra kernels so autoremove is now working correctly. I probably need to remove some more of the old configuration files but I'll put that off for another day.

**I hope you left 2 of the linux-image installed!!!!**  If not, don't reboot.  Install the last two ASAP.
Sorry if that wasn't clear.  The goal is to have 2 install, but not have any remnants from older kernels, and dependencies pulled in automatically due to older kernels, left.

---

### Post by Yellow Pasque on 2021-11-05
> **rsteinmetz70112 said:**
> I probably need to remove some more of the old configuration files but I'll put that off for another day.

Use Synaptic. It will show you "Not installed (residual config)" packages that you can purge.

---

