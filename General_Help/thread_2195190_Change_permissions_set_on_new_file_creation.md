---
title: "Change permissions set on new file creation"
date: 2013-12-22
forum: General Help
---

### Post by fishiazza on 2013-12-22
My family share an Ubuntu desktop computer.
We have our individual logins and are all members of our "family-name" group.

Some folders are shared between all users in the group.

Unfortunately when any of the group members create or modify a file in the shared folder, they change the group permissions of that file to read only.

How can I set it up so that whenever a file is created or modified that the group permissions are set to read+write rather than read only?

---

### Post by efflandt on 2013-12-22
You may need to use "**sudo** " prefix for commands changing directory group or permissions if not the owner.

You need to chown the directory to the group: **chown :users directory**

 set the group sticky bit on the parent directory: **chmod g+s directory**

Example of **sample** directory set to group "users", group sticky bit set, and files created by 2 users in the group:```
efflandt@xps8100-1204:~$ ls -dl sample
drwxrwsr-x 2 efflandt users 4096 Dec 22 19:55 sample

efflandt@xps8100-1204:~$ ls -l sample
total 0
-rw-rw-r-- 1 deffland users 0 Dec 22 19:55 deffland.txt
-rw-rw-r-- 1 efflandt users 0 Dec 22 19:55 efflandt.txt
```

---

### Post by fishiazza on 2013-12-22
Thanks.  The sticky permissions is a nice touch, but new files created still have permissions:
-rw-r--r--

I want newly created files to be created with the group also having rw permissions.
How do I do that.

---

### Post by bab1 on 2013-12-23
> **fishiazza said:**
> Thanks.  The sticky permissions is a nice touch, but new files created still have permissions:
-rw-r--r--

I want newly created files to be created with the group also having rw permissions.
How do I do that.
This is a *umask* problem.  What version of Ubuntu are you using?  

The "sticky bit" that you are referring to is not a sticky bit at all.  It is the **sgid** bit.  It is what you want to use as it sets the group ownership,

---

### Post by fishiazza on 2014-01-02
> **bab1 said:**
> This is a *umask* problem.  What version of Ubuntu are you using?  

The "sticky bit" that you are referring to is not a sticky bit at all.  It is the **sgid** bit.  It is what you want to use as it sets the group ownership,

I'm using Ubuntu 13.10 with Unity desktop.

Thanks.  You pointed me in the right direction with *umask.  *A little googling shows that that is indeed my problem.  It also seems that it is not possible to change the default umask for a folder only.

However that searching suggested a workaround which I have done... I have just moved the folder in question to an NTFS partition where the permissions are not a problem (as long as you want them totally open, which I do for that folder).  This "solves" my problem.

---

### Post by bab1 on 2014-01-02
> **fishiazza said:**
> I'm using Ubuntu 13.10 with Unity desktop.

Thanks.  You pointed me in the right direction with *umask.  *A little googling shows that that is indeed my problem.  It also seems that it is not possible to change the default umask for a folder only.

However that searching suggested a workaround which I have done... I have just moved the folder in question to an NTFS partition where the permissions are not a problem (as long as you want them totally open, which I do for that folder).  This "solves" my problem.

It would have been easier to just update the package that is causing the problem.  See [here]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686") for the correct solution.

Specifically, you should download the upstart deb package from here:[ https://launchpad.net/ubuntu/trusty/+package/upstart]("https://launchpad.net/ubuntu/trusty/+package/upstart").  Then install the package```
  

sudo dpkg -i <package.deb>


```...reboot and you have the proper rw-rw-r-- permissions.  There is no need to use NTFS to solve a Linux problem.

---

### Post by fishiazza on 2014-01-09
Really? So will that allow me to have different umask from the system-wide one for a SINGLE FOLDER and it's contents will it?
The bug doesn't say anything about that.

---

### Post by bab1 on 2014-01-09
> **fishiazza said:**
> Really? So will that allow me to have different umask from the system-wide one for a SINGLE FOLDER and it's contents will it?
The bug doesn't say anything about that.
The umask is not applied to any existing file or folder.  The umask is a setting that sets the permissions at creation time.  I'm not sure what you are after here.  Your original question does not refer to a "SINGLE FOLDER" (see below) > [COLOR="#0000FF"]How can I set it up so that whenever a file is created or modified that the group permissions are set to read+write rather than read only[/COLOR]? ...When you set the umask to 0002 rather than 0022 you have solved the problem.  The update allows just that.  Without that patch the umask is always set to 0022.

Do you have a secondary problem?

---

### Post by fishiazza on 2014-01-09
Sorry if the question wasn't clear.
I was referring to permissions in the Family Group's shared folder only.
 (Refer to the paragraph before the one you quoted. Sorry, I can't quote here, am away on holidays and using a mobile device).

AFAIK, (and I don't know much), umask can only be set system-wide?

---

### Post by bab1 on 2014-01-09
> **fishiazza said:**
> Sorry if the question wasn't clear.
I was referring to permissions in the Family Group's shared folder only.
 (Refer to the paragraph before the one you quoted. Sorry, I can't quote here, am away on holidays and using a mobile device).

AFAIK, (and I don't know much), umask can only be set system-wide?

Umask can be set at any time.  The system wide settings are the default and are persistent over reboots.  What is the problem with the Family Group's shared folder?  Are you having problems with ownership or permissions?  Have you installed the patch?

What are the permissions and ownership when you create a file in the in the Family Group's shared folder?  You should have rw-rw-r-- as permissions (read and write on owner and group).  After the install of the patch you do need to set the **sgid** to provide common group inheritance.  You need to:
[LIST]
[*]Set the common group on the root folder of the share (chgrp)
[*]Set the **sgid** bit on the folder that is the root of the share (sudo chmod g+s)
[*]Make sure the system umask is set to 0002 (umask)
[/LIST]

---

### Post by fishiazza on 2014-01-21
Sorry for tardy response, I've been away.

My issue was that I was happy with the current system default umask of rw-r--r-- and only wanted rw-rw-r-- on the ONE SINGLE Family folder.
This is because every user in the family had their main group as the family name.  If I allowed the group to have system wide rw permissions, then everyone in the family could access all of each others files.

I realise this is not the accepted way of doing things, with each user's main group normally also being their username.
I had it setup this way because there are some non-family members who use the machine also.

Anyway I've now installed the new upstart package and changed each user's main group to a different one other than the family name, so that they can't rw each others files in files other than the Family shared folder.

Problem solved.  Thanks.

---

