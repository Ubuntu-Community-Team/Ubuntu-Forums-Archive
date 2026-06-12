---
title: "Openvpn with Google Authenticator Cant make it work"
date: 2013-05-28
forum: General Help
---

### Post by TheProdigY20P on 2013-05-28
I am running into problem trying to get google authenticator to work with my openvpn installation.

I first installed openvpn and confirmed it work fine.

I then installed google authenticator and verified it works by setting it up for my ssh server.

I then followed these instruction [http://zcentric.com/2012/10/09/google-authenticator-with-openvpn-for-2-factor-auth/](http://zcentric.com/2012/10/09/google-authenticator-with-openvpn-for-2-factor-auth/) to config my openvpn server. Basically plugin in the /etc/openvpn/server.conf file and /etc/pam.d/openvpn with the line to pass the password forward after stripping the 6 digit authentication code.

I am running Ubuntu server 12.04 LTS fully updated.

I checked my /var/log/auth.log file and noticed this error

May 27 19:04:36 bb-vpn openvpn[996]: PAM unable to dlopen(pam_google_authenticator.so):lib/security/pam_google_authenticator.so: undefined symbol: pam_get_item
May 27 19:04:36 bb-vpn openvpn[996]: PAM adding faulty module: pam_google_authenticator.so

Reading about this error online i've found that it could be because it was not compiled with a spec. option. So i decided to try and compile it myself and got this error


root@bb-vpn:/home/benoit/google-authenticator/libpam# pam_google_authenticator.c:50:31: fatal error: security/pam_appl.h: No such file or directory


I dont know what else to do now.

Please help

Thanks

**Edit: **I found the answer to my own question.

1. I needed to compile it from source because the one from the repo is an old one.
2. To get it to compile I needed to install libpam0g-dev i found that solution by reading the comments at this address.

[https://code.google.com/p/google-authenticator/wiki/PamModuleInstructions](https://code.google.com/p/google-authenticator/wiki/PamModuleInstructions)

Thanks

---

