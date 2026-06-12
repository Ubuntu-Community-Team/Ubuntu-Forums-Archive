---
title: "Creating a user without a password"
date: 2007-01-23
forum: General Help
---

### Post by daemonoid on 2007-01-23
I've asked this before but got no replies, thought I'd try again. I want to create a group of (very low privilege) users for my media centre pc that don't require passwords. Then anyone can use the face browser to just get straight in without having to mess about with the keyboard. 

I can handle the user privileges an the scripts to auto-run the correct software for each user but the login from the face browser without a password is a little more annoying - either i've missed something simple or it's not possible by design. Anyone got any ideas?

---

### Post by Ramses de Norre on 2007-01-23
I found this in a mailing list:
> I recently had the same problem. After some googling I found out that the LocalNoPasswordUsers option was removed in GDM 2.4.2.95 because it did not play well with the improved PAM support. Thus I solved it entirely through PAM:

Edit /etc/pam.d/gdm and insert a line like
```
auth sufficient pam_listfile.so sense=allow file=/etc/passwordless item=user
```
above the line that reads
```
@include common-auth
```
Then create /etc/passwordless and put in the names of all the users you want to be able to logon without a password, one on each line. Make sure that file is only writeable by root. Et voila, you're done.

It might solve your problem, they also mentioned removing the user's password with **passwd -d username** but the gdm solution looks better I think.

---

