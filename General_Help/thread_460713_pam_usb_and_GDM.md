---
title: "pam_usb and GDM"
date: 2007-05-31
forum: General Help
---

### Post by logical_thought on 2007-05-31
Ok, I've been setting up and playing with pam_usb for the last day or two, and I'm unable to get it to log me in. I have it working with everything else (screensaver, sudo, etc..) , but when I try logging in with pam_usb I get these messages in auth.log:

May 31 23:13:06 ubuntu pam_usb[5050]: Authentication request for user "billy" (gdm) 
May 31 23:13:06 ubuntu pam_usb[5050]: Device "SWITCHBLADE" is connected (good). 
May 31 23:13:06 ubuntu pam_usb[5050]: Performing one time pad verification... 
May 31 23:13:06 ubuntu pam_usb[5050]: Mount failed 
May 31 23:13:06 ubuntu pam_usb[5050]: Access denied. 

, forcing me to use a password to login.

When setting pam_usb up I added this to /etc/pam.d/common

auth    sufficient      pam_usb.so allow_remote=1

Can anyone point me in the correct direction to fix this?

---

### Post by logical_thought on 2007-06-01
Solved my own problem. After looking at the debug information, I found it needed a command pmount. I installed that and it worked. :)

My only worry is the security of pmount, as I have never heard of that before.

---

