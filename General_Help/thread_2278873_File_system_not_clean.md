---
title: "File system not clean"
date: 2015-05-19
forum: General Help
---

### Post by MarcWord on 2015-05-19
Hello I am trying to do a system recovery on an ASUS k53sv with Windows 7 HOME premium 64bit that has a Wubi installation of Ubuntu 12.04 on it.  System recovery continues to fail and having used a system repair disk I am showing Windows 7 Home Premium (recovered) on (D:) OS (it should be C:).   I forgot to uninstall Ubuntu before attempting the system recovery.  I loaded a live boot Linux and  ran "Check Filesystem" from the Disk Utility and it reported that both the 102mb partition and the 622gb partition were "not clean".  The recovery partition reported as clean.  I have several questions.  From the live boot system I am able to see all my files in the 622 which were all backed up before I started this process.  I have a couple questions.

Are my problems related to the Wubi installation?  If so can I just delete it from the directory using the live boot usb drive?

Can I just delete both the partitions and expect System Recovery to reinstall the system afterwards or will that mess things up more?
Thanks

---

### Post by hakuna_matata on 2015-05-19
> **MarcWord said:**
> 
Are my problems related to the Wubi installation?

IMHO, your problems are not related to Wubi. Wubi does not change the file system of your Windows partitions. So a Windows recovery tool should have no problems because of Wubi.

Maybe, an unclean file system is a problem for a file recovery. But it could be also the other way round. A broken recovery has caused the unclean file system.

You didn't write if you got some error messages or reason codes during system recovery or during file check. 

But IHMO your problems are related to Windows, so maybe you will get some more help in Windows forums.

---

### Post by MarcWord on 2015-05-19
That's nice to know.  I checked on this PC which is running fine using 7, XP and wubi Ubuntu and it also shows the System Reserved and the regular partition as "unclean" in Disk Utility so I assume it is normal.   

Disk Utility SMART scan returned no error codes and reported all partitions as healthy.  

chkdsk showed all partitions with no errors also except for > "Failed to transfer logged messages to the event log with status 50."
Problem Signature 07:  MissingOsLoader 


Yeah digging away on other forums related to repairing the MBR also.

btw it's hard as hell to login to this site.

---

