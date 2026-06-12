---
title: "Citrix error 61"
date: 2008-02-11
forum: General Help
---

### Post by knowlesy on 2008-02-11
[[IMG]http://img125.imageshack.us/img125/5745/screenshotclienterrorty3.png[/IMG]](http://imageshack.us)


i get this error every time i try to connect to my uni's citrix server what to do ??? i have copied over (the error is GlobalSign ServerSign CA SSL 61)

ThawteServerCA.cer
ThawteRoot.crt

to the

/usr/lib/ICAClient/keystore/cacerts

but still no look

---

### Post by trmentry on 2008-02-28
I was having a the same error but for a 'Thawte SGC CA' cert it was looking for.  I kept beating my head on the desk trying to import that cert into Firefox.  

Finally found your post and saw your path to the cert store for ICA.  I moved my cert into there and restarted firefox and then everything worked. 

I know its not much help for you since you moved your certs in there already, but I did have to restart firefox.  Not sure if you've tried that.

---

