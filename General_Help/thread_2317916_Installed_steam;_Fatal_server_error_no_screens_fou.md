---
title: "Installed steam; Fatal server error: no screens found?"
date: 2016-03-21
forum: General Help
---

### Post by tim-connolly-321 on 2016-03-21
[COLOR=#111111][FONT=Ubuntu]I can't find any answers on this in any thread here, so here goes. PS - this is, quite obviously, my first time with Linux...
I have now twice installed XFCE onto my Toshiba Chromebook 2 using Crouton. After I install Steam via the Software Center, it works fine. But as soon as I restart Chrome OS and try to get into XFCE, I get the response at the foot of this message.
In order, again, I have only installed Crouton, installed Crouton / XFCE, installed Software Center and then installed Steam.
Any help very gratefully received and apologies if I've missed some relevant information - please just ask!
crosh> shell chronos@localhost / $ sudo startxfce4 Entering /mnt/stateful_partition/crouton/chroots/precise... /usr/bin/startxfce4: Starting X server
_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created.
X.Org X Server 1.11.3 Release Date: 2011-12-16 X Protocol Version 11, Revision 0 Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu Current Operating System: Linux localhost 3.10.18 #1 SMP Thu Mar 10 05:11:12 PST 2016 x86_64 Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=e4e36f0d-ca2b-5940-a7fe-a61287b5a2d8/PARTNROFF=1 hashtree=PARTUUID=e4e36f0d-ca2b-5940-a7fe-a61287b5a2d8/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=4e9b414bae166191f327061db1e0104e14931c37 salt=6e87672096a04fb9a0ba805901d389751453d204165b651c52f73d0c74f829e0" noinitrd vt.global_cursor_default=0 kern_guid=e4e36f0d-ca2b-5940-a7fe-a61287b5a2d8 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic
Build Date: 12 February 2015 02:49:01PM xorg-server 2:1.11.4-0ubuntu10.17 Current version of pixman: 0.30.2 Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/") to make sure that you have the latest version. Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown. (++) Log file: ", Time: Mon Mar 21 20:23:16 2016 (==) Using system config directory
Fatal server error: no screens found
Please consult the The X.Org Foundation support at for help. Please also check the log file at " for additional information.
ddxSigGiveUp: Closing log Server terminated with error (1). Closing log file. /usr/bin/xinit: giving up /usr/bin/xinit: unable to connect to X server: No such file or directory /usr/bin/xinit: server error Unmounting /mnt/stateful_partition/crouton/chroots/precise...


[/FONT][/COLOR]

---

