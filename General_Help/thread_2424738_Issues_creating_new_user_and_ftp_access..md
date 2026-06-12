---
title: "Issues creating new user and ftp access."
date: 2019-08-13
forum: General Help
---

### Post by mikeaw2010 on 2019-08-13
Hello. I'm having a odd problem.

I am using Ubuntu Server 16.04 with proftpd and when I create a new user 'adduser newuser' I am not receiving any new user options. It doesn't prompt me that its adding a user, it doesn't prompt me that its adding a group, or a home directory and it also does not prompt me to make a password. The command just passes and that is it. I know the command to create a password and have done this. The first attempt, I could not ssh into the account. I tried to remove the user and it told me it couldn't remove it from /etc/passwd. I managed to get around this and removed it piece by piece and recreated a new user. This time the password worked, however; only if I'm ssh'ing. If I try to ftp it tells me I have the incorrect password even though Im using the same password that I use to ssh. What is odd is, this is only happening for new users and the existing users are able to ftp.

I will note that I do have password authentication turned off for ssh access and have key authentication enabled but shouldnt this only affect me if I'm using sftp?

What could be going wrong and what should I look for to fix?

---

