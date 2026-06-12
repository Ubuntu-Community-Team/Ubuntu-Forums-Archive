---
title: "Need help get pam_tally2 to onlu lock outlocall accounts and not LDAP accounts."
date: 2015-05-20
forum: General Help
---

### Post by breezely on 2015-05-20
Here are my Pam settings. I tried to use a doc I found on Redhat that was talked about the auth pam modules but I'm still having issues to get this to work right on Ubuntu 14.04 with the configuration below. Local accounts are not getting failed login in tallylog fille and LDAP users are. I need it the other way around UGH... Hopefully some can point out what I'm doing wrong.

Thank you,
Fab

auth    required      pam_env.so
auth    [success=3 default=ignore]  pam_localuser.so
auth    [success=ignore default=die]    pam_succeed_if.so uid >= 10000 quiet_success
auth    [success=4 default=ignore]      pam_krb5.so minimum_uid=10000
auth    [success=done new_authtok_reqd=done default=die]    pam_sss.so

auth    required    pam_unix.so nullok_secure 
auth    sufficient  pam_tally2.so onerr=fail deny=5 unlock_time=900 magic_root

auth    required                        pam_deny.so
auth    required                        pam_permit.so
auth    optional                        pam_cap.so 



password        requisite                       pam_pwquality.so retry=3
password        [success=3 default=ignore]      pam_krb5.so minimum_uid=10000 try_first_pass use_authtok
password        [success=2 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512 remember=10
password        sufficient                      pam_sss.so use_authtok
password        requisite                       pam_deny.so
password        required                        pam_permit.so
account required                        pam_tally2.so

session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session optional                        pam_umask.so
session optional                        pam_krb5.so minimum_uid=1000
session required        pam_unix.so 
session    required    pam_mkhomedir.so skel=/etc/skel/ umask=0022
session optional                        pam_sss.so 
session optional        pam_systemd.so

---

