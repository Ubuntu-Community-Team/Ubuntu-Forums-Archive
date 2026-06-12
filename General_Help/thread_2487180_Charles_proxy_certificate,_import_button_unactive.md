---
title: "Charles proxy certificate, import button unactive"
date: 2023-05-26
forum: General Help
---

### Post by ne-dmtro on 2023-05-26
Hey, everyone. 

I'm new here and new to the Linux system. So, if I make any mistakes regarding the forum rules, please point them out to me.

I have encountered a problem with importing the Charles proxy certificate into the system. When trying to do it from the GUI, the 'Import' button is greyed out, and it displays the message 'Cannot import because there are no compatible importers'. I also tried manually placing the certificate and using 'update-ca-certificate', but it didn't work either.

Ubuntu 23.04

---

### Post by idmbe on 2023-05-27
That is location for certificates :
```
 /usr/local/share/ca-certificates
```

See if the certificate there already or put it there, then type:
```
sudo update-ca-certificates
```

---

### Post by TheFu on 2023-05-27
Not related to certs, but .... 

Someone new to Linux shouldn't be running Ubuntu 23.04, unless there was no other choice. It isn't an LTS release so you'll be doing 2 OS replacements over the next year.  However, if you install 22.04, then that comes with 3 or 5 yrs of standard support, so you'll plenty of use/life without being forced to replace the OS just to retain the ability to be patched.

If you don't have a really, really, good reason to run 23.04, best to fix that issue ASAP.

I have no  idea what a "Charles proxy cert" is.  I've only be a Unix/Linux admin for 25 yrs, so there is always more to learn.

---

### Post by ne-dmtro on 2023-05-28
Thank you, first of all

I had done this before. And did it again just now and I have the same result, some how there are new trusted certificate. But Charles proxy still gives me errors with SSL handshake, and webpages won't loading: "Your connection is not privat" NET::ERR_CERT_AUTHORITY_INVALID


> Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
Processing triggers for ca-certificates-java (20230103ubuntu1) ...
done.
Updating Mono key store
Mono Certificate Store Sync - version 6.8.0.105
Populate Mono certificate store from a concatenated list of certificates.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed.

Importing into legacy system store:
I already trust 141, your new list has 137
1 previously trusted certificates were removed.
Certificate removed: CN="Charles Proxy CA (26 May 2023, latitudell3570)", OU=https://charlesproxy.com/ssl, O=XK72 Ltd, L=Auckland, S=Auckland, C=NZ
Import process completed.

Importing into BTLS system store:
I already trust 137, your new list has 137
Certificate added: C=ES, CN=Autoridad de Certificacion Firmaprofesional CIF A62634068
1 new root certificates were added to your trust store.
1 previously trusted certificates were removed.
Certificate removed: CN="Charles Proxy CA (26 May 2023, latitudell3570)", OU=https://charlesproxy.com/ssl, O=XK72 Ltd, L=Auckland, S=Auckland, C=NZ
Import process completed.
Done
done.



---

### Post by ne-dmtro on 2023-05-28
It's been over a year since I started using Linux on a daily basis, and I still feel like a noob, no diggity. And what about before, I was doing exactly as you said, sticking with LTS release. Decided to try this time to update to 23.04 right away it was released. It's interesting to try something new, specially to Gnome updates, I wish they both don't have such dependency with releases. 

And Charles proxy is just a traffic sniffer program, just like Wireshark. To catch some encrypted traffic you to install a certificate. And I don't understand why I can't, start to thinking that I will go to reinstall Ubuntu soon.

---

