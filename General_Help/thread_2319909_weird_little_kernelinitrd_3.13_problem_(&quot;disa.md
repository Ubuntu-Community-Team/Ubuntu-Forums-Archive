---
title: "weird little kernel/initrd 3.13 problem (&quot;disagrees about version&quot;)"
date: 2016-04-08
forum: General Help
---

### Post by hes2 on 2016-04-08
Hello all,
I have a really strange problem with three diferrent (but same model) Intel Atom D525-based PCs - every so often, my installed Lubuntu 14.04 (with ubuntu kernel 3.13) hangs during boot with messages like these: 

```

[    5.582437] pps_core: disagrees about version of symbol schedule_timeout
[    5.595867] pps_core: Unknown symbol schedule_timeout (err -22)
[    5.717685] psmouse: disagrees about version of symbol schedule_timeout
[    5.730985] psmouse: Unknown symbol schedule_timeout (err -22)
[...]
[    9.594958] usbhid: disagrees about version of symbol schedule_timeout
[    9.611268] usbhid: Unknown symbol schedule_timeout (err -22)
[    9.629067] usbhid: disagrees about version of symbol schedule_timeout
[    9.645390] usbhid: Unknown symbol schedule_timeout (err -22)
[...]
[   12.182255] reiserfs: disagrees about version of symbol do_sync_read
[   12.198321] reiserfs: Unknown symbol do_sync_read (err -22)
[   12.213071] reiserfs: disagrees about version of symbol current_fs_time
[   12.229643] reiserfs: Unknown symbol current_fs_time (err -22)
[   12.249711] reiserfs: disagrees about version of symbol do_sync_read
[   12.265728] reiserfs: Unknown symbol do_sync_read (err -22)
[   12.280441] reiserfs: disagrees about version of symbol current_fs_time
[   12.296939] reiserfs: Unknown symbol current_fs_time (err -22)

```

The last messages prevent the reiserfs driver from loading, which results in a boot failure because the reiserfs system partition cannot be found or mounted. This all happens while the PC is still running off the initrd grub has loaded along with the kernel.

From what I gather, this error ususally means that the modules to be loaded are incompatible with the kernel - but that can't be the case here. First of all the initrd was built along with the kernel and contains only modules with the exact same kernel number. Second of all, this happens only every twelve to 20 boots; the other 19, the exact same kernel and initrd boot without a problem, and without any of the above messages. 

I've run memtest on all PCs without any errors whatsoever, I've SMART-tested all three hard drives (100Gig Toshiba netboot drives), again no errors. But when I switch to a different hard drive (that one's from Hitachi), this problem doesn't occur anymore (i've literally done 500 reboots!). 

How can this problem have anything to do with the hard drive, though? The drives were running fine for several months before (using Windows XP, which I want to finally get rid of), plus I cannot change all the hard drives (there are about 50 more kiosk systems out there which would need to be recalled and retrofitted).  

Can anybody shed any light on this strange behavior? Any help is appreciated.

TIA, Michael.

---

