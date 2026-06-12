---
title: "Problems with GUI, or lack thereof, after update."
date: 2017-01-22
forum: General Help
---

### Post by Excellis on 2017-01-22
Recently I updated/upgraded in Ubuntu 14.04.5 LTS on my Dell inspiron 15 using:
```

sudo apt-get upgrade
sudo apt-get update

```

I also installed the latest version of SSH using:

```

sudo apt-add-repository 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main universe multiverse'
sudo apt-get update
sudo apt-get install openssh-server=1:7.3p1-1

```

Everything was working fine and I am now using the latest version of SSH.
However, after I restarted my computer, instead of going through the normal boot process and taking me to the Ubuntu GUI/Desktop Enviroment it takes me to Ubuntu 14.04.5 LTS username-computername tty1.

I can then login by typing my normal username and password. I get an error 
```

apt-config: relocation error: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: symbol _ZNKSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEE7compareERKS4_, version GLIBCXX_3, 4.21 not defined in file libstdc++.so.6 with link time reference

```
Repeated 9 times.

After that I am in a normal terminal.

I tried 
```

sudo startx

```
To get to GUI.
It printed the standard stuff and then I got the error:
```

Unable to update the static FcBlanks: 0x0600
Unable to update the static FcBlanks: 0x0601
Unable to update the static FcBlanks: 0x0602
Unable to update the static FcBlanks: 0x0603
Unable to update the static FcBlanks: 0x06dd
Unable to update the static FcBlanks: 0x070f
Unable to update the static FcBlanks: 0x2028
Unable to update the static FcBlanks: 0x2029
Unable to update the static FcBlanks: 0xfff9
Unable to update the static FcBlanks: 0xfffa
Unable to update the static FcBlanks: 0xfffb
```

I used
```

sudo dpkg --configure -a

```

In an attempt to fix it and now when I use
```

sudo startx

```

I get the standard output, then a black screen, and then it returns to tty1 and prints the error:
```

[  105.238222]  [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 0 (-2).
[  105.241089]  [drm:amdgpu_resume [amdgpu]] *ERROR* resume 4 failed -2
[  105.243938]  [drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-2).
[  105.246992]  amdgpu 0000:03:00.0: couldn't schedule ib
[  105.251776]  [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  105.257251]  [drm:amdgpu_sched_main [amdgpu]] *ERROR* Failed to run job!
(II) [KMS] Kernel modesetting enabled.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:                   Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                                Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
xinit:   connection to X server lost

waiting for X server to shut down (II) Server terminated successfully (0). Closing log file.
 

```

And then I am back to standard terminal.

It might be a problem with the graphics card so helping me troubleshoot that would be appreciated.

I am plugged into an ethernet connection however it does not seem to be able to reach the network.

Thank you in advance,
Ex.

Edit: I have gotten back my internet connection by editing /etc/network/interfaces
Now need to attempt to fix apt-get, that is the significance of this error:

```

apt-config: relocation error: /usr/lib/x86_64-linux-gnu/libapt-pkg.so.5.0: symbol _ZNKSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEE7compareERKS4_, version GLIBCXX_3, 4.21 not defined in file libstdc++.so.6 with link time reference

```

Edit 2: I fixed apt-get by using wget and dpkg on my version of libstdc++. I also had to use --auto-deconfigure, to force it to drop back to the previous version.

---

### Post by TheFu on 2017-01-22
a) This is the wrong order:
```
sudo apt-get upgrade
sudo apt-get update
```
should be 
```
sudo apt-get update
sudo apt-get upgrade

```order matters.

b) You can't mix repos for different OSes and expect things to work.  14.04 is NOT "yakkety".  Basically, you just shoved a Ford engine into a Toyota vehicle. Bad.  14.04 is "trusty."

I think the only solution to fix it will be to restore from the backup you did just prior. You can try fixing the repo (use trusty) and do a full-upgrade, but I wouldn't expect that to work.

Obviously, backup any more data that might have changed since the before the last attempt with the wrong repo.

[http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories](http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories) says:
>  Mixing repositories can break your system. 
and [https://help.ubuntu.com/community/Repositories/CommandLine#Suggestions_.26_Recommendations](https://help.ubuntu.com/community/Repositories/CommandLine#Suggestions_.26_Recommendations) says:
```
Repositories that are not designed to work with **your version** of Ubuntu can introduce inconsistencies in your system and might force you to re-install.
```
Be careful out there. Hopefully you have a few backups and can restore.

---

### Post by Excellis on 2017-01-23
I have managed to save all my data. I upgraded to 16.04.1, uninstalled the Yackety version of SSH and reinstalled 7.0.2, then managed to log-in.
Now i'm going to copy off all my data and then reinstall ubuntu completely.

Thanks.

---

