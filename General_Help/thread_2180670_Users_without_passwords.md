---
title: "Users without passwords"
date: 2013-10-14
forum: General Help
---

### Post by X D face me on 2013-10-14
Hello everyone

When i listed all my users with # lastlogin. there were a lot of unused users. i wanted to find out there passwords but in /etc/shadow they dont seem to have a password. Can someone explain what this is about?

Regards, Bastiaan van Hoorn

---

### Post by TheFu on 2013-10-14
Different daemons run as different users. These are security techniques. Without a list of the users, we cannot guess if there is any issue at all.  However, if the uid - the number for the userid - is less than 1000, generally, those are system accounts.  more /etc/passwd to see them.

Of course, you might be using ldap or other external authentication methods - if so, let us know, since other userids CAN come from those things too.

---

### Post by CaptainMark on 2013-10-14
Users passwords won't be accessible by anyone else, even the superuser. If you are the superuser you can gain access to someone's account using the su command but their password is still their own and I doubt anyone will give you any help to break a shadow passwords file, at least I hope they wont.

---

