---
title: "KVpnc setup questions"
date: 2006-07-03
forum: General Help
---

### Post by Enigmatic on 2006-07-03
I've got Ipcop running OpenVPN in order to give me VPN support. I can connect to it from Windows, but I'm having some difficulty setting it up in Linux.

I'm trying Kvpnc as I think it's probably the easiest to setup, but please correct me if I'm wrong. I first went to Profile/Import Cert. I assumed that the p12 file Ipcop was outputting was a racoon file, so I pointed it to it and gave it the pwd and it imported it successfully. 

Then I created a new profile, set it to OpenVPN type and pointed it to my Dyn DNS address, and changed the auth to certificate based (X509).

Then I browsed to /etc/racoon (where it said it had imported the cert) but it had two certs in there. There were ca_Travel.pem and mykeys_Travel.pem. I selected the first one. Hit okay and it accepted all the settings.

So I hit connect, and it just closed on me. I restarted the program, and it tells me it can't find the private key file. So I edit the profile and point it to the mykeys_Travel.pem file and enter in the same password as for the other cert. 

Try connecting again, and no, it's now missing the CA file! So I point that setting in the profile to ca_Travel.pem.

Finally, it doesn't give me an error about the certs, but that the module 'tun' could not be found. I'm not sure how to solve this, I looked in the package manager and couldn't find anything by that exact name.

---

### Post by switchtower on 2006-08-09
Enigmatic,

Have you found a solution for this problem? I'm trying to do the same thing with the same setup, but no luck.

Thanks,

Nick

---

### Post by Enigmatic on 2006-08-09
Actually not, I ended up just using an HTTP proxy over SSH.

---

