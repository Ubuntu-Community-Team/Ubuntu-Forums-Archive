---
title: "Why can't I sign the Ubuntu code of Conduct"
date: 2007-07-13
forum: General Help
---

### Post by uibesteven on 2007-07-13
I followed the instructions all the way, but the page goes this way:

Sign the Ubuntu code of Conduct
Sign a code of conduct

To sign the code of conduct:

   1.

      Download the file to your own computer and read it carefully to ensure you agree to it.
   2.

      If you want to, add extra spaces or blank lines between words in the file. (This helps protect against other people trying to forge your signature.)
   3.
      In a terminal, run the command:

          gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt 

      (or whatever filename you gave to the code). This will create a file with a name like UbuntuCodeOfConduct-1.0.1.txt.asc.
   4.

      Open that new file, and copy and paste its contents into this box. Then click “Continue”.

Please fix the problems below and try again.

[COLOR="Red"](7, 9, 'No public key')[/COLOR]

I don't know why I was labeled "NO PUBLIC KEY".

Does anyone know what the matter is? 

Thank you in advance!!!

---

### Post by linuxwizard on 2007-07-13
Do you have OpenPGP Key.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto?highlight=%28openpgp%29](https://help.ubuntu.com/community/GnuPrivacyGuardHowto?highlight=%28openpgp%29)

---

### Post by uibesteven on 2007-07-13
The problem has been solved. I signed the document with a different sub key.

---

