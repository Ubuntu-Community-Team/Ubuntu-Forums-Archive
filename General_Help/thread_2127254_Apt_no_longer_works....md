---
title: "Apt no longer works..."
date: 2013-03-19
forum: General Help
---

### Post by britesc on 2013-03-19
Hi,
Every time I run apt or dpkg in any guise I get the following end result.

> 
install@ULS022C00:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-2
6-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-26-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-26-generic.
postinst line 1010.
dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
dpkg: dependency problems prev
ent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.5.0-26-generic; however:
  Package linux-image-extra-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
dpkg: dependency problems prev
ent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
Errors were encountered while
processing:
 linux-image-extra-3.5.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
install@ULS022C00:~$


Could someone please advise me how to resolve this problem?
I think it may be related to this message which I have just started getting...

> 
 => /boot is using 96.5% of 227MB


I am running Ubuntu 12.10 (GNU/Linux 3.5.0-23-generic x86_64) on an old headless WHS from Acer (H-340) which has an internal ram disk (/dev/sde1) which I setup as /boot during install as the boot image was small enough.

I think I need to move boot back onto the main hard disk and waste the ram disk. So even if that is not the problem, could someone advise me how to move boot?

Appreciate any support.
Kind reagrds,
jB :cool:

---

### Post by Bashing-om on 2013-03-19
britesc; Hi !

Agree, looks like a space constraint situation.
The following command is useful for finding out which directories are using all your space...
```
du -h --max-depth=1 | sort -hr
```
If it is the boot partition that is full, I recommend sysnaptic to remove older kernels and related files:
(synaptic is no longer installed by default)
The command uname -a in a terminal will tell you which kernel you are running - you keep it and as well as one other (for fall back reasons)....then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
When done remember to update grub !
```
sudo update-grub
``` 
  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).[INDENT=2]
this works for me, hope it helps you too

[/INDENT]

---

### Post by britesc on 2013-03-19
Hi Bashing-om,

Many thanks for the reply. Slight difficulty (isn't there always), it's a server with no gui.

Regards,

jB :cool:

---

### Post by Bashing-om on 2013-03-19
britesc; Regret the delay getting back to ya, bust forum.

Not having the GUI requires a detour in finding and removing the older kernels and headers. I have always used "synaptic" for the ease of use. The same thing can be done from the command line. I have seen the method. If needed I will hunt the procedure up.
But first tell me that the du code shows /boot as at capacity and will proceed on.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by britesc on 2013-03-20
Hi,

Solved. Yes it was to do with limited space.
I first off installed the reduced desktop, synaptic via ssh.
Logged in and found synaptic.
Followed your advice.'
Then via ssh rebuilt grub and voila I am back down to 53m so plenty of space and performance increase.
I will keep an eye on this now.
If I can do similar via webmin I will remove the desktop as it is veeeerrrrrrry slow.

Thanks and kind regards, another happy bunny,
jB :cool: No I am not cool just disabled and partially sighted.

---

### Post by schragge on 2013-03-20
The following console command will remove all kernels, but the latest:
```

sudo apt-get purge linux-image-{[0-9],`uname -r`+}

```
If you want to retain two last kernels (the latest and the previous one), modify it as
```

sudo apt-get purge linux-image-{[0-9],`uname -r`+,`readlink /vmlinuz.old|cut -d- -f2-`+}

``` It will work so long as you have at least two kernels installed. You can see what an apt-get command is trying to do by adding the -s option like this:
```
apt-get -s purge linux-image-{[0-9],`uname -r`+}
```

---

### Post by britesc on 2013-03-20
Thank you.
This is why linux is great. 75 ways at least to do something. All of them correct.
Kind regards,
jB :cool:

---

### Post by Bashing-om on 2013-03-20
britesc; Pleased you are up and running.
I had hunted up          schragge's instructions in another thread.
As you are good to go; please mark this thread as solved. That aids us and others seeking solutions.
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=5]
Happy ubuntu'n

[/INDENT]

---

