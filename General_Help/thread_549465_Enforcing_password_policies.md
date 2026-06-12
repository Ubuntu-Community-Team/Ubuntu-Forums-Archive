---
title: "Enforcing password policies"
date: 2007-09-12
forum: General Help
---

### Post by cbozic on 2007-09-12
I am looking for some help on how to configure Ubuntu 7.04 to enforce a corporate password policy at my work.  I have read some posts here and elsewhere on the net and most sources tell me to use the pam crack library.   I have edited /etc/pam.d/common-password to use this and also installed the corresponding packages from apt-get but I cannot seem to get the Ubuntu New User GUI tool (or even the passwd command) to behave as I have configured.  I am trying to start simple by having pam enforce an 8 character minimum then I'd like to add more rules like "must include at least one number, uppercase letter, and lowercase letter" once that's working.  Can anyone point me in the right direction?

Below is my simple edit to common-password:
```

#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.

#password   required   pam_unix.so nullok obscure min=4 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
password required         pam_cracklib.so retry=3 minlen=8 difok=3
password required         pam_unix.so use_authtok nullok md5


```

Thanks!

Chris Bozic

---

