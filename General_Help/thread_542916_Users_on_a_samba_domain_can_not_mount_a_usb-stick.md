---
title: "Users on a samba domain can not mount a usb-stick"
date: 2007-09-04
forum: General Help
---

### Post by pfigueira on 2007-09-04
Hi,
I manage a large school equipment (+-1250 users) and I had to configure a mix envoirement (linux a window$ clients). 
I configured a linux distro (sme server) with samba+winbind (h**p://tech.canterburyschool.org/tech/UbuntuWorkstations)
The domain users, on the ubuntu workstations, can not mount the usb-sticks. Can anyone help me?

Thanks,
Paulo F.

---

### Post by steever on 2007-11-03
Logins validated by the Windows server won't correctly pickup membership in local groups, making sound, USB devices, etc. inaccessible. To fix that do the following:
   1.

      edit /etc/pam.d/gdm to include

            auth optional pam_group.so
                    

   2.

      edit /etc/security/group.conf to include

            gdm;*;*;Al0000-2400;floppy,audio,cdrom,video,plugdev,scanner
                   

Explanation:

    *

      No.1 instructs gdm to use the /etc/security/group.conf
    *

      No.2 assigns membership of the floppy, audio, cdrom, video, plugdev (usb sticks) and scanner groups to any user who logs in through the gdm.

---

