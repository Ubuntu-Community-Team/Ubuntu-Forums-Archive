---
title: "How to install digital certificate in browser?"
date: 2015-01-08
forum: General Help
---

### Post by rdh61 on 2015-01-08
Hi,

I'm running Lubuntu 14.04 LTS. I am trying to access a government website (the tax office... aaargh!) for which I have a digital certificate. This certificate has already been installed successfully on this computer, but I have since upgraded from Lubuntu 13.10 with a clean install, and I need to install it again. I am not having any success in doing so either in chromium or chrome or firefox. I have two files, one with .cer and one with a .crt extension.

In chromium/chrome I go to settings -> advance settings -> HTTPS/SSL Manage Certificates -> Your Certificates tab -> Import. A window opens asking me to select a "PKCS Nº 12" file. No files are visible. If I change it to "All files" I see my certificates. If I select either one and click "Open", I am told: *"PKCS Nº12 Import Error - Invalid or corrupt file".* Not surprising as my certyificate isn't PKCS Nº12! So how do I import a .cer / .crt certificate?

In firefox I go to Preferences -> Advanced -> Certificates -> View Certificates -> Your Certificates -> Import. A window opens and I select "Certificate files" then my .cer or .crt file. I click "Open". I am told: *"This personal certificate can't be installed because you do not own the corresponding private key which was created when the certificate was requested."* I have read that a "private key" is an encryption key with a .key extension. I cannot remember ever having had one of these. If I did I would have saved it and backed it up with the other files. 

I also remember that the original installation of the certificate a year ago was straightforward. The certificate has not expired.

Any suggestions?

Many thanks.

---

### Post by bashiergui on 2015-01-08
The second answer down in this thread has detailed instructions,
[http://superuser.com/questions/437330/how-do-you-add-a-certificate-authority-ca-to-ubuntu](http://superuser.com/questions/437330/how-do-you-add-a-certificate-authority-ca-to-ubuntu)

Once you place the .crt in /usr/local/share/ca-certificate then you import it into browsers, as per the links in that same thread.

---

### Post by rdh61 on 2015-01-09
Thanks for your answer. I am still confused. I placed the .crt in /usr/local/share/ca-certificate, and ran sudo update-ca-certificates, as instructed in the answer you linked to. The output was:

```
robert@robert-P4i65GV:~$ sudo update-ca-certificates
[sudo] password for robert: 
Updating certificates in /etc/ssl/certs... unable to load certificate
3074283196:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:703:Expecting: TRUSTED CERTIFICATE
unable to load certificate
3074266812:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:703:Expecting: TRUSTED CERTIFICATE
WARNING: Skipping duplicate certificate AC_Raíz_FNMT-RCM.pem
1 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
robert@robert-P4i65GV:~$ 
```

Does this indicate an error or success?

In any case I then tried to import the certificate in the browsers, both as I had done before (same result), and as indicated in the links in the thread (although the link for Chrome was for the Windows version). I find the certificate can be imported under "Servers" or "Authorities" but not under "Personal". However, in neither case can I access the restricted area of the website that they should allow.

I also have a Windows system, and there I see that the certificate is imported in Chrome (under "Servers"). It works. But I don't want to have to rely on Windows (and really, one shouldn't have to) for these things!

I have dug out the documentation with instructions that I have from the authority that issued the certificate, and in no place do they mention a "private key". Other than that, it is not very helpful, saying in essence "Import your certificate into your browser". If only it were that simple!

Can you help further?

Many thanks.

---

### Post by bashiergui on 2015-01-09
Beyond that I can't really help. Contact the government office help desk if no one else answers. It's possible they require a certain OS or browser version. The last government site I visited required IE 6 :-/

---

### Post by rdh61 on 2015-01-10
OK, thanks for your help.

---

### Post by rdh61 on 2015-01-10
> **bashiergui said:**
> It's possible they require a certain OS or browser version.

That may be right. 

In Windows XP I can open and view the contents of the  .crt file as well as the .cer file. In Lubuntu I can open and view the  .cer file but not the .crt file. The latter appears as a blank icon, and when I  try to open it I am asked which application should be used. I notice .crt file has been converted to .pem and added to my /etc/ssl/certs folder. The icon again is blank and I cannot open and view it. The other .pem files in this directory have an icon with a cogwheel and can all be opened and viewed. 

I do not know why my certificate should be readable in Windows  but not in Ubuntu.

---

