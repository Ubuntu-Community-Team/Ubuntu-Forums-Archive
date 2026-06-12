---
title: "Disk Quotas for users..."
date: 2007-07-31
forum: General Help
---

### Post by Slazer on 2007-07-31
Ok... I understand how quotas work. I have all the quota stuff setup on my server, so here is my problem. I have this NFS server with all the user's home directories on it (right now 230+ directories) so when they log into the network, their home directory is grabbed from that NFS machine.  I'm want to enable a disk quota for the users but I don't want to do it manually for each of the 230+ users.

My question is: does anyone have, or know where to find, a script that will go through the list of users and set the quota for it. I know the "setquota -p <prototype_user> <user_without_a_quota>" will copy the setting from the "prototype_user" to the "user_without_a_quota" but like I said, I don't want to do that manually... so hoping someone could point me to a script to help me out with this.

Thanks a lot. Sorry for the long-ish post.

---

### Post by Don_Sonic on 2007-10-18
How 'bout this script?
Only thing is, you'll have to make a list of the users first an' call the script like this:

~#./setquotas.sh listfile

#Filename: setquotas.sh
#Set list delimeters
IFS=$',\n';

cat "${1}" | while read userName;
do
	#Set disk quota
	setquota -u "${userName}" <quotaLimit> <quotaLimit> 0 0 <filesystem>;
done;

---

