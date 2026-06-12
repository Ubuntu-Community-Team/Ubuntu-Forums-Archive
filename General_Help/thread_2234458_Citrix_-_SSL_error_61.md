---
title: "Citrix - SSL error 61"
date: 2014-07-14
forum: General Help
---

### Post by Josh_and_Debs on 2014-07-14
I am using Ubuntu 12.04 and the latest version of Citrix Receiver downloaded with the .deb file from the Citrix website. Previously Citrix has been working fine but recently I received the following error notice "You have chosen not to trust "Go Daddy Secure Certificate Authority - G2", the issuer of the server's security certificate (SSL error 61)". 

I've tried downloading what I think are the right certificates from the Go Daddy repository [https://certs.godaddy.com/anonymous/repository.pki](https://certs.godaddy.com/anonymous/repository.pki) and installed them into /opt/Citrix/ICAClient/keystore/cacerts but no luck. I've looked all over the place for solutions and tried making symbolic links to this directory from the Mozilla CA directory as often suggested, but still no luck. 

The error message only appears when I use Chromium to access Citrix, but using Mozilla it just does nothing. 

Any thoughts?

---

### Post by billdozor on 2014-07-18
You should be able to fix the certificate issues by creating symbolic links to the firefox ca-certs for the citrix client:

```
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
```

---

### Post by Josh_and_Debs on 2014-07-29
This doesn't work unfortunately. Still get the same error. Is it possible there is a problem at the server end?

---

### Post by billdozor on 2014-08-06
Just to clarify....The current setup you have right now was working and then one day it stopped working?

Or is this a case of, a previous Citrix install with Ubuntu 12.04 worked and now a reproduced new install does not?

[Edit] If this helps, I have compiled the steps that I do every time to install the Citrix Receiver on Ubuntu 14.04/Xubuntu 14.04 64 bit...which works each time for me: [https://sites.google.com/site/bashinlinux/howtos/citrix-receiver](https://sites.google.com/site/bashinlinux/howtos/citrix-receiver)

---

### Post by Josh_and_Debs on 2014-08-18
Hi billdozor, 

That's right, it was working fine on 12.04 32 bit and now stopped working (still on 12.04). Unfortunately I tried out your suggested method but it didn't work at all and now when I try to install via the software center it tells me the dependencies are wrong. Is there any way I can undo the changes made through your script? My mistake I guess, I assumed stuff for 14.04 would work for 12.04 but that looks like it was a bad assumption.

---

### Post by Josh_and_Debs on 2014-08-26
Update: I've upgraded to Ubuntu 14.04 and can now install again. However, I still have the same certificates issue. I've tried editing the trust for the certificate in Firefox but still no luck.

---

