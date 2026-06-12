---
title: "cant access nfs share"
date: 2016-05-02
forum: General Help
---

### Post by eran_raz on 2016-05-02
Hi all.

we have several Ubuntu pc in our organization. thy all used to access a share on our storage. since yesterday or so most of them except one cannot access this share anymore. from windows pc, the same users can access the share.

i tried to use the user from the computer who can access the share on the other Ubuntu pc - didn't work.

the only thing that changed in the last couple of days is the fact that we changed password to all of our users (Active Directory users).

does anyone have an idea what went wrong? any direction to check?

Thanks in advance.

---

### Post by Yaron_Klein on 2016-05-04
Hi,
It looks like you were effected by a recent update that changed the default value of spnego from no to yes.
modify your smb.conf file accordingly:

sudo gedit /etc/samba/smb.conf

Right after the [global] section in the file add the following line:

client use spnego = no 

Save and restart samba
service samba restart

---

### Post by eran_raz on 2016-05-05
i think youre rigty becouse i found out the computer who didnt have the problem were using an older samba version (4.1.6) and all the rest updated the samba client (4.3).

---

