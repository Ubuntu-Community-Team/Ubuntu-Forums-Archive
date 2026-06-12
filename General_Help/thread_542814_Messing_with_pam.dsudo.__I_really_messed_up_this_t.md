---
title: "Messing with pam.d/sudo.  I really messed up this time!"
date: 2007-09-04
forum: General Help
---

### Post by palisaide on 2007-09-04
Alright, I think I've messed up big this time.  I'm running 7.04 Feisty. I was attempting to configure the Fingerprint Reader on my ThinkPad T60 to work with Gnome and ended up severely screwing myself.  I followed the instructions on [http://linux.org.mt/node/82#AEN153](http://linux.org.mt/node/82#AEN153) and everything seemed to be working just fine.  However, when editing my /etc/pam.d/sudo config file, I forgot to comment out some text, as you can see: ```

#%PAM-1.0

#@include common-auth
auth	required	pam_unix.so nullok_secure
@include common-account

If you like to use the fingerprint reader in the terminal too, you can use the following /etc/pam.d/sudo file instead:

#%PAM-1.0

#@include common-auth
auth    sufficient pam_unix.so nullok_secure
auth       required pam_bioapi.so {5550454b-2054-464d-2f45-535320425350} /etc/bioapi/pam/
password   required pam_bioapi.so {5550454b-2054-464d-2f45-535320425350} /etc/bioapi/pam/
@include common-account

```

Now, when I try to run sudo, after 2 failed PW attempts, I get the following message: sudo: pam_authenticate: Module is unknown.

Is there any possible way I can edit my /etc/pam.d/sudo file now?  Any time I try to run anything that requires root, I enter my password and it does not accept it.  I can still log in (whew!) but I can't run anything as root.  TIA!

---

### Post by Stebalien on 2007-09-04
start the computer in recovery mode (at the Grub boot menu).

---

