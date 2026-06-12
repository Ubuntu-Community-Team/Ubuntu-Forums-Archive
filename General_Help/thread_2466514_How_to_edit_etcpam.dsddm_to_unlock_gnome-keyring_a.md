---
title: "How to edit /etc/pam.d/sddm to unlock gnome-keyring at login"
date: 2021-08-29
forum: General Help
---

### Post by aliquo93 on 2021-08-29
Hi, I have Mailspring on Kubuntu 21.04, but every time I open it a popup appears asking the keyring password. After some research I found that the issue is that SDDM doesn't automatically unlock gnome-keyring at login (even with auto-login disabled), but it can be fixed by editing "/etc/pam.d/sddm" configuration file. I also know that editing that file wrongly can lock you out of your system, so I want to do it after being sure of what I am doing. This is the content of my sddm configuration file:


```
#%PAM-1.0


# Block login if they are globally disabled
auth    requisite       pam_nologin.so
auth    required        pam_succeed_if.so user != root quiet_success


# auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
# gnome_keyring breaks QProcess
-auth   optional        pam_gnome_keyring.so
-auth   optional        pam_kwallet5.so


@include common-account


# SELinux needs to be the first session rule.  This ensures that any
# lingering context has been cleared.  Without this it is possible that a
# module could execute code in the wrong domain.
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
# Create a new session keyring.
session optional        pam_keyinit.so force revoke
session required        pam_limits.so
session required        pam_loginuid.so
@include common-session
# SELinux needs to intervene at login time to ensure that the process starts
# in the proper default security context.  Only sessions which are intended
# to run in the user's context should be run after this.
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
-session optional       pam_gnome_keyring.so auto_start
-session optional       pam_kwallet5.so auto_start


@include common-password


# From the pam_env man page
# Since setting of PAM environment variables can have side effects to other modules, this module should be the last one on the stack.


# Load environment from /etc/environment
session required        pam_env.so


# Load environment from /etc/default/locale and ~/.pam_environment
session required        pam_env.so envfile=/etc/default/locale user_readenv=1
```


I see that gnome-keyring is already mentioned in 2 lines:  


```
-auth   optional        pam_gnome_keyring.so 
``` 


and 


```
-session optional       pam_gnome_keyring.so auto_start
```


How can I edit it to make it unlock gnome-keyring at login? I just have to remove the "-" before those 2 lines or there is something else I have to do? Thanks in advance!

---

### Post by HermanAB on 2021-08-30
Err… PAM is a very sensitive girl. The first thing to do is to make a backup of your data. I have learned to leave PAM alone…

---

