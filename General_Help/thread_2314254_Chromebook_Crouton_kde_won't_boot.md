---
title: "Chromebook Crouton kde won't boot"
date: 2016-02-19
forum: General Help
---

### Post by tmcdonagh12 on 2016-02-19
Hey so I dual booted my chromebook with chrome os and ubuntu kde. I usually press ctrl+alt+t shell then sudo startkde, and it will start but now I get this error

Entering /mnt/stateful_partition/crouton/chroots/precise...


_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created.


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 #1 SMP Mon Feb 8 23:28:26 PST 2016 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=19e2ec8a-1b16-364f-8846-2008c97cd1c2/PARTNROFF=1 hashtree=PARTUUID=19e2ec8a-1b16-364f-8846-2008c97cd1c2/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=83420448db55a77a441ea0b1238d1fa6cdfb0be5 salt=1dc2bd5d624c1be6b58b0f6712c6064332ef0c51cebca25d5da06dfab43666fd" noinitrd vt.global_cursor_default=0 kern_guid=19e2ec8a-1b16-364f-8846-2008c97cd1c2 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Fri Feb 19 11:46:28 2016
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

I can use sudo sh ~/Downloads/crouton -n precise -u and it will work once but it takes a while and is not at all practical. Any help would be greatly appreciated.
EDIT: I think that the problem may be caused by an installation error in software center when installing steam. Any help fixing this would also be appreciated.

---

