---
title: "Fatal Error:No screens founded"
date: 2016-07-12
forum: General Help
---

### Post by howk890 on 2016-07-12
So, after when I installed steam, it doesn't work. After that, my Linux is not working because of a fatal error of no screens. If you have the time, could you help? Thanks

crosh> shell
chronos@localhost / $ sudo startunity
Entering /mnt/stateful_partition/crouton/chroots/precise...

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root



This what happened:
X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.18.0-11125-g013294a #1 SMP PREEMPT Thu Jun 23 01:39:31 PDT 2016 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=b8b4ea46-61d4-0844-9afe-732105da49ac/PARTNROFF=1 hashtree=PARTUUID=b8b4ea46-61d4-0844-9afe-732105da49ac/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=c7c4998623bfdbdbaa2ec1ad3df713d809be64b6 salt=ec14a51ab468eff27065893419dbf77016a86475d5ac647a13b9370be205ad0e" noinitrd vt.global_cursor_default=0 kern_guid=b8b4ea46-61d4-0844-9afe-732105da49ac add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Tue Jul 12 18:10:12 2016
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
Unmounting /mnt/stateful_partition/crouton/chroots/precise...

---

### Post by howk890 on 2016-07-15
Nevermind already fixed it :/

Sorry, though I just had to update it.

---

