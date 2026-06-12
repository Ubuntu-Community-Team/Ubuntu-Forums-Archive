---
title: "??  pam.d     common-password    arguments ??"
date: 2014-09-18
forum: General Help
---

### Post by Gobugs on 2014-09-18
Howdy

With a fresh install of TT,  with two users.  I want to require the non-SysAdmin to use a password that ::

has min length of 10
is NOT any of the last four passwords
contain at least 4 types of characters      A a * 3

I understand this can be accomplished within pam.d/common-password  configuration.  Here is what I tried first ::

password    [success=1 default=ignore]    pam_unix.so min=10 max=12 number=4 difok=4 sha512
password    requisite            pam_deny.so
password    required            pam_permit.so
password    optional    pam_gnome_keyring.so 

Using SysAdmin,   I expired the password with sudo chage -d 0 userA
Login with userA, it was forced to change password,  and it accepted   abc123     but that fails the test.

Re-reading man pam_unix   I tried different arguments as shown below ::

password    [success=1 default=ignore]    pam_unix.so minlen=10 remember=4 difok=4 sha512
password    requisite            pam_deny.so
password    required            pam_permit.so
password    optional    pam_gnome_keyring.so 

Again expiring the password with sudo chage -d 0 userA
Login with userA, it was forced to change password,  and it accepted   xcv567      and that fails the test too.

Well heck!    ?? Is pam.d/common-password   the place to make this happen ??
                       ??  are any of the above arguments accurate for what I want to do ??
Any suggestions on where I can learn how to do this.

Thanks

---

