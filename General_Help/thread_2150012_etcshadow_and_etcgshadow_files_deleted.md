---
title: "/etc/shadow and /etc/gshadow files deleted"
date: 2013-05-30
forum: General Help
---

### Post by palaciosmiguelan on 2013-05-30
Hello ...,

Unadvertedly my files /etc/shadow and /etc/gshadow have been deleted. As a consequence of that I can not log in anymore.

Please, could someone expert list the steps I should follow to solve this problem or to get a "generic" /etc/shadow and /etc/gshadow in place?

Best regards,


Miguel

---

### Post by deadflowr on 2013-05-30
Reinstall.

From the shadow man page

>  shadow is a file which contains the password information for the       system's accounts and optional aging information.


       This file must not be readable by regular users if password security is
       to be maintained.



So it would be rather difficult to repopulate all the password information.

Or you could try booting a live cd or recovery session and move the backup file /etc/shadow~ into the /etc/shadow.
And /etc/gshadow~ into /etc/gshadow.

---

### Post by palaciosmiguelan on 2013-05-30
> **deadflowr said:**
> Reinstall.

From the shadow man page




So it would be rather difficult to repopulate all the password information.

Or you could try booting a live cd or recovery session and move the backup file /etc/shadow~ into the /etc/shadow.
And /etc/gshadow~ into /etc/gshadow.

The copies are also gone. I've read that in the recovery mode a console for the root can be launched by editing the kernel line but I do not succeed in doing it.

---

### Post by sisco311 on 2013-05-30
If you can boot a live CD/USB, then check out the content of the /var/backups directory on your root partition. If you are lucky, there are some recent copies of the shadow and group shadow files. If not, then you can try to chroot into Ubuntu from the live CD/USB and use pwconv and grpconv to create create the files. If you need more details please feel free to ask.

---

### Post by palaciosmiguelan on 2013-05-31
Hi ...,

Thank you very much for your replies. If I understand correcty I have three options with the live CD:
1. Create again the shadow and gshadow files, by copying them from the live CD, and assigning a username and password as before.
Is his possible? Are the shadow and gshadow files not encrypted?
2. Look at the /var/backups directory of the old Ubuntu system and look for a copy of the shadow and gshadow files.
3. Create the shadow and gshadow files with pwconv and grpconf.
This step is completely unknown to me. Could you provide more details?

Thank you very much in advance.


Miguel

---

