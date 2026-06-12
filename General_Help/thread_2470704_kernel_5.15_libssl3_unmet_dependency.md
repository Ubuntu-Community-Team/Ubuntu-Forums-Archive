---
title: "kernel 5.15 libssl3 unmet dependency"
date: 2022-01-08
forum: General Help
---

### Post by theadmiral2 on 2022-01-08
i recently installed ubuntu 21.10 and installed the kernel 5.15. after that sudo apt upgrade gives the following output


sudo apt upgrade 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies: 
 linux-headers-5.15.13-051513-generic : Depends: libssl3 (>= 3.0.0~~alpha1) but it is not installable 
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution). 
 
and this command asks to remove the kernel header.

sudo apt --fix-broken install 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Correcting dependencies... Done 
The following packages will be REMOVED: 
  linux-headers-5.15.13-051513-generic 
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 23.8 MB disk space will be freed. 
Do you want to continue? [Y/n]  

what to do please help.

---

### Post by ramirojuy on 2022-01-09
I have the same problem. The weird thing is that the library if I have it installed, but it still appears to me as if the dependencies are not satisfied? Did you have a solution?

---

### Post by ActionParsnip on 2022-01-09
Where did you get the kernel from?

---

### Post by dnbattack on 2022-01-09
I have the same problem too.
I took the kernel from this link: [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.13/amd64/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.13/amd64/)

---

### Post by &amp;KyT$0P# on 2022-01-09
The package libssl3 does not exist in the normal Ubuntu repositories [until Ubuntu 22.04]("https://packages.ubuntu.com/jammy/libssl3"), which is not yet release.

Why do you need the 5.15 kernel?  If you really do need this particular 5.15 kernel, I would suggest you contact the maintainer of that repository about this.

---

### Post by ActionParsnip on 2022-01-10
As above, what, specifically, in the 5.15.13 kernel do you need? Does the kernel from the Ubuntu repositories not run all of your hardware OK?

---

### Post by dnbattack on 2022-01-10
The new kernel resolved the display not working issue after locking the screen or restarting my dell 7779.
Since then I have been updating the kernel myself

But, there are two problems left..
- blinking of the external screen (lowering the frequency slightly improved the situation, but did not solve the problem)
- blinking of the built-in screen, when after switching on the screen blinks 5-10 times and only after that it will start working

The following lines appear in the logs:

```

...
Jan 10 11:11:38 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Printing DDC gathered Modelines:
Jan 10 11:11:38 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Modeline "1920x1080"x0.0  143.30  1920 1936 1952 2140  1080 1083 1097 1116 +hsync -vsync (67.0 kHz eP)
Jan 10 11:11:38 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Modeline "1920x1080"x0.0  114.80  1920 1936 1952 2140  1080 1083 1097 1116 +hsync -vsync (53.6 kHz e)
Jan 10 11:11:39 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (WW) modeset(0): hotplug event: connector 95's link-state is BAD, tried resetting the current mode. You may be leftwith a black screen if this fails...
Jan 10 11:11:39 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): EDID vendor "AUO", prod id 4253
Jan 10 11:11:39 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Printing DDC gathered Modelines:
Jan 10 11:11:39 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Modeline "1920x1080"x0.0  143.30  1920 1936 1952 2140  1080 1083 1097 1116 +hsync -vsync (67.0 kHz eP)
Jan 10 11:11:39 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): Modeline "1920x1080"x0.0  114.80  1920 1936 1952 2140  1080 1083 1097 1116 +hsync -vsync (53.6 kHz e)
Jan 10 11:11:40 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (WW) modeset(0): hotplug event: connector 95's link-state is BAD, tried resetting the current mode. You may be leftwith a black screen if this fails...
Jan 10 11:11:40 leo-Inspiron-17-7779 /usr/libexec/gdm-x-session[3271]: (II) modeset(0): EDID vendor "AUO", prod id 4253
...

```

... but I have already ceased to believe that it can be solved.

---

### Post by fayaaz-ahmed on 2022-01-10
> **ActionParsnip said:**
> Where did you get the kernel from?

I have this problem and got it through using mainline using this PPA:
 [https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa](https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa)

I can't speak for others in this thread but I am running a 6600XT which should see some performance improvements with the 5.15 kernel and this is the reason for trying it.
I too am having this same libssl3 error.

---

