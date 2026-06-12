---
title: "problem with this howto"
date: 2007-08-29
forum: General Help
---

### Post by paulus4605 on 2007-08-29
[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10)

dears I installed the server according to this howto however I have the following questions :

1. I only see one of the three harddrives how can I add the 2 others 

2. when trying to add passwords for a user I get an error message that it's not able to apply the changes (I can give you the exact message when I'm at home tonight.

3. When I'm on my Windows workstation I can get into the fileserver with my administrator account, and I can then only acces the public folder all the other folders are not accessible by me ? how can I solve this?

4 Do I need to add my workstations to the files win dns or can I skip that?

thanks for your help 

kind regards 

Paul

---

### Post by paulus4605 on 2007-08-29
this is the error message that i get 

 smbpasswd -a paul
New SMB password:
Retype new SMB password:
tdb_update_sam: Failing to store a SAM_ACCOUNT for [paul] without a primary group RID
Failed to add entry for user paul.
Failed to modify password entry for user paul
root@fileserver1 /bin/hostname -F /etc/hostname:/home/administrator#


thanks for your help

---

