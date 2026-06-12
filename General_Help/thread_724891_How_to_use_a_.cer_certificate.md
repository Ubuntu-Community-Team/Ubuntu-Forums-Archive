---
title: "How to use a .cer certificate?"
date: 2008-03-15
forum: General Help
---

### Post by XeiaieX on 2008-03-15
Hello friends.

I need to use a .cer certificate to log into a UI for work. (https webpage)

i must be able to do this in order to completely rid my hard drive of that garbage M$ calls an OS.

Thanks in advance for your time and help!

---

### Post by XeiaieX on 2008-03-18
Anyone? :)

---

### Post by XeiaieX on 2008-03-19
i can't believe i havent gotten any replies in the proper (security) forum!

someone *has* to know how!

---

### Post by danwood76 on 2008-03-19
Dont the web servers host the .cer files as certificates of being certifiedly secure?

What exactly is the issue?

---

### Post by XeiaieX on 2008-03-22
> **danwood76 said:**
> Dont the web servers host the .cer files as certificates of being certifiedly secure?

What exactly is the issue?

No, basically what it is, is i have to log into a secure site for work.

In order for the site to even consider allowing me to TRY to log in, i must first certify that I am ok to try to log in you see... and thats where the .cer comes in.

in windows, i just run the .cer file and it opens an import wizard. but in linux i cannot even run the .cer.

thanks for the help and sorry for the delay! been super busy lately.

thanks a lot for the help.

---

### Post by danwood76 on 2008-03-25
I just had a quick search and found this:
[http://kb.mozillazine.org/Installing_an_SMIME_certificate](http://kb.mozillazine.org/Installing_an_SMIME_certificate)

It looks like you need to import the .cer file into the authorities tab in the certificate management section in the firefox preferences.

---

### Post by 77n3077 on 2008-04-08
Hi i had the same issue when trying to connect to a citrix server with a privately created key/certificate the message i got was "you have not chosen to trust "<servername>", the issuer of the server's security certificate." so i just renamed it to .crt instead of .cer and placed it in the /usr/lib/ICAClient/keystore/cacerts which isnt relevant to the original question but perhaps you could rename it and import it into you browser.

:idea:

---

