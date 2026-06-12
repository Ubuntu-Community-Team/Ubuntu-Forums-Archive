---
title: "laptop authentication with kerberos/local offline ?"
date: 2007-10-31
forum: General Help
---

### Post by jlawren1 on 2007-10-31
here is the situation...

I have my work laptop setup to authenticate against AD with Kerberos as so...

common-auth

 auth    required        pam_env.so
 auth    sufficient      pam_krb5.so
 auth    sufficient      pam_unix.so nullok_secure 
 auth    required        pam_deny.so

Root authentication to AD is bypassed in the /etc/krb5.conf file with:

 [appdefaults]
       pam = {
               minimum_uid = 1000
               debug = false
       }

Since I will be the only one logging on the laptop, I just have a local account in /etc/passwd that has the password locked (kerberos authenticates me).  This has the benefit of AD authentication using only the smbclient and kerberos client packages.   What would be the best way to do off-line authentication?  I've looked at pam_ccreds, but if your going to have a stored encrypted password, why not just sync your local account with your AD credentials?

The only problem I would see with having a synced local account would be if you changed your AD password on another machine....

  thoughts ? concerns ?

---

