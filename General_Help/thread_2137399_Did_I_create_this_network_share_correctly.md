---
title: "Did I create this network share correctly?"
date: 2013-04-20
forum: General Help
---

### Post by burgertime78 on 2013-04-20
I installed Xubuntu on an old Dimension2400 to see if it will serve me well as NAS.  Anyhow, I wanted to create a simple shared folder to see if my windows machine and WDTVlive box would be able to see it.  What I did worked, I'm just wondering if this is the best/easiest/most correct way to accomplish this or did I just happen to stumble upon my success?

1) Xubuntu terminal
2) ```
cd /
``` (should I have created this folder in root?
3) ```
sudo mkdir testshare
```
4) ```
sudo chmod a+rwx testshare
```
5) install samba
6) xubuntu system settings>samba - add share, select my 'testshare' folder and apply permissions

---

### Post by bab1 on 2013-04-20
> **burgertime78 said:**
> I installed Xubuntu on an old Dimension2400 to see if it will serve me well as NAS.  Anyhow, I wanted to create a simple shared folder to see if my windows machine and WDTVlive box would be able to see it.  What I did worked, I'm just wondering if this is the best/easiest/most correct way to accomplish this or did I just happen to stumble upon my success?

1) Xubuntu terminal
2) ```
cd /
``` (should I have created this folder in root?
3) ```
sudo mkdir testshare
```
4) ```
sudo chmod a+rwx testshare
```
5) install samba
6) xubuntu system settings>samba - add share, select my 'testshare' folder and apply permissions

If it works then it is good for you.  Will you have multiple users sharing data in this directory?  What happens then?

---

### Post by burgertime78 on 2013-04-20
Yes, I mean, this directory was only a test.  But, if it were not a test, it would be a dir which contained movies and I would want all machines in my house to have full access for streaming purposes.

---

### Post by bab1 on 2013-04-20
> **burgertime78 said:**
> Yes, I mean, this directory was only a test.  But, if it were not a test, it would be a dir which contained movies and I would want all machines in my house to have full access for streaming purposes.

The test is not complete.  Machines don't have access, users do.  By users I mean user accounts.  These accounts are not just you, there are system users too.

The type of share you have created are Samba *usershares*.  Typically these shares are created by users in their own home directory.  The permissions are either the user or all users.  The way you are using the share there could be permissions issues.  This can only be determined by by you using the shares and seeing what happens.

The other type of share is created by the administrator (root) of the machine via sudo.  This is done by editing the /etc/samba/smb.conf file.  The administrator can control user access via permissions.  This is the type of share that typically resides outside of the users home directory (i.e /data or /srv or /share).

So basically you are using an ad hoc type of share to do administrator duties.  If the share you have created doesn't work you will have to revert to administrator created shares.  On an Ubuntu host, the first user created at install time has the right to administer the the machine (via sudo).  Did you install Ubuntu?  This user has the UID of 1000.  We can see what account that is with this command at the CLI in the terminal```
 getent passwd 1000
```

I am the administrator of my install.  Here is what I get```
getent passwd 1000
bab:x:1000:1000:bab,,,:/home/bab:/bin/bash
```

---

