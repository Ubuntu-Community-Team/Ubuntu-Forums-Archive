---
title: "Users Privileges for good Desktop Experience."
date: 2015-02-23
forum: General Help
---

### Post by Fedor_Syagin on 2015-02-23
Greetings.
I am trying to setup Ubuntu 14.04 with Likewise (Pbis-Open at this point.) and libpam_mount that will provide user with as streamline experience as possible.
I do not want all users (or specific users if I have to particular user on workstation to specific local groups) to have full sudo  ( ALL=(ALL) ALL). 

So far I achieved following goals.
1.) Domain authentication.
2.) Auto mounting of cifs partitions for users.
3.) Controlling sudoers files based on active directory group membership. (Give all users ability to do package installation with apt-get and dpkg for example.)

I would also like for each user to be able to
1.) Do installations using software center.
2.) Be able to automount external usb drives.
3.) Be able to add printers 

What groups should I add desktop users in to have a smooth of desktop experience as possible without giving them full root access? 
Any particular setup recomendation? (Adding to plugdev and lpadmin group? etc.)
Would really appreciate advice on this.
Thank you.

---

