---
title: "Two password required for sudo"
date: 2008-07-07
forum: General Help
---

### Post by officeitplus on 2008-07-07
When I run sudo I get asked for two passwords; one by pam_mount, the other sudo. i.e.

[COLOR="Green"] 
tony@humphrey: sudo
pam_mount password:
[sudo] password for tony: 
tony@humphrey:[/COLOR]

I suspect that this is a result of me setting the system to be part of my SME Server (NT) domain.  I changed the following files:

[COLOR="Green"]/etc/samba/smb.conf
/etc/nsswitch.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-session
/etc/pam.d/sudo[/COLOR]

The change to the sudo file was to add the following lines:

[COLOR="Green"]auth sufficient pam_winbind.so
auth required pam_unix.so use_first_pass[/COLOR]

The resulting change to the system also affects the Synaptic package manager which opens, asks for a password and then disappears.

TIA,

Tony

---

### Post by officeitplus on 2008-07-08
Is there a better place to ask this question?

Tony

---

