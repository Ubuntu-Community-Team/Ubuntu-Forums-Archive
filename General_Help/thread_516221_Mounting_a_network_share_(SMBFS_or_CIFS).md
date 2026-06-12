---
title: "Mounting a network share (SMBFS or CIFS)"
date: 2007-08-02
forum: General Help
---

### Post by tienhn on 2007-08-02
Hi All,
I have googled all day for a tip that would allow a user to mount a Windows share using cifs or smbfs onto the user's own mount point.
So:

sudo mount -t cifs //IP//Share ~/mount_point -o username=user_name

would work. But how do I allow the aobve command without "sudo"? A none root user should be able to mount a drive to his/her mount moint right? Why must it be "sudo"?

Any help pointing to the right way to do this would be greatly appreciate.

Thanks,
Tien,

---

### Post by veloce on 2007-08-04
> **tienhn said:**
> 
A none root user should be able to mount a drive to his/her mount moint right? 


No, sorry.  mounting and unmounting is a root activity.

Best avenue is to mount at startup using fstab or rc.local.  if you want the mount to be under the users home drive you might need to use a command in rc.local so you can refer to the home directory with the ~ (though I've never tried that).

Alternatively, users can access samba shares using "places - connect to server"  without mounting, do they need to have the directory mounted?

---

