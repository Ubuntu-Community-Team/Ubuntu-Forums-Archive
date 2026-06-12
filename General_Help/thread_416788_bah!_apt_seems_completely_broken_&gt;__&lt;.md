---
title: "bah! apt seems completely broken &gt;__&lt;"
date: 2007-04-21
forum: General Help
---

### Post by Stormx on 2007-04-21
Okay. I was installing gnome-office. here is the output of synaptic:

> (Reading database ... 261653 files and directories currently installed.)
Removing abiword ...
Selecting previously deselected package abiword-gnome.
(Reading database ... 261649 files and directories currently installed.)
Unpacking abiword-gnome (from .../abiword-gnome_2.4.6-1.1ubuntu2_i386.deb) ...
Selecting previously deselected package dia-gnome.
Unpacking dia-gnome (from .../dia-gnome_0.96.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package gnome-core.
Unpacking gnome-core (from .../gnome-core_1%3a2.14.3.3ubuntu1_all.deb) ...
Selecting previously deselected package inkscape.
Unpacking inkscape (from .../inkscape_0.45-0ubuntu4_i386.deb) ...
Selecting previously deselected package gnome-office.
Unpacking gnome-office (from .../gnome-office_1%3a2.14.3.3ubuntu1_all.deb) ...
Setting up abiword-gnome (2.4.6-1.1ubuntu2) ...
Setting up dia-gnome (0.96.1-0ubuntu1) ...
Segmentation fault
dpkg: error processing dia-gnome (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-core (2.14.3.3ubuntu1) ...

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660858] Oops: 0000 [#1]

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660963] CPU:    0

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660965] EIP:    0060:[find_inode_fast+23/80]    Not tainted VLI

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660967] EFLAGS: 00210202   (2.6.20-15-386 #2)

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660985] EIP is at find_inode_fast+0x17/0x50

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660989] eax: 5a678802   ebx: 0008e7b0   ecx: ea8a6b38   edx: 5a678802

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660994] esi: eefdd400   edi: c16c0224   ebp: 0008e7b0   esp: c5a99d9c
Setting up inkscape (0.45-0ubuntu4) ...

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.660998] ds: 007b   es: 007b   ss: 0068

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661002] Process update-mime (pid: 12978, ti=c5a98000 task=ca0d2550 task.ti=c5a98000)

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661005] Stack: 0008e7b0 c16c0224 eefdd400 c0175140 c5a99e3c 0008e7b0 c16c0224 c01754f4 

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661014]        00000000 d10b62b0 0008e7b0 ed15d994 eefdd400 c5a99e3c f09bfe49 c5a99f04 

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661022]        c0173b4b d092e094 ed15d994 c0caa0a8 f09d41c0 ed15d994 c5a99f04 c0169e18 

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661030] Call Trace:

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661038]  [ifind_fast+16/112] ifind_fast+0x10/0x70

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661048]  [iget_locked+52/288] iget_locked+0x34/0x120

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661063]  [<f09bfe49>] ext3_lookup+0x89/0x100 [ext3]

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661103]  [d_alloc+27/368] d_alloc+0x1b/0x170

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661116]  [do_lookup+328/400] do_lookup+0x148/0x190

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661137]  [__link_path_walk+1947/3264] __link_path_walk+0x79b/0xcc0

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661163]  [link_path_walk+67/192] link_path_walk+0x43/0xc0

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661200]  [do_path_lookup+117/400] do_path_lookup+0x75/0x190

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661207]  [getname+167/208] getname+0xa7/0xd0

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661217]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661230]  [vfs_lstat_fd+31/80] vfs_lstat_fd+0x1f/0x50

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661264]  [sys_lstat64+15/48] sys_lstat64+0xf/0x30

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661294]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661323]  =======================

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661325] Code: 00 89 da 89 f0 e8 ca 8d fb ff 83 c4 1c 5b 5e c3 8d 74 26 00 57 89 d7 56 89 c6 53 89 cb 8b 17 85 d2 75 08 eb 2d 85 c0 74 29 89 c2 <8b> 02 0f 18 00 90 39 5a 20 89 d1 75 ed 39 b2 88 00 00 00 75 e5 

Message from syslogd@localhost at Sat Apr 21 13:59:17 2007 ...
localhost kernel: [44211.661357] EIP: [find_inode_fast+23/80] find_inode_fast+0x17/0x50 SS:ESP 0068:c5a99d9c

Synaptic hung at this point. I manually killed it. Now whenever I go to do something with apt-get / synaptic / dpkg I get:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

On running this command, I am faced with:

> Setting up dia-gnome (0.96.1-0ubuntu1) ...

Which just hangs. I have absolutely no clue how to fix this issue! Can someone help?

---

### Post by Georgie-o on 2007-04-23
I've got  the same darn problem!  I am trying to use synaptic behind a firewall and while I had my I.T. folks add permission to the Main ubuntu repositories in the US, I still seemed to have many packages not installed or missing dependencies.  I believe while trying to install Macromedia it tried to download info from a different server and failed.  Now when I try to run Synaptic it says error as above and closes the program.  When Irun the dpkg it hangs up just the same.  Now I have a broken synaptic, or something is broken and it won't let me run Synaptic.

---

### Post by edieguez on 2007-04-23
I have the same problem as detailed here [http://ubuntuforums.org/showthread.php?t=417366&highlight=apt-get+segmentation]("http://ubuntuforums.org/showthread.php?t=417366&highlight=apt-get+segmentation")

---

