---
title: "How do you set up Samba..."
date: 2007-08-08
forum: General Help
---

### Post by tj71587 on 2007-08-08
How do you set up Samba to be able to map a network drive from another location.  I have my router set correctly to forward to that IP correctly to the point where i can vnc into it, but when I try to map a network drive it looks and is unable to find it.  I used this Samba guide to set it up....

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Is there anything I have to change in that .conf?  Is there even a way to get this done?

---

### Post by misconfiguration on 2007-08-08
After you have your file directory, permissions and samba running. You must have the samba front-end installed on your client machine and mount the samba share.

```
mkdir /media/shared_media
mount -t smbfs //<ip_or_hostname_of_smb_box>/shared_dir /media/shared_media
```

---

### Post by tj71587 on 2007-08-08
Thanks, but there is no way to map it from another xp computer outside of this network the same sort of way its mapped in house?

---

### Post by DagMan on 2007-08-08
You would have to have the appropriate ports forwarded to the linux box from the router.
ports 137 138 139 445 according to my firestarter's auto samba selection.

I've never tried to do it like you are btw, so can't garuntee that's a solution.

---

### Post by tj71587 on 2007-08-08
Thanks for the try, but that didnt seem to make a difference, anyone else have an idea?

---

### Post by tj71587 on 2007-08-09
Just to explain whats going on a little more, I am able to map the drive from computers on my network with the real ip address, as well as the local one, but when i try to do it from another network it cannot be found. "The network path \\ip\folder could not be found".

---

