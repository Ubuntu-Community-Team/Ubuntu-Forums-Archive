---
title: "Best Way To Update VirtualBox To A New Version"
date: 2016-05-19
forum: General Help
---

### Post by walterdowis on 2016-05-19
When I opened VirtualBox, a message came up that there is an updated version. I downloaded the .deb file of the update version. 
What is the best way to update VirtualBox with the new .deb file?  Should I first uninstall/remove VirtualBox and install fresh? Or can I just run the .deb file and it will do everything that's needed?
If I need to remove VirtualBox first, how do I remove all of it cleanly from my computer?

---

### Post by QIII on 2016-05-20
Hello!

The answer is going to depend on how you initially installed VBox.

Could you tell us how you did that?

Cheers!

---

### Post by walterdowis on 2016-05-20
sudo apt-get install virtualbox.

---

### Post by SeijiSensei on 2016-05-20
The best method is to add the Oracle repository to your system and install/update VB from there.  For details see: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  Then all updates will be managed the same way the rest of your system is, and you will get new versions as soon as they are released.

---

