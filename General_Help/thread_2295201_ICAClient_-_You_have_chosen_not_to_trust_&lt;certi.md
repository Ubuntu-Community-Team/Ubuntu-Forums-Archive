---
title: "ICAClient - You have chosen not to trust &lt;certificate&gt;"
date: 2015-09-16
forum: General Help
---

### Post by swatto on 2015-09-16
Hello,

I have installed the Citrix client on my Ubuntu 15.04 machine so that I can use resources on a Netscaler Gateway appliance, I am getting the following certificate error though:

**'You have not chosen to trust "COMODO RSA Organization Validation Secure Server CA", the issuer of the server's security certificate (SSL error 61).'**

I am using the Chrome browser and have followed the instructions on this page:

[https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")

I have fixed the issue on my Windows machine by simply installing the following certificate into the 'Trusted Root Authorities' store:

[https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/968/108/intermediate-ca-2-comodo-rsa-organization-validation-secure-server-ca-sha-2]("https://support.comodo.com/index.php?/Default/Knowledgebase/Article/View/968/108/intermediate-ca-2-comodo-rsa-organization-validation-secure-server-ca-sha-2")

For some reason I cannot get it to work on Ubuntu - I have tried importing it into the keystore and following various instructions about adding additional certificates but it is still not working.

Please could someone help me with this.

---

### Post by swatto on 2015-09-17
Can anyone help with this please? :-(

---

