---
title: "Strange user admininstration problem."
date: 2007-02-10
forum: General Help
---

### Post by AtSeaWithC on 2007-02-10
Hello all,

I'm running Ubuntu 6.06.1 LTS "Dapper Drake". A few days ago, I installed the KDE packages.

This morning I started up "Users and Groups" from the "System" menu from KDE, to delete two user accounts I'd created some time ago. I deleted successfully, but here's the weird part. The account I'm deleting from is the account I setup during install and it's given the privilege to use sudo and do administrative tasks. But after this deletion, I got an error message about my account not being in the /etc/sudoers file. Following Ubuntu's "recommendation" I'd disabled the root account.

So here I was, with only one account left, which was somehow mysteriously disabled from doing admin tasks and root disabled. I couldn't creat a new account! I couldn't edit my account! I couldn't even dump the /etc/sudoers file! Finally I went into single user mode and diffed the /etc/group and /etc/group- files and found that my accounts membership of the admin group was present in the latter file, but not the former file! So I copied /etc/group- to /etc/group, and used users-admin to give myself all the preset privileges back, like using CD burner, accessing tape drives etc.

Now my question is what could have caused this problem? I didn't touch my account settings, merely deleted two other user accounts. I never mess with /etc/passwd, /etc/group and other similar files.

One difference was that I was using the "Users and Groups" utility from KDE instead of GNOME, but I can't figure out how that would cause this mishap. The deletion of the two accounts means that the utility has to modify the /etc/group and /etc/passwd files. Could it have a bug that unintentionally erases other members also? As far as I can tell, only the /etc/group file was changed like this.

Anyone else had such a problem? Should I try to reproduce this "problem" and if it's consistently observable, perhaps file a bug report?

Thanks.

---

### Post by taurus on 2007-02-10
The first account that you created when you installed Ubuntu has the system privilege.  Anybody else that you created after that is not.  Therefore, you need to add that user back to groups adm and admin again.  

Boot into recovery mode and at the prompt, do

```
adduser **username** adm admin
```
Replace **username** with the actual username that you log in with.

---

### Post by AtSeaWithC on 2007-02-10
> **taurus said:**
> The first account that you created when you installed Ubuntu has the system privilege.  Anybody else that you created after that is not.  Therefore, you need to add that user back to groups adm and admin again.  

Boot into recovery mode and at the prompt, do

```
adduser **username** adm admin
```Replace **username** with the actual username that you log in with.


But *why* should I need to do that, when all I did was delete two *other* accounts? I did not edit my account at all. I just deleted two other non-privileged accounts that I had created and found a short time later that *my* user name had been removed from the admin, adm, and other such groups in /etc/group. And /etc/group-, which is presumably a backup, did contain the original form, which I copied over to /etc/group.

It seems to me like a bug in some program somewhere. I'll see if I can reproduce this behaviour.

Thanks for your time anyway.

---

### Post by dannyboy79 on 2007-02-15
well it sounds to me like you deleted the user which was first created when you did the install, there will be an easy way to find out. type in more /etc/passwd and you should see what the user id is of the user that you say is the account that was created during the install. if it's anything other than 1000, than, yep, you deleted the account that was created when you did the install. hence also why you had to give myself all the preset privileges back, like using CD burner, accessing tape drives etc. if it is 1000, than I would have to agree with you that something is amiss??? i have never heard of any of the files like that just changing automatically??

---

### Post by ctwardy on 2007-07-12
AtSea: There is a bug in the graphical users-admin program. See for example: #26338.
[#26338]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/26338") and duplicates.  In short, adding *new* users strips group membership from *old* users. Perhaps deleting them is also a problem.

---

