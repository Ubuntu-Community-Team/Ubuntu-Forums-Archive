---
title: "Problem setting up permissive mode SELinux on Ubuntu 7.04"
date: 2007-05-10
forum: General Help
---

### Post by quark_77 on 2007-05-10
Hi All,

I'm wondering how to get SELinux up and running properly on Ubuntu? Support for it at the moment seems a little non-existent but FC6 Zod LiveCD has a nice graphical tool & SELinux running smoothly and I'd like to achieve the same on Ubuntu.

With a little difficulty I installed selinux-policy-default. I updated initramfs as the package suggested and modified my kernel line:
```
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro selinux=1 enforcing=0
```

What I'm trying to do is run SELinux in permissive mode so I can debug my policy and work out what tweaks are needed. I'm running this on a Desktop install at the moment but intend to do so on a server install once I can copy a working policy.

My understanding was that permissive mode enabled selinux in a logging-only mode so errors would be dumped but we wouldn't actually be restricted by the policy. However, as far as I can tell SELinux is not running on boot, because:
```
$ newrole
Sorry, newrole may be used only on a SELinux kernel.
```

However, given the following output it looks like SELinux is working:
```
$ dmesg | fgrep SELinux
[   24.027762] SELinux:  Initializing.
[   24.027965] SELinux:  Starting in permissive mode
[    0.964000] SELinux:  Registering netfilter hooks

$ dmesg | fgrep selinux
[    0.000000] Kernel command line: root=/dev/mapper/root ro selinux=1 enforcing=0 
[   39.212000] selinux_register_security:  Registering secondary module capability

```
Also:
```
session required pam_selinux.so multiple
```
Has been placed in /etc/pam.d/login and /etc/pam.d/ssh. Also, /selinux is mounted as follows: none on /selinux type selinuxfs (rw).

What I can't understand is how I get SELinux actually running in permissive mode on boot, as it currently doesn't appear to be. Only once I've managed that can I actually debug the policy as dmesg | grep avc gives no output in the current state.

Thanks in advance for all your help, I posted this in the servers & security section previously and got no answers.

Quark_77

---

### Post by quark_77 on 2007-05-15
It's hard to believe nobody is interested in SELinux as a security measure... I've heard it said the NSA runs a server to which they can give you the root password and it'll still be unbreakable... given that most attackers will attack the root account this sort of technology has to be worthwhile...

I have made a few changes to my custom kernel configuration file which I shall be trying soon, I would appreciate any feedback you may have regarding SELinux & your experiences.

Quark_77

---

### Post by ice60 on 2007-05-18
hi, if you are just testing things out you could try apparmor. i use it with suse without too many problems. 

you tell it you want to profile an app, then start and run that app making sure you do everything you want that app to do e.g. if you are profiling a browser open a PDF with it. then when you have closed the program apparmor will then make a profile for it.

once you have profiled a program you can run an update wizard that will run through things that have been disallowed so you can allow them if you want.

anyway, here are some SELinux links -
[http://www.linuxsecurity.com/content/blogcategory/171/178/](http://www.linuxsecurity.com/content/blogcategory/171/178/)

---

### Post by seamless on 2007-05-18
SELinux is mounted in /selinux. If that directory doesn't exist then there is your problem. Otherwise it should be populated with files which can give you a lot of information about the state of SELinux. I'm not sure if it is required on Ubuntu but you may have to add an entry to /etc/fstab as well. If required the entry would read:
```
none    /selinux        selinuxfs       defaults        0       0
```

I would also recommend you check out the ref-policy. It is the policy that Fedora ships with and the one that is being actively developed.

SELinux isn't very well supported on Ubuntu because of how complicated and honestly it is overkill on a desktop system. Also it causes a noticeable (estimated by the NSA at 7%) system slow down.

> **&#8221 said:**
> if you are just testing things out you could try apparmor.
Apparmor is easier but does not provide anywhere near the security that SELinux can.

---

### Post by quark_77 on 2007-05-19
Hi All,

Really appreciate the feedback - it's quite obvious SELinux is unsupported. I've installed ref-policy-targeted from the repos as seamless suggested. I solved the problem of the policy not loading with the system...

Upstart, Ubuntu's version of /sbin/init is not patched to support SELinux policies - basically I had to download System V Init (from freshmeat.net), the version of init every other linux distribution uses, patch it, install it and reboot... that done I can safely say SELinux loads on boot!!

That's not the end of the errors, mind you... I intend to google these but anyone with any experience is of course welcome to post!! (Hint hint!)

Firstly, here's an extract from dmesg showing init throwing its toys out:
```
[ 1121.752000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587497
[ 1121.804000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=20971687
[ 1122.960000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=20971688
[ 1124.112000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=20971689
[ 1125.288000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=29447574
[ 1125.304000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=41966170
[ 1125.304000] audit(1179577587.382:195): avc:  denied  { name_bind } for  pid=4606 comm="portmap" src=111 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:portmap_port_t tclass=udp_socket
[ 1125.304000] audit(1179577587.382:196): avc:  denied  { name_bind } for  pid=4606 comm="portmap" src=966 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:reserved_port_t tclass=udp_socket
[ 1125.304000] audit(1179577587.382:197): avc:  denied  { name_bind } for  pid=4606 comm="portmap" src=111 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:portmap_port_t tclass=tcp_socket
[ 1125.304000] audit(1179577587.382:198): avc:  denied  { name_bind } for  pid=4606 comm="portmap" src=967 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:reserved_port_t tclass=tcp_socket
[ 1126.308000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587498
[ 1126.316000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587499
[ 1126.324000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587500
[ 1126.340000] audit(1179577588.418:199): avc:  denied  { getattr } for  pid=4645 comm="setupcon" name="tty1" dev=tmpfs ino=2514 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.340000] audit(1179577588.418:200): avc:  denied  { write } for  pid=4645 comm="setupcon" name="tty1" dev=tmpfs ino=2514 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.340000] audit(1179577588.418:201): avc:  denied  { ioctl } for  pid=4646 comm="echo" name="tty1" dev=tmpfs ino=2514 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.340000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=4194494
[ 1126.340000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=41973070
[ 1126.368000] audit(1179577588.446:202): avc:  denied  { read } for  pid=4647 comm="consolechars" name="tty1" dev=tmpfs ino=2514 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.380000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=29447546
[ 1126.400000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=21138431
[ 1126.416000] audit(1179577588.494:203): avc:  denied  { create } for  pid=4651 comm="udevd" name="vcs2" scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.420000] audit(1179577588.498:204): avc:  denied  { unlink } for  pid=4654 comm="udevd" name="vcs2" dev=tmpfs ino=17234 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tty_device_t tclass=chr_file
[ 1126.504000] audit(1179577588.582:205): avc:  denied  { ioctl } for  pid=4741 comm="loadkeys" name="tty" dev=tmpfs ino=6730 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:devtty_t tclass=chr_file
[ 1126.716000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587501
[ 1126.716000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=20996451
[ 1126.720000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587502
[ 1126.720000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587503
[ 1126.720000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=37851912
[ 1126.724000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=133
[ 1126.728000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=41966549
[ 1126.728000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=54531792
[ 1126.760000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=55277275
[ 1126.780000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=42850742
[ 1126.816000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587504
[ 1126.816000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587505
[ 1126.820000] audit(1179577589.095:206): avc:  denied  { setattr } for  pid=4784 comm="chown" name="screen" dev=tmpfs ino=17789 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tmpfs_t tclass=dir
[ 1126.820000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=41986132
[ 1126.844000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=17519111
[ 1126.960000] audit(1179577589.235:207): avc:  denied  { relabelfrom } for  pid=4792 comm="restorecon" name=".X11-unix" dev=dm-0 ino=149921 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:unlabeled_t tclass=dir
[ 1126.960000] audit(1179577589.235:208): avc:  denied  { relabelto } for  pid=4792 comm="restorecon" name=".X11-unix" dev=dm-0 ino=149921 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:xdm_tmp_t tclass=dir
[ 1127.056000] audit(1179577589.331:209): avc:  denied  { relabelto } for  pid=4797 comm="restorecon" name=".ICE-unix" dev=dm-0 ino=5417558 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:ice_tmp_t tclass=dir
[ 1127.060000] inode_doinit_with_dentry:  context_to_sid(kernel) returned 22 for dev=dm-0 ino=12587506
[ 1127.064000] audit(1179577589.335:210): avc:  denied  { setattr } for  pid=4807 comm="chmod" name="utmp" dev=tmpfs ino=17822 scontext=system_u:system_r:kernel_t tcontext=system_u:object_r:tmpfs_t tclass=file
```

That's 45 lines from 1156....

Secondly, I keep getting this error:
```
[ 1184.216000] security_compute_av:  unrecognized class 57
```

Which happens when I log in (which takes about 5-6 mins as opposed to 30 seconds or less normally). Finally, I can't use the internet or my local network... Oh, and SELinux thinks it IS in permissive mode:
```
root@quark_77s_pc:~# sestatus
SELinux status:                 enabled
SELinuxfs mount:                /selinux
Current mode:                   permissive
Mode from config file:          permissive
Policy version:                 21
Policy from config file:        .
```

So for now selinux=0 has been set until I fix these issues. Any help with the above would be appreciated, if I don't find an answer I'll post again...

I agree, SELinux is probably overkill on the desktop but very useful on servers... I'm not going to start on server setups until I'm confident enough configuring what I need to on my laptop.

Thanks once again for your help,

Quark_77

---

