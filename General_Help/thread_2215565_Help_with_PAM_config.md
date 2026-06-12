---
title: "Help with PAM config"
date: 2014-04-07
forum: General Help
---

### Post by lawren-giam on 2014-04-07
Hi All,

I have recently installed a Ubuntu 12.04 LTS and successfully joined to an Active Directory. This server is use only for CUPS service which I have configured Samba, Winbind and CUPS. 
As I need to authenticate users using my CUPS server to print, I need to kerberize the system.

As another colleaguea and myself will need to ssh into this server to administer it, I would like advise on how I can configure the PAM module.

Right now, when I SSH into the server, I need to type in my password twice where the first one will fail. 
Using username "lawrence".
Using keyboard-interactive authentication.
Password:
Using keyboard-interactive authentication.
Wrong Password
Password:
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.11.0-15-generic x86_64)


This is my current pam.d config:
/etc/pam.d/common-auth
# here are the per-package modules (the "Primary" block)
auth    sufficient                      pam_winbind.so krb5_auth krb5_ccache_type=FILE
auth    [success=2 default=ignore]      pam_unix.so nullok_secure
auth    [success=1 default=ignore]      pam_lsass.so try_first_pass
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

I know that the pam.d part needs to fine tune but I do not know how to do it. I want to be able to login via SSH using my local unix account and be able to administer it with my unix account. The users in the Active Directory will not login via SSH, they will only be authenticated when they access the CUPS printing service. Can anyone advise me what I need to do on the PAM module?

Thanks & Regards.

---

