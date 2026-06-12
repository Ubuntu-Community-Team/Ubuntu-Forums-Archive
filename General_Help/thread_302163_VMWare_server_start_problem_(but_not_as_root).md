---
title: "VMWare server: start problem (but not as root?)"
date: 2006-11-18
forum: General Help
---

### Post by stengah on 2006-11-18
I'm running edgy and have installed VMware server. Seemed to run fine, until I figured out yeaterday that I wanted to create and allocate space for a new virtual macine on a separate partition (ext). In order to be permitted to change the output destination for the virtual mackine I had to run VMware as root (sudo), so I did.

Now I cannot start VMware from the menu nor terminal as a regular user. I get this output from the terminal:

[INDENT]mads@mads-laptop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/mads/.vmware/preferences": Permission denied.

VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/mads/.vmware/preferences": Permission denied.
A log file is available in "/tmp/vmware-mads/ui-5643.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.
[/INDENT]

Man, this is annoying. Tried suggestions put forward in similar 'won't start threads', but nothings seems to do the trick.

The wierd part is that I can start VMware server as root by typing sudo vmware in the terminal?

Qualified suggestions would be greatly appreciated. Thanks!](*,)

---

### Post by BLTicklemonster on 2006-11-26
Dude, I've been looking all over the place for an answer, and here it is:

[http://www.ubuntuforums.org/showpost.php?p=1514238&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1514238&postcount=10)

---

