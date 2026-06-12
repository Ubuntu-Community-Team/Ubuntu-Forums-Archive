---
title: "Ubuntu 20.04 on USB stick does not see network"
date: 2021-06-04
forum: General Help
---

### Post by raymondvillain on 2021-06-04
Windows 10 on a desktop.  Booted to USB stick with 20.04.  I can see the files on the (Windows) C drive (in the graphical interface and in a terminal window).  No trouble moving around.  But I need to delete a directory, "C:/Windows/Softwaredistribution".  When I try this it fails.  Evidently Ubuntu on the USB stick is treating the windows files and directories as "read only".  Things didn't used to be this way (I think).  How to get around it?

Also the USB Ubuntu does not show the ethernet connection.  I've no idea why.  Do I just need to create a USB stick with an older version of Ubuntu?  Is this a new thing?

Any and all suggestions greatly appreciated.

---

### Post by sudodus on 2021-06-04
The live system may refuse to delete the directory because the Windows file system is

- either set read-only, but can be reset with read/write permissions when unmounted and mounted again. Please notice that the Linux sets ownership and permissions of Microsoft file systems when the file system is mounted, and these settings are inherited by all directories and files in the file systems.

- or not shut down completely (for example hibernated or semi-hibernated alias in 'fast startup' mode) - needs boot into Windows and reboot (not shutdown) before starting Ubuntu again

- or damaged, and needs repair in Windows, reboot (not shutdown) before starting Ubuntu again.

Please let us know if you need more details in order to delete that directory.

[hr][/hr]
Ubuntu can use ethernet in most computers. The success rate is lower for wireless networks (wifi). I am not good at troubleshooting network problems, so I hope someone else will chip in and help you with that problem.

---

### Post by scorp123 on 2021-06-04
> **raymondvillain said:**
>  How to get around it? 

Don't do that. There's a reason why Ubuntu treats Windows partitions as *"read only"*. Microsoft has done many (undocumented + secret) changes in Windows 10 regarding what gets written to Windows filesystems and how it gets written. Windows 10 is *"closed source"* after all. This is the exact reason why it's called like that. You're at risk of ruining your disk if you force Ubuntu to write to it. If you want to deal with Windows 10 filesystems then let Windows 10 handle it.

> **raymondvillain said:**
>  Also the USB Ubuntu does not show the ethernet connection.

What leads you to this conclusion? What's the output of this command:
```
ip a
```

---

### Post by ActionParsnip on 2021-06-05
If you want to delete the softwaredistribution folder simply stop the Windows Update service in Windows and rename it to "Softwaredistribution_old" start the service again then delete the "Softwaredistribution_old" folder. The service locks the folder as in use. Note this will remove the system's knowledge of installed updates but can be useful for reclaiming space or troubleshooting update issues

---

