---
title: "LDAP - local and ldap accounts"
date: 2014-02-09
forum: General Help
---

### Post by sim085 on 2014-02-09
Hello,

I am trying to install and make use of ldap. I am following the tutorial over here:
[https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)

However I have a question. In the tutorial there is the following note: 

*"It's important that uid and gid values in your directory do not collide with local values. Use high number ranges, such as starting at 5000. By setting the uid and gid values in ldap high, you also allow for easier control of what can be done with a local user vs a ldap one. More on that later."*

Now during the installation of the Ubuntu server I created an account for myself. I also want to have an account on ldap (so that I can have access to some other tools I am going to install on the same machine).

My question is; 

(a) should my account on ldap point to the account I already have on the machine? or
(b) should I have a local account and another account on ldap (with same username and password)? or
(c) should I delete my local account and have my account only on ldap?

---

### Post by bab1 on 2014-02-09
> **sim085 said:**
> Hello,

I am trying to install and make use of ldap. I am following the tutorial over here:
[https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)

However I have a question. In the tutorial there is the following note: 

*"It's important that uid and gid values in your directory do not collide with local values. Use high number ranges, such as starting at 5000. By setting the uid and gid values in ldap high, you also allow for easier control of what can be done with a local user vs a ldap one. More on that later."*

Now during the installation of the Ubuntu server I created an account for myself. I also want to have an account on ldap (so that I can have access to some other tools I am going to install on the same machine).

My question is; 

(a) should my account on ldap point to the account I already have on the machine? or
(b) should I have a local account and another account on ldap (with same username and password)? or
(c) should I delete my local account and have my account only on ldap?

You should have a local account (with sudo rights) that is in the range starting with UID = 1000 AND an LDAP account.  The above quote recommends UID's starting with UID = 5000.  

**You should have both a local and an LDAP account but they should not be the same UID.**

[COLOR="#0000FF"]Edit: I usually have this format:  Local user = <firstname>  LDAP user = <first_initial_last name>  The LDAP user John Smith would have: Local = john and LDAP = jsmith.[/COLOR]

---

### Post by sim085 on 2014-02-10
> **bab1 said:**
> 

**You should have both a local and an LDAP account but they should not be the same UID.**

This means that the two accounts will not be related right? changing the password of the ldap account will not also imply a change to the local account? In other words, my account on the machine (to login and install new things) will always be the local account and not the ldap account.

Is there a way to link these accounts or this is not suggested?

---

### Post by bab1 on 2014-02-10
> **sim085 said:**
> This means that the two accounts will not be related right? changing the password of the ldap account will not also imply a change to the local account? 

The two accounts are not related at all.  Changing the password on one account will not affect the other account
> 
In other words, my account on the machine (to login and install new things) will always be the local account and not the ldap account.

Not at all.  Both accounts can act as a normal user account.  The difference is the LDAP account is held in the LDAP server database while the configuration of the local account is held on the local machine in the following files ```
/etc/passwd

/etc/shadow

/etc/group

```
The distinction is that the local account is administered at the individual host (computer) while the LDAP accounts (multiple users) are administered in a centralized fashion on one server for the entire domain (multiple hosts).
> 
Is there a way to link these accounts or this is not suggested?
You shouldn't link local accounts to domain wide accounts.  In fact you don't need many local accounts if you are managing users with a domain wide LDAP server.  My local users are only used as failsafe backups (system administrators) to administer the local machine if the LDAP server is not available.  Not every domain user needs a local account with LDAP.

How many users/machines are you administrating with your LDAP server?  Is this just a test case with one or two hosts (computers)?

---

### Post by sim085 on 2014-02-10
> **bab1 said:**
> How many users/machines are you administrating with your LDAP server?  Is this just a test case with one or two hosts (computers)?

Hello, thank you very much for your answer. I am building a  "server" at home which I will mostly use for backup (documents, photos, etc.). So most probable the number of users will be 1, me. However I always wanted to learn how to set up ldap and link it with other systems which is why I am very interested on best practices rather then just make it work.

---

### Post by bab1 on 2014-02-10
> **sim085 said:**
> Hello, thank you very much for your answer. I am building a  "server" at home which I will mostly use for backup (documents, photos, etc.). So most probable the number of users will be 1, me. However I always wanted to learn how to set up ldap and link it with other systems which is why I am very interested on best practices rather then just make it work.

A lot of the reasons for using LDAP to manage multiple users get's lost if you only have one machine for everything.  The concept is valid though.  If you have a user that can successfully log in and you cant find that user by using ```
getent passwd 

getent group
```...then LDAP is working.  

On the other hand, you can have a local user on multiple machines with the same UID/GID.  Then NFS will work and managing permissions and ownership of files and directories is consistent; just as it would be if you had a centralized LDAP database.  The key is the UID/GID.

---

### Post by sim085 on 2014-02-11
Hello, I managed to install LDAP and PHP LDAP Admin. I created a new user account "Generic: User Account". After this I restarted the machine and tried to login with the username of this account. However I was not given access to the machine. Is this normal? Note that this account only exists in LDAP and is not a local account.

---

### Post by bab1 on 2014-02-11
> **sim085 said:**
> Hello, I managed to install LDAP and PHP LDAP Admin. I created a new user account "Generic: User Account". After this I restarted the machine and tried to login with the username of this account. However I was not given access to the machine. Is this normal? Note that this account only exists in LDAP and is not a local account.

The whole idea is to authenticate the user (jsmith or some such)  on a host (machine) that does not have a local user with that username.  See [this re: getent and LDAP]("http://superuser.com/questions/292199/why-doesnt-getent-show-openldap-users").  Have you tried *[getent.ldap]("http://arthurdejong.org/nss-pam-ldapd/getent.ldap.1")*?

See if this helps: [http://theurbanpenguin.com/wp/?p=2375]("http://theurbanpenguin.com/wp/?p=2375")

Check out [this  google search]("https://www.google.com/search?q=openldap+user+vs+local+user+ubuntu&btnG=Go!") on the subject.

---

