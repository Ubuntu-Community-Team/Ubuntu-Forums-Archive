---
title: "imported users don't show up at login window/Users&amp;Groups"
date: 2014-10-28
forum: General Help
---

### Post by josh103 on 2014-10-28
Hi-

I'm upgrading a number of systems from older Fedora 13 (ugh) to Xubuntu 14.04. The users logging into the system are using local authentication (/etc/passwd, /etc/shadow, etc) to mount NFS home folders. When I re-input those user records into /etc/passwd after installing Xubuntu, those users don't show up in the login list or in Settings > Users and Groups. From doing some research, I know this is probably due to AccountsService and other back-end processes. 

I figured that re-creating the user within Users and Groups and then changing the UID within the Users and Groups panel would update the appropriate config files, but after doing this the user disappears from Users and Groups as well as the login window.

Is there a way to import these users into the system and/or update UIDs for users so that the the appropriate things happen for users to show up in Users and Groups Settings as well as the login list? Thanks.

---

### Post by TheFu on 2014-10-28
I'm not certain but the default lower-number for UIDs in Ubuntu and Fedora might be different. Any numbers lower than X (1000 for Ubuntu, I think), will not be shown.  OTOH, they can manually enter their userid/password and all will work as expected.  That lower number on the login screen is in a config file under /etc somewhere. Since I don't use GUI user management tools, don't know where the settings for that are  - probably a different place, but since it needs to be admin-only, I'd hope under /etc too.

BTW - if I had more than 5 users, I'd use LDAP and kerberos for authentication, not /etc/passwd .... especially if NFS was used.

Update - found it: [http://ubuntuforums.org/showthread.php?t=2222085](http://ubuntuforums.org/showthread.php?t=2222085)

---

### Post by josh103 on 2014-10-28
> **TheFu said:**
> I'm not certain but the default lower-number for UIDs in Ubuntu and Fedora might be different. Any numbers lower than X (1000 for Ubuntu, I think), will not be shown.

Ahh, that might be it- lightdm lists the minimum-uid at 500 in /etc/lightdm/users.conf, but it might either be the bug referred to in your link, or something with AccountsService. I don't know

> BTW - if I had more than 5 users, I'd use LDAP and kerberos for authentication, not /etc/passwd .... especially if NFS was used.

Yup, LDAP/Kerberos is on my short list to deploy, too. Thanks.

---

### Post by TheFu on 2014-10-28
There's another thread going here about doing LDAP + Kerberos - just updated in the last hour.
I think he followed a how-to from 2012-ish ... 

Of course, another option is to use something like puppet or ansible to keep all these files mirrored from a central system - getting users to remember to change their passwords only on that central machine could be hard, however.

If you have a RHEL/CentOS install, running FreeIPA might be the best option. It saddens me to say the power to debian/Ubuntu for that solution has been non-trivial. There are debian/ubuntu clients which work well, I hear.  Just another option and I know some RHEL admins who swear by freeipa.

---

### Post by josh103 on 2014-10-28
> **TheFu said:**
> There's another thread going here about doing LDAP + Kerberos - just updated in the last hour.


I'll check it out. I guess I'm going to have to go with 'empty' user/pass fields at login instead of a list of users regardless.

---

### Post by TheFu on 2014-10-28
> **josh103 said:**
> I'll check it out. I guess I'm going to have to go with 'empty' user/pass fields at login instead of a list of users regardless.

Well, I've always though showing a list of valid userids was less secure.
Plus for non-typists, what better way to learn to type than to practice on their login data? ;)

---

