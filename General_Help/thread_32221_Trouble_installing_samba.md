---
title: "Trouble installing samba"
date: 2005-05-06
forum: General Help
---

### Post by young on 2005-05-06
Hi there,

     I am having some trouble installing samba on my ubuntu.  During the
   installation procedure, I get the following error messages:


        Preconfiguring packages.....
        (Reading database ... 644468 files and directories currently installed.)
        Preparing to replace samba-common 3.0.7- lubuntu6.3 (using
         .../samba-common_3.0.7-lubuntu6.3_i386.deb) ...
        Unpacking replacement samba-common ...
        Selecting previously deselected package samba-doc.
        Unpacking samba-doc (from .../samba-doc_3.0.7-lubuntu6.3_all.deb) ...
        Setting up samba-common (3.0.7-lubuntu6.3) ...

        Setting up samba-doc (3.0.7-lubuntu6.3) ...
        Setting up samba (3.0.7-lubuntu6.3) ...
        update-rc.d: warning: /etc/rc2.d/K09samba is not a link to  ../init.d/samba
        update-rc.d: warning: /etc/rc3.d/K09samba is not a link to  ../init.d/samba
        invoke-rc.d: danglin symlink : /etc/rc2.d/K09samba
        dpkg: error processing samba (--configure):
             subprocess post-installation script returned error exit status 102
------------------------------------------------------------------------------------------------------------------------------
  Can somebody please tell me what went wrong, and how I could fix this problem?
  Your suggestions ideas will be much appreciated.  Thank you.


                                                                                                             Young

---

### Post by markw on 2005-05-06
Next time please try searching the Forums and Google before asking. 



I found this in about 5 seconds with a simple Google search. It may fix you problem.
[http://ubuntuforums.org/archive/index.php/t-6318.html](http://ubuntuforums.org/archive/index.php/t-6318.html) (5 posts from the top)

---

### Post by Ingwar on 2006-05-22
Markw, thanks a lot for the link it helped me to fix it after reading this thread.

---

