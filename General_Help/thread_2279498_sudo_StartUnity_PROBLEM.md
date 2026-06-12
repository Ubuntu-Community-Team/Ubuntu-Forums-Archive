---
title: "sudo StartUnity PROBLEM"
date: 2015-05-23
forum: General Help
---

### Post by james135 on 2015-05-23
When I go into crosh>shell then type sudo Startyuntiy it comes up with this

Entering /usr/local/chroots/precise...

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.8.11 #1 SMP Fri May 8 14:15:23 PDT 2015 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=d68dfa31-f8fd-8448-8eca-51e2789f4d8d/PARTNROFF=1 hashtree=PARTUUID=d68dfa31-f8fd-8448-8eca-51e2789f4d8d/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=e97ebdb6d9d8dd4f0dd358a4ab75ad920e8fdc8a salt=4a0c1259c34f7d288ed55eb1c58f8b5d6aa076e316f433e4aadd29282b48de03" noinitrd vt.global_cursor_default=0 kern_guid=d68dfa31-f8fd-8448-8eca-51e2789f4d8d add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Sat May 23 19:57:53 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: No such file or directory
/usr/bin/xinit: server error
Not unmounting /usr/local/chroots/precise as another instance is using it.

Please help me

---

