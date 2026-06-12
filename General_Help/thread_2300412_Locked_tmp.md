---
title: "Locked /tmp"
date: 2015-10-25
forum: General Help
---

### Post by Kurt_Alan on 2015-10-25
I am troubleshooting vmplayer. I need access to a log in /tmp but /tmp is locked. How do I access it via CLI?

---

### Post by bapoumba on 2015-10-26
Hello, use **cd** to navigate to that directory, or **sudo cd** in case your user is not allowed (which looks like what you are describing). Make sure you give the whole path. What kind of problems are you running into ? Running VMs will lock files (so that no other VMs overwrite that space).
[https://www.vmware.com/support/ws55/doc/ws_disks_lockfiles.html](https://www.vmware.com/support/ws55/doc/ws_disks_lockfiles.html)

---

### Post by Kurt_Alan on 2015-11-01
> **bapoumba said:**
> Hello, use **cd** to navigate to that directory, or **sudo cd** in case your user is not allowed (which looks like what you are describing). Make sure you give the whole path. What kind of problems are you running into ? Running VMs will lock files (so that no other VMs overwrite that space).
[https://www.vmware.com/support/ws55/doc/ws_disks_lockfiles.html](https://www.vmware.com/support/ws55/doc/ws_disks_lockfiles.html)

I looked at Properties on the /tmp locked file. The owner was root but all functions in the next field were greyed out. I then tried ```
sudo cd /home/lucas/t
```

but when I hit Tab to complete the /mp in /tmp as expected this didn't happen.

I then read the vmplayer article for the link you provided about vmplayer locking files. It seems that I cannot access this file for a log file that I need for errors.

Unless you have another idea I'm marking this thread as "solved" This problem is a troubleshooting step for another problem with failure of vmplayer on MATE 14.04, so I think I'll approach that problem in another way.

---

### Post by Kurt_Alan on 2015-11-01
> **Kurt_Alan said:**
> I looked at Properties on the /tmp locked file. The owner was root but all functions in the next field were greyed out. I then tried ```
sudo cd /home/lucas/t
```

but when I hit Tab to complete the /mp in /tmp as expected this didn't happen.

I then read the vmplayer article for the link you provided about vmplayer locking files. It seems that I cannot access this file for a log file that I need for errors.

Unless you have another idea I'm marking this thread as "solved" This problem is a troubleshooting step for another problem with failure of vmplayer on MATE 14.04, so I think I'll approach that problem in another way.

More information:

I ran ```
 vmplayer
```  That gives me "VMware Kernel Module Updater," which says "Stopping VMware Services, Compiling Virtual Network Device, Running depmod, Starting VMware Services, ERROR: Unable to start services. See log file /tmp/vmware-root/vmware-modconfig-3288.log for details.

It seems that this is my only hope for troubleshooting this failure. But vmware player itself locks the same file it tells you to open, with no obvious way to open it.

The strange thing is that I have two machines I built with identical hardware and OS's: Ubuntu MATE 14.04 LTS. On one it's always worked great, on this one, not.

I even uninstalled and reinstalled.

Any solution besides giving up vmplayer on this machine and moving to VirtualBox?

---

### Post by bapoumba on 2015-11-02
[https://communities.vmware.com/message/2335864?z=N833r5](https://communities.vmware.com/message/2335864?z=N833r5)
[http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html](http://dandar3.blogspot.cz/2014/01/vmware-player-601-on-ubuntu-1404-alpha.html)

Maybe this patch ?

---

