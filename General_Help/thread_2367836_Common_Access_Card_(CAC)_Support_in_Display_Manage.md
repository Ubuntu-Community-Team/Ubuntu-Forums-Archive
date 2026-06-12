---
title: "Common Access Card (CAC) Support in Display Manager"
date: 2017-08-03
forum: General Help
---

### Post by squinky86 on 2017-08-03
Note: I'm using the Artful development branch so that I could use opensc 0.17. I'm also using coolkey.

I've set up smart card authentication on my machine following [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard). Everything seems to work great from the command line: I type in my username, and I am greeted with a welcome message identifying my certificate subject with a prompt for my pin.

The problem comes when I try to use lightdm or sddm. I have added the "auth sufficient pam_pkcs11.so" line to /etc/pam.d/sddm and /etc/pam.d/lightdm, but both display managers hang at asking for my account's password. I have tried entering my pin, my user's password, and leaving the password blank hoping that I get prompted in some way for a pin, but I never receive a prompt.

Does anyone know what I need to do to get my smart card working from the login prompt?

---

### Post by squinky86 on 2017-08-04
Switched to the gdm3 package, and everything just works.

---

