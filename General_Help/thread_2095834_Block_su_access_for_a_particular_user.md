---
title: "Block su access for a particular user?"
date: 2012-12-18
forum: General Help
---

### Post by sahabcse on 2012-12-18
Hi All

I have to block su, root login access for a particular user.

Please help me on this.

Thanks in Advance
Sahab

---

### Post by mlentink on 2012-12-18
AFAIK the only way a normal user would be able to get root priviliges would be through sudo. Remove the user from the sudoers group should remedy that, but this may have changed in the 12.04/12.10 era.

---

### Post by Lars Noodén on 2012-12-18
For the services listed in /etc/pam.d, you can use PAM to block access for a group.  Take a look at the line below in /etc/pam.d/su and uncomment it.

```

# auth       required   pam_wheel.so deny group=nosu

```

That will block members of the group nosu from using su then.  Do the same for the other PAM-using services.  Alternately, you can set so they must be a member of certain group instead.  See the line with 'required   pam_wheel.so' and the comments above it for that.

---

### Post by sahabcse on 2012-12-19
Thanks Lars

---

### Post by dcstar on 2012-12-19
> **sahabcse said:**
> Hi All

I have to block su, root login access for a particular user.

Please help me on this.


Extremely simple, DON'T give them the admin password or admin rights.

Users should not be System Administrators, they should just be Users.

---

### Post by Rockstarever on 2012-12-19
well its right donot give the sudo pass to anyone. thats the basic you can do as may the other users can login the to root account and get back the privilege to there account.

---

### Post by Lars Noodén on 2012-12-19
Also, sudo is not an all-or-nothing setup.  You can configure /etc/sudoers so that groups of individuals can access only one specific program or even one specific program with specific parameters.

---

### Post by sahabcse on 2012-12-20
Thanks to all..

Finally I followed below tricks

Added the su access users into wheel group and uncomment the below entry in /etc/pam.d/su

auth            required        pam_wheel.so use_uid

Ex) 
useradd test
passwed test
usermod -G wheel test

Next, open the PAM configuration file for su ( /etc/pam.d/su) in a text editor and remove the comment # from the following line


auth            required        pam_wheel.so use_uid

This I  have tested in centos 6 box and got succeeded.

---

### Post by dcstar on 2012-12-20
> **sahabcse said:**
> 
This I  have tested in centos 6 box and got succeeded.

Then MARK the thread.

---

