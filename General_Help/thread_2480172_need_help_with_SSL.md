---
title: "need help with SSL"
date: 2022-10-21
forum: General Help
---

### Post by npereira on 2022-10-21
hi,

I have setup a ubuntu CA server and created a CA root (server is pki.nelsonlab.local) which i loaded in the trusted root certificate of my windows 10 station

I also created and signed a csr for a web server with subject alternative as web1.nelsonlab.local


I added the instructions for the apache default virtual host as:
    SSLEngine on
    SSLCertificateKeyFile /etc/ssl/web1.nelsonlab.local.key
    SSLCertificateFile /etc/ssl/web1.nelsonlab.local.crt
 
then restarted the web server

When going to the web page [https://web1.nelsonlab.local](https://web1.nelsonlab.local) i am still getting a certificate error and dont understand why this is happening.

everything to me looks fine i just don't understand why it's still giving me cert error.

Can anyone explain why this is?

---

### Post by ActionParsnip on 2022-10-21
Does the cert also contain the root? you need both the cert from the authority and the root ca in the same file, then the key file as you expect. Make sure you also distribute your root CA cert to the "Trusted Root Authority"  folder in the client system so that it trusts the chain

---

### Post by npereira on 2022-10-21
hmmm, not sure what you mean by that, but this is the command i did on the CA server :



openssl x509 -req -in web1.nelsonlab.local.csr -CA ca.cert.pem -CAkey ca.key -CAcreateserial -out web1.nelsonlab.local.crt -days 825 -sha256 -extfile web1.nelsonlab.local.ext

---

### Post by &amp;KyT$0P# on 2022-10-21
> **npereira said:**
> created a CA root (server is pki.nelsonlab.local) which i loaded in the trusted root certificate of my windows 10 station

What web browser are you using?  Some browsers, such as Firefox or Chrome, use their own certificate stores independent of the OS store, so you would need to import your CA root certificate as an authority in your browser's settings.

---

### Post by ActionParsnip on 2022-10-21
What OS is the client system?

---

### Post by npereira on 2022-10-21
im using edge and the root ca is there see attached

---

### Post by npereira on 2022-10-21
Windows 10 as mentioned in the original post

---

### Post by ActionParsnip on 2022-10-21
OK and does the cert file on y website have the root in it as well as the certificate from the CA?

---

### Post by npereira on 2022-10-21
here is the webserver cert

---

### Post by npereira on 2022-10-21
hmmm... I rebooted the station and now it's working....

---

### Post by ActionParsnip on 2022-10-21
Cool. Yeah all looks OK. You made the chain in both places. In large setups you have intermediate servers you rise certs from and they are certified by the root. You keep the root CA powered off for security. Glad you got the gold

---

