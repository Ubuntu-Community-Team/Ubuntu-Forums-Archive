---
title: "Slow boot due to swap?"
date: 2007-02-06
forum: General Help
---

### Post by testube_babies on 2007-02-06
Ever since I reinstalled Edgy about a week ago, I've noticed slow boot-up times.  I finally got the brains to look at /var/log/boot and found this:

Feb  6 20:09:15 rcS:  * Activating swapfile swap...          [ ok ]
Feb  6 20:10:33 rcS:  * Configuring network interfaces... [ ok ]

If I'm reading this correctly, it takes ~80 seconds to activate swap.  Or is that 80 seconds spent on activating the network interfaces?  Or could it have anything to do with the warning that ntfs-3g spits out (see below)?


Full /var/log/boot:

```

Feb  6 14:09:11 rcS:  * Reading files needed to boot...         
 [ ok ]
Feb  6 14:09:11 rcS:  * Setting preliminary keymap...         
 [ ok ]
Feb  6 14:09:11 rcS:  * Preparing restricted drivers...         
 [ ok ]
Feb  6 14:09:11 rcS:  * Starting basic networking...         
 [ ok ]
Feb  6 14:09:11 rcS:  * Starting kernel event manager...         
 [ ok ]
Feb  6 20:09:14 rcS:  * Loading hardware drivers...         
 [ ok ]
Feb  6 20:09:14 rcS:  * Loading manual drivers...         
 [ ok ]
Feb  6 20:09:14 rcS:  * Starting FUSE:          
 [ ok ]
Feb  6 20:09:15 rcS:  * Mounting local filesystems...         WARNING: Old FUSE kernel module detected. This means, some driver features
Feb  6 20:09:15 rcS:          are not available (swap file on NTFS, boot from NTFS by LILO),
Feb  6 20:09:15 rcS:          and unmount is not safe unless you make sure the ntfs-3g process
Feb  6 20:09:15 rcS:          naturally terminates after calling 'umount'. The safe FUSE kernel
Feb  6 20:09:15 rcS:          driver is included in the official Linux kernels since version
Feb  6 20:09:15 rcS:          2.6.20-rc1, or in the FUSE 2.6 software package. Please see the
Feb  6 20:09:15 rcS:          next page for more help: http://www.ntfs-3g.org/support.html#fuse26
Feb  6 20:09:15 rcS: 
Feb  6 20:09:15 rcS: WARNING: Old FUSE kernel module detected. This means, some driver features
Feb  6 20:09:15 rcS:          are not available (swap file on NTFS, boot from NTFS by LILO),
Feb  6 20:09:15 rcS:          and unmount is not safe unless you make sure the ntfs-3g process
Feb  6 20:09:15 rcS:          naturally terminates after calling 'umount'. The safe FUSE kernel
Feb  6 20:09:15 rcS:          driver is included in the official Linux kernels since version
Feb  6 20:09:15 rcS:          2.6.20-rc1, or in the FUSE 2.6 software package. Please see the
Feb  6 20:09:15 rcS:          next page for more help: http://www.ntfs-3g.org/support.html#fuse26
Feb  6 20:09:15 rcS: 
Feb  6 20:09:15 rcS: 
 [ ok ]
Feb  6 20:09:15 rcS:  * Activating swapfile swap...         
 [ ok ]
Feb  6 20:10:33 rcS:  * Configuring network interfaces...         
 [ ok ]
Feb  6 20:10:33 rcS:  * Setting up console keymap...         
 [ ok ]
Feb  6 20:10:32 rc2:  * Saving VESA state...         
 [ ok ]
Feb  6 20:10:32 rc2:  * Loading ACPI modules...         
 [ ok ]
Feb  6 20:10:32 rc2:  * Starting ACPI services...         
 [ ok ]
Feb  6 20:10:33 rc2:  * Starting system log...         
 [ ok ]
Feb  6 20:10:33 rc2:  * Starting kernel log...         
 [ ok ]
Feb  6 20:10:34 rc2:  * Starting GNOME Display Manager...         
 [ ok ]
Feb  6 20:10:35 rc2:  * Starting Common Unix Printing System: cupsd         
 [ ok ]
Feb  6 20:10:35 rc2:  * Starting HP Linux Printing and Imaging System         
 [ ok ]
Feb  6 20:10:36 rc2:  * Starting system message bus dbus         
 [ ok ]
Feb  6 20:10:45 rc2:  * Starting Hardware abstraction layer hald         
 [ ok ]
Feb  6 20:10:45 rc2:  * Starting DBUS aware dhcp client: dhcdbd         
 [ ok ]
Feb  6 20:10:45 rc2:  * Starting NetworkManager daemon         
 [ ok ]
Feb  6 20:10:45 rc2:  * Starting NetworkManager dispatcher         
 [ ok ]
Feb  6 20:10:46 rc2:  * Starting System Tools Backends system-tools-backends         
 [ ok ]
Feb  6 20:10:48 rc2:  * Starting the Firestarter firewall...         
 [ ok ]
Feb  6 20:10:48 rc2:  * Starting disk temperature monitoring daemon hddtemp:         
 [ ok ]
Feb  6 20:10:48 rc2:  * Starting powernowd...          
 [ ok ]
Feb  6 20:10:48 rc2: Starting internet superserver: xinetd.
Feb  6 20:10:48 rc2:  * Starting Bluetooth services         
 [ ok ]
Feb  6 20:10:49 rc2:  * Starting anac(h)ronistic cron: anacron         
 [ ok ]
Feb  6 20:10:49 rc2:  * Starting deferred execution scheduler atd         
 [ ok ]
Feb  6 20:10:49 rc2:  * Starting periodic command scheduler...         
 [ ok ]
Feb  6 20:10:49 rc2:  * Enabling additional executable binary formats binfmt-support         
 [ ok ]
Feb  6 20:10:49 rc2:  * Checking battery state...         
 [ ok ]
Feb  6 20:10:49 rc2:  * Running local boot scripts (/etc/rc.local)         
 [ ok ]

```

---

### Post by chalex on 2007-02-06
You could test this by commenting out the swap partition from your /etc/fstab, then rebooting.

---

### Post by testube_babies on 2007-02-06
> **chalex said:**
> You could test this by commenting out the swap partition from your /etc/fstab, then rebooting.

/var/log/boot still reports the same as before, even without swap!

Feb  6 21:26:53 rcS:  * Activating swapfile swap...           [ ok ]
Feb  6 21:28:13 rcS:  * Configuring network interfaces...  [ ok ]

So I guess swap isn't the problem.  I'll try disabling networking and ntfs-3g if at all possible and see if they are the culprits.

---

### Post by testube_babies on 2007-02-06
My wireless card was the culprit.  It's apparently a bug that needs to be worked out.  There's a simple hack here that "fixes" the problem:
[http://www.ubuntuforums.org/showpost.php?p=1837754&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1837754&postcount=3)

---

### Post by chalex on 2007-02-06
Don't forget to put your swap back ;)

---

