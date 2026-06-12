---
title: "How to add to sources.list"
date: 2007-05-31
forum: General Help
---

### Post by dinochopins on 2007-05-31
Hi,

I've just downloaded a number of ubuntu's .deb packages for PLESK ([http://www.swsoft.com/en/products/plesk](http://www.swsoft.com/en/products/plesk)). The packages is organized like below :

--------------------------------------------------------------------------------------------------------------
/dist-deb-Ubuntu-6.06-i386
  +--- /base
--------- libpam-plesk_8.1.1-ubuntu6.06.build81070322.17_i386.deb
         --------- psa_8.1.1-ubuntu6.06.build81070322.17_i386.deb
--------- psa-api_8.1.1-ubuntu6.06.build81070404.14_i386.deb
--------- psa-courier-imap_3.0.8-ubuntu6.06.build81070322.17_i386.deb
--------- and so on ...
  +--- /opt
         +------------- /api 
                  -------------- psa-api-rpc_8.1.1-ubuntu6.06.build81070404.14_i386.deb
         +---- /backup
                  -------------- psa-backup-manager_8.1.1-ubuntu6.06.build81070404.14_i386.deb
-------------- psa-ftputil_8.1.1-ubuntu6.06.build81070322.17_all.deb
                   +------------- /coldfusion
                  -------------- psa-coldfusion-support_8.1.1-ubuntu6.06.build81070322.17_i386.deb
                   +------------- /docs
                  -------------- psa-manual-custom-skin-guide_8.1.1-ubuntu6.06.build81070322.17_i386.deb
                   +------------- /drweb
                  -------------- drweb-base_4.33-5psa_i386.deb
                  -------------- drweb-daemon_4.33-5psa_i386.deb
                  -------------- drweb-qmail_4.33-ubuntu6.06.build81070322.17_i386.deb
                  -------------- drweb-updater_4.33-4psa_i386.deb
         +---- and so on...

--------------------------------------------------------------------------------------------------------------

My question is, how can I parse all the packages and added it to my sources.list ? Since I need to run PLESK autoinstaller and that installer search the sources.list packages ?

Any help will be greatly appreciated.

Thanks,

Feris

---

### Post by cisforcojo on 2007-05-31
I might not understand your question but do you want to add .deb files to your sources.list?

If so, sources.list is only a file that controls which repositories you install from.

---

