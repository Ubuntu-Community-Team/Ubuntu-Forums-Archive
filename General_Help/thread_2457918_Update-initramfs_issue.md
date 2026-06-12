---
title: "Update-initramfs issue"
date: 2021-02-12
forum: General Help
---

### Post by v45ch300 on 2021-02-12
I'm currently running Kubuntu and when trying to install something from the terminal e.g. 'sudo apt-get firefox' I get the following error:

[FONT=monospace][COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR]
[/FONT]
After running [FONT=monospace][COLOR=#000000]'sudo dpkg --configure -a' the following happens:[/COLOR][/FONT]

update-initramfs: Generating /boot/initrd.img-5.4.0-65-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-5.4.0-59-generic

And it keeps going on trying lower versions and it just gets stuck there and there's nothing I can do.

How can I fix this?

Thank you!

---

### Post by ajgreeny on 2021-02-12
How many kernels do you have installed?  You show three in your post above; are there still more which the system is trying to deal with?

Show us the output of terminal command ```
dpkg -l linux-image*
```
Please use code tags for the terminal output.  There's a ***how-to*** in my signature below.

---

### Post by v45ch300 on 2021-02-12
```

[FONT=monospace][COLOR=#000000]Desired=Unknown/Install/Remove/Purge/Hold [/COLOR]
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name                                  Version      Architecture Description 
+++-=====================================-============-============-================================= 
un  linux-image                           <none>       <none>       (no description available) 
rc  linux-image-5.4.0-26-generic          5.4.0-26.30  amd64        Signed kernel image generic 
rc  linux-image-5.4.0-29-generic          5.4.0-29.33  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-31-generic          5.4.0-31.35  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-33-generic          5.4.0-33.37  amd64        Signed kernel image generic 
rc  linux-image-5.4.0-37-generic          5.4.0-37.41  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-39-generic          5.4.0-39.43  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-40-generic          5.4.0-40.44  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-42-generic          5.4.0-42.46  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-45-generic          5.4.0-45.49  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-47-generic          5.4.0-47.51  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-48-generic          5.4.0-48.52  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-51-generic          5.4.0-51.56  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-52-generic          5.4.0-52.57  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-53-generic          5.4.0-53.59  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-54-generic          5.4.0-54.60  amd64        Signed kernel image generic 
rc  linux-image-5.4.0-56-generic          5.4.0-56.62  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-58-generic          5.4.0-58.64  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-59-generic          5.4.0-59.65  amd64        Signed kernel image generic 
rc  linux-image-5.4.0-60-generic          5.4.0-60.67  amd64        Signed kernel image generic 
rc  linux-image-5.4.0-62-generic          5.4.0-62.70  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-64-generic          5.4.0-64.72  amd64        Signed kernel image generic 
ii  linux-image-5.4.0-65-generic          5.4.0-65.73  amd64        Signed kernel image generic 
ii  linux-image-generic                   5.4.0.65.68  amd64        Generic Linux kernel image 
un  linux-image-unsigned-5.4.0-26-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-29-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-31-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-33-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-37-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-39-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-40-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-42-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-45-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-47-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-48-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-51-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-52-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-53-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-54-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-56-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-58-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-59-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-60-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-62-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-64-generic <none>       <none>       (no description available) 
un  linux-image-unsigned-5.4.0-65-generic <none>       <none>       (no description available)
[/FONT]
```

Thank you!

---

### Post by tea for one on 2021-02-12
I think that [COLOR="#0000FF"]dpkg -l linux-image* [/COLOR] has listed available kernels rather than installed kernels.

Try this in the terminal and post the output in code tags:-
```
ls /boot | grep vmlinuz-

```

---

### Post by v45ch300 on 2021-02-12
This is the output:

```

[FONT=monospace][COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-31-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-33-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-39-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-40-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-42-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-45-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-47-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-48-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-51-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-52-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-53-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-54-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-58-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-59-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-64-generic [/COLOR]
[COLOR=#ff5454]**vmlinuz-**[/COLOR][COLOR=#000000]5.4.0-65-generic[/COLOR]
[/FONT]
```

---

### Post by deadflowr on 2021-02-12
Those are installed kernels.
Or at least all those marked with the ii status are installed.
Plenty of different ways to remove them.
Unless there some reason not to just run the apt autoremove command to clear them out.
append the --purge option to clear out the full package including the configurations,
```
sudo apt autoremove --purge
```

---

### Post by v45ch300 on 2021-02-12
I can't do that...

```

[FONT=monospace][COLOR=#000000]sudo apt autoremove --purge [/COLOR]
[sudo] password for leandro:  
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/COLOR]
[/FONT]
```

---

### Post by CelticWarrior on 2021-02-12
The error message tells you what to do.

---

### Post by v45ch300 on 2021-02-12
I know, that's the problem, take a look at my first post on top.

---

### Post by deadflowr on 2021-02-12
Then let the dpkg command run.
It'll take a while. You have 16 kernels installed.
How long did you run it before?
With as many kernels it has to deal with as it does I would expect it to run for a minimum of half an hour. Seriously.
(and that's the minimum, it might as well run well over a full hour, or even longer.)
If it to seems like it hangs at times, just let it go without trying to force it to stop.

---

### Post by v45ch300 on 2021-02-12
Oh ok, then! I will try that, I thought there was something wrong that's why I only waited like 4 minutes and forced it to stop. I'll leave it running for a while then and see how it goes! Thank you!

---

### Post by v45ch300 on 2021-02-12
That fixed it! Excellent! Thank you so much!

---

### Post by deadflowr on 2021-02-12
> **v45ch300 said:**
> That fixed it! Excellent! Thank you so much!

Now you should run the apt autoremove command,
which will also take a while.
But it'll remove most of the older kernels.
(If autoremove works correctly it'll leave just two kernels; The current in use one and the one before it as a fallback option.)

I was going to amend my previous statement of it taking over half an hour as the last time I had to deal with a system with that many old kernels my machine was a dinosaur.
Newer hardware should be a lot faster.

---

### Post by ajgreeny on 2021-02-12
Just  a minor warning of something to watch for!

If you have installed any packages from sources other then the standard repos it is just possible that autoremove may try to remove them so to check before any action is taken run the autoremove with the -s option to simulate what will happen.
As an example, I use get-iplayer installed from the application's own website and autoremove attempts to uninstall some of the packages needed for that to run properly.

If that happens for you and it tries to remove something you want to keep, you can then remove the unwanted linux-image versions using, for example, synaptic.

---

### Post by v45ch300 on 2021-02-12
That doesn't seem to work:

```
[FONT=monospace][COLOR=#000000]
sudo apt autoremove --purge [/COLOR]
[sudo] password for leandro:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/FONT]
```

---

### Post by ajgreeny on 2021-02-12
That is a bit sytrange so now please show us the output of command ```
cat /etc/apt/apt.conf.d/01autoremove
``` which may give us some clues why the command is not showing anything and then follow that with ```
cat /etc/apt/apt.conf.d/01autoremove-kernels
```
Once again please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by v45ch300 on 2021-02-12
```
[FONT=monospace][COLOR=#000000]
cat /etc/apt/apt.conf.d/01autoremove [/COLOR]
APT 
{ 
  NeverAutoRemove 
  { 
        "^firmware-linux.*"; 
        "^linux-firmware$"; 
        "^linux-image-[a-z0-9]*$"; 
        "^linux-image-[a-z0-9]*-[a-z0-9]*$"; 
  }; 

  VersionedKernelPackages 
  { 
        # kernels 
        "linux-.*"; 
        "kfreebsd-.*"; 
        "gnumach-.*"; 
        # (out-of-tree) modules 
        ".*-modules"; 
        ".*-kernel"; 
  }; 

  Never-MarkAuto-Sections 
  { 
        "metapackages"; 
        "contrib/metapackages"; 
        "non-free/metapackages"; 
        "restricted/metapackages"; 
        "universe/metapackages"; 
        "multiverse/metapackages"; 
  }; 

  Move-Autobit-Sections 
  { 
        "oldlibs"; 
        "contrib/oldlibs"; 
        "non-free/oldlibs"; 
        "restricted/oldlibs"; 
        "universe/oldlibs"; 
        "multiverse/oldlibs"; 
  }; 
};


[/FONT]
```

```
[FONT=monospace][COLOR=#000000]
cat /etc/apt/apt.conf.d/01autoremove-kernels [/COLOR]
// DO NOT EDIT! File autogenerated by /etc/kernel/postinst.d/apt-auto-removal 
APT::NeverAutoRemove 
{ 
   "^linux-.*-5\.4\.0-64-generic$"; 
   "^linux-.*-5\.4\.0-65-generic$"; 
   "^kfreebsd-.*-5\.4\.0-64-generic$"; 
   "^kfreebsd-.*-5\.4\.0-65-generic$"; 
   "^gnumach-.*-5\.4\.0-64-generic$"; 
   "^gnumach-.*-5\.4\.0-65-generic$"; 
   "^.*-modules-5\.4\.0-64-generic$"; 
   "^.*-modules-5\.4\.0-65-generic$"; 
   "^.*-kernel-5\.4\.0-64-generic$"; 
   "^.*-kernel-5\.4\.0-65-generic$"; 
}; 
/* Debug information: 
# dpkg list: 
rc  linux-image-5.4.0-26-generic                      5.4.0-26.30                                 amd64        Signed kernel image generic 
rc  linux-image-5.4.0-29-generic                      5.4.0-29.33                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-31-generic                      5.4.0-31.35                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-33-generic                      5.4.0-33.37                                 amd64        Signed kernel image generic 
rc  linux-image-5.4.0-37-generic                      5.4.0-37.41                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-39-generic                      5.4.0-39.43                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-40-generic                      5.4.0-40.44                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-42-generic                      5.4.0-42.46                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-45-generic                      5.4.0-45.49                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-47-generic                      5.4.0-47.51                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-48-generic                      5.4.0-48.52                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-51-generic                      5.4.0-51.56                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-52-generic                      5.4.0-52.57                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-53-generic                      5.4.0-53.59                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-54-generic                      5.4.0-54.60                                 amd64        Signed kernel image generic 
rc  linux-image-5.4.0-56-generic                      5.4.0-56.62                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-58-generic                      5.4.0-58.64                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-59-generic                      5.4.0-59.65                                 amd64        Signed kernel image generic 
rc  linux-image-5.4.0-60-generic                      5.4.0-60.67                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-62-generic                      5.4.0-62.70                                 amd64        Signed kernel image generic 
ii  linux-image-5.4.0-64-generic                      5.4.0-64.72                                 amd64        Signed kernel image generic 
iF  linux-image-5.4.0-65-generic                      5.4.0-65.73                                 amd64        Signed kernel image generic 
ii  linux-image-generic                               5.4.0.65.68                                 amd64        Generic Linux kernel image 
# list of installed kernel packages: 
5.4.0-31-generic 5.4.0-31.35 
5.4.0-33-generic 5.4.0-33.37 
5.4.0-39-generic 5.4.0-39.43 
5.4.0-40-generic 5.4.0-40.44 
5.4.0-42-generic 5.4.0-42.46 
5.4.0-45-generic 5.4.0-45.49 
5.4.0-47-generic 5.4.0-47.51 
5.4.0-48-generic 5.4.0-48.52 
5.4.0-51-generic 5.4.0-51.56 
5.4.0-52-generic 5.4.0-52.57 
5.4.0-53-generic 5.4.0-53.59 
5.4.0-54-generic 5.4.0-54.60 
5.4.0-58-generic 5.4.0-58.64 
5.4.0-59-generic 5.4.0-59.65 
5.4.0-62-generic 5.4.0-62.70 
5.4.0-64-generic 5.4.0-64.72 
5.4.0-65-generic 5.4.0-65.73 
# list of different kernel versions: 
5.4.0-65.73 
5.4.0-64.72 
5.4.0-62.70 
5.4.0-59.65 
5.4.0-58.64 
5.4.0-54.60 
5.4.0-53.59 
5.4.0-52.57 
5.4.0-51.56 
5.4.0-48.52 
5.4.0-47.51 
5.4.0-45.49 
5.4.0-42.46 
5.4.0-40.44 
5.4.0-39.43 
5.4.0-33.37 
5.4.0-31.35 
# Installing kernel: 5.4.0-65.73 (5.4.0-65-generic) 
# Running kernel: 5.4.0-64.72 (5.4.0-64-generic) 
# Last kernel: 5.4.0-65.73 
# Previous kernel: 5.4.0-64.72 
# Kernel versions list to keep: 
5.4.0-64.72 
5.4.0-65.73 
# Kernel packages (version part) to protect: 
5\.4\.0-64-generic 
5\.4\.0-65-generic 
*/


[/FONT]
```

---

### Post by deadflowr on 2021-02-13
Here are two links to removing old kernels:
[https://askubuntu.com/questions/401581/bash-one-liner-to-delete-only-old-kernels]("https://askubuntu.com/questions/401581/bash-one-liner-to-delete-only-old-kernels")
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

The /etc/apt/apt.conf.d/-01autoremove-kernels is an odd file since it only gets updated when a new kernel is installed, so it's hard to tell how accurate it is to the current package status.
(Mine, for instance, shows a bunch of rc listings which have cleared out since the last kernel was installed)

---

### Post by v45ch300 on 2021-02-13
Excellent, I followed the second link and it worked. Thank you so much for your help! :)

---

