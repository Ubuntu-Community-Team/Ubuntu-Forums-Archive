---
title: "Changing the default kernel and making it stay changed"
date: 2013-02-20
forum: General Help
---

### Post by ArlieS on 2013-02-20
I have a 12.10 system which has been through several weeks of updates from "software upgrader". This has taken the kernel from 3.5.0-17, which works, to 3.5.0-22 and 3.5.0-23, which seem to be making my X server quite unstable. It boots 3.5.0-23 by default. 

I want to leave all 3 kernels there, and change the default. I'd normally expect to do this by editing  /boot/grub/grub.cfg.    BUT that file has a warning that one should not edit the file, as it is automatically generated.   Also, I don't want "apt-get upgrade" or the "software updater" tool undoing my changes.  I'm willing to try future kernels in case they fix my problem, but I don't want them being booted by default. 

How should I do this?

---

### Post by Doug S on 2013-02-20
As usual, there are several ways to do what you want, of which I will describe 1.
Note that I am using a 13.04 machine, but I think 12.10 uses grub 2.00 also. It might be a little different for grub 1.99.
 
First, save your current copy of /etc/default/grub:```
doug@test-smy:/etc/default$ sudo cp grub grub.original.2
doug@test-smy:/etc/default$ ls -l grub*
-rw-r--r-- 1 root root 1233 Feb 20 14:21 grub
-rw-r--r-- 1 root root 1225 Feb  3 08:18 grub.original
-rw-r--r-- 1 root root 1233 Feb 20 14:36 grub.original.2
```Now edit grub. I prefer nano:```
doug@test-smy:/etc/default$ sudo nano grub

``` find this area:```
GRUB_DEFAULT=0
```And change that line and add one new line:```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```You might want to increase the default timeout, to give yourself more time to actually notice the menu:```
GRUB_TIMEOUT=10
```
What this will do is make it so that grub will default to whatever you did last time.
Then update grub```
doug@test-smy:/etc/default$ sudo update-grub
```Now re-boot and manually select the kernel you want to run. Then re-boot again and it should be the default.
You can observe the default:```
doug@test-smy:~$ cat /boot/grub/grubenv
# GRUB Environment Block
saved_entry=gnulinux-advanced-1bfeb1e4-5228-4e17-9ee0-87ab695fbe79>gnulinux-3.8.0-5-generic-advanced-1bfeb1e4-5228-4e17-9ee0-87ab695fbe79
###############################...
```And here is is after I have gone back to the latest kernel as the default (but still using the whatever I did last time method):```
doug@test-smy:~$ cat /boot/grub/grubenv
# GRUB Environment Block
saved_entry=gnulinux-simple-1bfeb1e4-5228-4e17-9ee0-87ab695fbe79
################################...
```Hope this helps
 
Reference: [https://help.ubuntu.com/community/Grub2#Saved](https://help.ubuntu.com/community/Grub2#Saved)

---

### Post by ArlieS on 2013-02-21
> **Doug S said:**
> As usual, there are several ways to do what you want, of which I will describe 1.
Note that I am using a 13.04 machine, but I think 12.10 uses grub 2.00 also. It might be a little different for grub 1.99.
 
[snippage]

Hope this helps
 
Reference: [https://help.ubuntu.com/community/Grub2#Saved](https://help.ubuntu.com/community/Grub2#Saved)

This looks great, thank you.  I'll mark the thread [solved] once I've tried and verified it - or post what happened, if it's not what I wanted, which I'm not expecting.

---

### Post by ArlieS on 2013-02-24
> **ArlieS said:**
> This looks great, thank you.  I'll mark the thread [solved] once I've tried and verified it - or post what happened, if it's not what I wanted, which I'm not expecting.

Well, it's not solved.

This somehow caused the previously good kernel to misbehave.  I followed your instructions without changing anything else, and rebooted - and the graphics problem I'd seen with the recent kernels promptly started happening with the good kernel. Behaviour with the one bad kernel I tested changed - it still couldn't produce a graphical login, but now the error  was detected and reported to me. 

I rebooted several times, on both the good kernel and one of the bad ones, both letting it default to the remembered kernel and specifying my choice explicitly. No graphical login. 

Finally in frustration I did:
```

cd /etc/default
sudo mv grub grub.bad
sudo ln grub.original2 grub
sudo update-grub

```
I then rebooted, and selected the good kernel manually. I'm now looking at a graphical login.

I am completely baffled. I don't see how taking a different path to the point of loading the kernel could produce different behaviour at the point of starting graphics - unless we're looking at different boot-time parameters, resulting in failure to correctly detect graphics hardware. 

And meanwhile the GUI has decided to announce "apt-file update needed" - whereas before I rebooted it was merely telling me I needed to install a few dozen updates, including (somewhat frighteningly) yet another kernel.

---

### Post by Doug S on 2013-02-25
Sorry for your troubles with this. I am baffled also.

---

