---
title: "Guidance needed setting up users and groups"
date: 2016-05-18
forum: General Help
---

### Post by keith30 on 2016-05-18
I look after a network of Win 7 PC's in a small office connected to a server running Ubuntu. Until now we have had no need for much security as everyone has the right to see all files. However, I would like to introduce some security and would like to check a few things before I proceed.

My plan is to have 7 users affiliated to three groups (admin, surveyors and typists). My aim is to control access to the shared folders. All PC's will have a user and password and I will add the same user names and passwords to Ubuntu and Samba via useradd, passwd, smbpasswd. Correct so far?

Once this is done I will create the groups (groupadd) and then add users to each group (usermod). 

As I understand it I will be best to use forcegroups in the smb.conf.  Finally I will need to chown the existing shares to the new respective group.

Have I missed anything?

Is there a way of making sure no one can delete a folder other than admin? I don't mind about individual files being deleted.

Thanks

---

