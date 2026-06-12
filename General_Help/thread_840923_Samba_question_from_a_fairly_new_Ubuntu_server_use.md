---
title: "Samba question from a fairly new Ubuntu server user"
date: 2008-06-25
forum: General Help
---

### Post by fat turbos on 2008-06-25
I have the latest ubuntu server running. I am learning how to use samba via command line. I have several shares setup, and in order to test my understanding I created a new share in the smb.conf file that looks like this

[test]
        comment = test directory for samba functionallity
        path= /test
        valid users = tester
        public = no
        writeable = yes

I have another share exactly like that one, only its to that /var/www directory for apache. I went ahead chown'd the test directory directory to the tester user and when I try to login I get an error that the share is not accessbile. However, I can login and access my other wwwroot share with out a problem. So if you have any idea's or could help me know how to fix it or what I am doing wrong. the other user (myself) that I use to login into that share I didnt setup any accounts in for that one is a system account as well as this tester account.

---

### Post by ajmorris on 2008-06-26
hi there,
does this share work via another user, if you allow that user to access the share?

Also, there is another paramater that you could try:

browseable = yes


AJ

---

### Post by fat turbos on 2008-06-26
Hi there, thanks for your reply. Interestingly enough the share does work via another user(I tried setting it up as me, which was created during the installation) and it worked just fine. I also did try the browseable parameter and it still didn't work. I noticed up at the top there is that parameter to sync unix passwords, I'm wondering though could the new account I created not be synced with samba accounts? I didn't have a chance to check whether or not my account was in the samba accounts.

---

### Post by ajmorris on 2008-06-26
> **fat turbos said:**
> Hi there, thanks for your reply. Interestingly enough the share does work via another user(I tried setting it up as me, which was created during the installation) and it worked just fine. I also did try the browseable parameter and it still didn't work. I noticed up at the top there is that parameter to sync unix passwords, I'm wondering though could the new account I created not be synced with samba accounts? I didn't have a chance to check whether or not my account was in the samba accounts.

Did you remember to add the new user to /etc/samba/smbusers ?

AJ

---

### Post by fat turbos on 2008-06-27
you know what I actually suspected that. But I was thrown off in the smb.conf where it has the line to sync unix passwords, but I went ahead and did smbpasswd -a user. and it worked just fine!

---

