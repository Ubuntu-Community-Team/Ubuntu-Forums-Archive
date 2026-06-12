---
title: "Xubuntu--help"
date: 2007-06-09
forum: General Help
---

### Post by Jerr973 on 2007-06-09
I just installed XUBUNTU 7.04 and running fine except that am trying to access my second drive and asking me for an administartive p/w  but it never asked me for one during install.  So ok is there a set pass for it?  any and all help would be appreciated..

---

### Post by frafu on 2007-06-09
Hello, 

The Accessibility Forum being used to discuss Assistive Software for disabled, I moved this thread to the General Help Forum. 

Have a nice day. 

Francesco

---

### Post by ugm6hr on 2007-06-09
> **Jerr973 said:**
> I just installed XUBUNTU 7.04 and running fine except that am trying to access my second drive and asking me for an administartive p/w  but it never asked me for one during install.  So ok is there a set pass for it?  any and all help would be appreciated..

It's the same password for the first user you added at the time of installing Xubuntu (i.e. probably the password you use to log into Xubuntu, assuming you installed it yourself).  

If you want the drive to be auto-mounted at boot (without a password), then look here for a bit of help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
If you do follow this - don't forget to substitute "/dev/hda1" or "/dev/hdb1" for "/dev/*your_drive_partition*", and "/windows" or "/fat_files" for "/media/*your_drive_name*"

---

