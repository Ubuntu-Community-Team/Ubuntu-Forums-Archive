---
title: "SSH to use Key and Local Password for authentication.."
date: 2013-02-06
forum: General Help
---

### Post by lynxus on 2013-02-06
Hi Guys,

I have key authentication enabled, That works fine.
But it just lets them in.

How can I get it so it ALSO asks for their local account password?

I enable password authentication as well as key but that does nothing..

Any ideas what to enable in sshd_conf ?

Thanbks
G

---

### Post by papibe on 2013-02-06
Hi lynxus.

By enabling both methods, a user can choose to connect using a key, or a password. However, both methods don't work at the same time.

When keys are well set (proper directory and permissions), the ssh client use them transparently. In other words, it detects if there are keys, and it use them to connect.

A user can revert to using passwords by renaming the ~/.ssh directory. The shh client won't find any key, and it will try to connect requesting a password.

Also, when keys fail, whatever the reason, the ssh client will try connecting again and request a password.

Hope that helps. Let us know how it goes.
Regards.

---

### Post by Stonecold1995 on 2013-02-07
Why would you like it to do this?  To increase security or so only certain computers can get in, but they also need to know the password?  If it's just security, I think a password alone is enough (I think it uses 3DES by default which is decent encryption).  If you only want certain computers to be able to connect, you can set SSH so that it only accepts incoming connections from a certain IP address.

---

### Post by lynxus on 2013-02-07
> **Stonecold1995 said:**
> Why would you like it to do this?  To increase security or so only certain computers can get in, but they also need to know the password?  If it's just security, I think a password alone is enough (I think it uses 3DES by default which is decent encryption).  If you only want certain computers to be able to connect, you can set SSH so that it only accepts incoming connections from a certain IP address.

Its to increase security ( Ive been asked to get this working as part of a project ) however , from what you guys have said and googling. It doesnt look like it does it out of the box without some annoying hacking and I really cant be bothered to hack it just to make it work.

I think we will stick with just Keys / Passphases and locked down FW rules to  only allow certain hosts.


TY

---

### Post by Stonecold1995 on 2013-02-07
> **lynxus said:**
> Its to increase security ( Ive been asked to get this working as part of a project ) however , from what you guys have said and googling. It doesnt look like it does it out of the box without some annoying hacking and I really cant be bothered to hack it just to make it work.

I think we will stick with just Keys / Passphases and locked down FW rules to  only allow certain hosts.


TY
I think you can increase security a bit more by using a more secure cipher.  To do that, go to /etc/ssh/ssh_config and edit the line that says "Cipher 3des-cbc" and change it to "Cipher aes256-ctr".  This will not only be faster but more secure as well, just less compatible with older versions of ssh.

There are plenty of ways to enhance ssh's security without increasing password length (although a long password is still very helpful).

---

