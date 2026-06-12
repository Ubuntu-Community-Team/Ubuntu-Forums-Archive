---
title: "problem updating the kernel"
date: 2006-11-04
forum: General Help
---

### Post by yotama9 on 2006-11-04
hello to all

I have a fresh install of ubuntu dapper, from the last afternoon. I've downloaded the cd image about three weeks ago and installed the system today.

the installation went fine and all but upon the first update the system I couldn't have update the kernel:
```
Setting up linux-restricted-modules-2.6.15-27-386 (2.6.15.12-1) ...
/sbin/lrm-manager: line 85:  6437 Bus error               depmod -a -q -F /boot/System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-27-386 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-386:
 linux-restricted-modules-386 depends on linux-restricted-modules-2.6.15-27-386; however:
  Package linux-restricted-modules-2.6.15-27-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.15-26-386 (2.6.15-26.47) ...
There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 7
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.15-26-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [No]  yes

```

I've tried running spkg --configure but it faild to perform the fixing:

```
shuki@shuki-laptop:~/Desktop/bkchem-0.11.6/bkchem$ sudo dpkg --configure linux-restricted-modules-2.6.15-27-386
Password:
Setting up linux-restricted-modules-2.6.15-27-386 (2.6.15.12-1) ...
/sbin/lrm-manager: line 85:  6682 Bus error               depmod -a -q -F /boot/System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-27-386 (--configure):
 subprocess post-installation script returned error exit status 135
Errors were encountered while processing:
 linux-restricted-modules-2.6.15-27-386
shuki@shuki-laptop:~/Desktop/bkchem-0.11.6/bkchem$


```

I'm going crazy here. please help me... every installation I do comes along with 10 minutes of the machine acting realy slow.

---

### Post by catlett on 2006-11-04
Hello,
First, you do not have to upgrade your kernel everytime it is offered as an update. The kernel is continually being worked on to add more/better hardware support etc. So if your system is running fine, you do not have to upgrade.
Second, if your system is responding well enough, go into Synaptic Package Manager (System>Administration>Synaptic Package manager) and install the restricted module from there.
Also you can add updates through Synaptic Package Mnager and skip the update manager. This way you only add what you want. 
I would try synaptic first. Search for restricted modules and try to install it. If you want the updated kernel, I would use Synaptic to install it instead of the update manager.

---

### Post by yotama9 on 2006-11-05
that's what I did on the first place. I clicked update on synaptic. and it went crazy

the system is realy messed up now and I don't know how.

the boot time takes like 5 minutes to load (instead of less then a minute) and python won't work well.

I think I'll reinstall the system and hope for good.

---

### Post by catlett on 2006-11-05
No, not select 'update' on synaptic. I mean if you want a newer kernel, select it manually and choose mark for installation.
If you are having update issues, stay away from automatic updating. You can individually select packages in synaptic. For instance if you want to get kernel 2.6 and you have 2.4 Don't select upgrade in synaptic nor say yes to the update manager. Go into to synaptiuc package manager and browse to kernel 2.6 Highlight it and select 'mark for installation'. Do it manually. Select a package and install it. Don't do anything automatically.
Hopefully that will help with the upgrade instability.

P.S. going from 2.4 to 2.6 is just an example. the upgrades now will be variations of 2.6 but I don't know the exact numbers and I just wanted an example of 2 different versions.

---

### Post by yotama9 on 2006-11-05
the problem at first is:

how come a fresh new install of ubuntu has that kind of problem

the second is that I can't find the problem and I want to konw if the problem is with my installation (apperntly not couse I have just installed again with the same problem). another problem is that now, whenever I install something with synaptic, the machine tries to update it's kernel wich is anoying couse it can't.

and ofcourse I want my machine to be up to date so it bother me that I can't use a new (and hopefully better) kernel.

---

### Post by Ramses de Norre on 2006-11-05
In fact I wouldn't advice against updates, I think it's always the best to have the most current packages from the repo's.

Secondly: it isn't your kernel being upgraded but the restricted-modules (or at least I didn't get a kernel upgrade..).

So I'd try ```
sudo aptitude purge linux-restricted-modules-2.6.17-10-386
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install linux-restricted-modules-386
```

---

### Post by yotama9 on 2006-11-06
no good:

```
shuki@shuki-laptop:~$ sudo aptitude purge linux-restricted-modules-2.6.17-10-386Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.17-10-386"
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.15-26-386 (2.6.15-26.47) ...
There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 7
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.15-26-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [No]

```

any other IDEA?

---

### Post by Ramses de Norre on 2006-11-06
Ow it seems you do have a kernel upgrade, only 386 kernel is affected then.
I'm not familiar with depmod so I don't really know how to fix it, I can't find anything related on launchpad neither..

---

