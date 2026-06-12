---
title: "Samba completely broken in Kubuntu Feisty"
date: 2007-05-29
forum: General Help
---

### Post by AmazingLarry on 2007-05-29
I've installed samba with apt-get.  There is no /etc/samba/smbpasswd file.  So I try to run smbpasswd -a followed by the username.  It takes my password, but doesn't make a smbpasswd file.

So I do:
cat /etc/passwd > mksmbpasswd /etc/samba/smbpasswd

It makes file with no passwords in it that looks like this:
#
# SMB password file.
#
halt:7:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:halt
operator:11:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:operator
shutdown:6:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:shutdown
sync:5:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:sync
bin:1:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:[U          ]:LCT-00000000:bin

-------ETC----

No passwords are stored in the file.  All users have the XXXX:XXXX instead of a password.  I can still run smbpasswd, but it doesn't make changes to the smbpasswd file.  Basically it looks like smbpasswd command cannot make changes to the smbpasswd file.

---

### Post by kuja on 2007-05-29
I've had issues with Feisty's samba also. The route I've taken is to install Edgy's samba packages, which works just fine I might add.

---

### Post by der_joachim on 2007-05-29
+1 :(

---

### Post by AmazingLarry on 2007-05-29
> **kuja said:**
> I've had issues with Feisty's samba also. The route I've taken is to install Edgy's samba packages, which works just fine I might add.

That sounds the opposite of promising.  I might have to "fix" this Kubuntu install with Fedora if the repositories are full of non-functional software.

---

### Post by der_joachim on 2007-05-30
I may have found a workaround: [launchpad bug & workaround here]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460").

---

### Post by Randy5150 on 2008-01-30
Just verified in Kubuntu Gutsy 7.10 that this is still broken.

copied from mrvanes:

The samba share gets broken after the 'advanced' interface in konqueror's directory sharing properties has been used, and the reason is it adds:
 case sensitive = no
 strict locking = no
 msdfs proxy = no
 and a slash to the end of the path of the share.

It turns out the "msdfs proxy = no" is the culprit. When removed, the sharing is flawless again.

---

