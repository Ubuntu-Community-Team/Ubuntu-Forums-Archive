---
title: "wu-ftpd and pam_time.so"
date: 2005-04-21
forum: General Help
---

### Post by asterix71 on 2005-04-21
hi all,
my boss asked me for an ftp server and since i was triyng ubuntu 4.10 i've managed to install wu-ftpd (with synaptic), then proceeded with configuration ...all fine the server is working very well.
Yesterday the boss asked me to add a new ftp user but this one should have limited time access ...i mean this user shuld be granted access only between 8,00 am to 11,00.
I was thinking to use pam_time.so to limit this specific user (and maybe other ones...) but if i add the line "account required pam_time.so" in my wu-ftpd pam config file noone can login (at any time) to the ftp server also with a correct (i suppose) time.conf file.

anyone experiencing the same problem?



here are the configuration files:

--------------------------/etc/pam.d/wu-ftpd----------------------------------------
#%PAM-1.0
auth    required pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
auth    required pam_unix.so
auth    required pam_shells.so
account required pam_unix.so
account required pam_time.so
session required pam_unix.so
-------------------------------------------------------------------------------------------

-----------------------/etc/security/time.conf----------------------------------------
wu-ftpd ; * ; limiteduser ; Al0800-1100
--------------------------------------------------------------------------------------------


TIA

---

