---
title: "School system login"
date: 2015-09-11
forum: General Help
---

### Post by Ethen_Crowl on 2015-09-11
I am designing a system for my school. I would like to have Ubuntu boot up and show a login screen that asks for a username and password, then checks the entered information against a database on the network. How would I do this? I have googled for hours and haven't found anything of use. Thanks in advance.

---

### Post by SeijiSensei on 2015-09-11
You would need to change the method of authentication to use the online database.  Linux uses something called "pluggable authentication modules" to handle this task.  Authentication for logins is handled by /etc/pam.d/login which is set by default to use /etc/passwd, /etc/group, and /etc/shadow.

If you want to authenticate against LDAP databases, read this: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)
Another option is RADIUS: [https://99linux.wordpress.com/2013/05/03/ssh-authentication-using-pam-and-radius-in-linux/](https://99linux.wordpress.com/2013/05/03/ssh-authentication-using-pam-and-radius-in-linux/)

There are also PAM modules to authenticate against MySQL and PostgreSQL databases and dozens of other options. Do a Google search to see.  It's also possible to [join a Linux workstation to an Active Directory domain]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") if that's what you're looking for.

---

### Post by chemist931 on 2015-09-12
Maybe Edubuntu has something like that?

---

### Post by iulian X on 2015-09-12
> **Ethen_Crowl said:**
> I am designing a system for my school. I would like to have Ubuntu boot up and show a login screen that asks for a username and password, then checks the entered information against a database on the network. How would I do this? I have googled for hours and haven't found anything of use. Thanks in advance.

Oftopic: Do you think Shooltool can help you in your activity?

[http://www.schooltool.org](http://www.schooltool.org)         -       [http://book.schooltool.org/screenshots.html](http://book.schooltool.org/screenshots.html)

[http://book.schooltool.org/about.html](http://book.schooltool.org/about.html)
> Credits

**Founder and primary funder: Mark Shuttleworth**

Project Manager: Tom Hoffman

Core Developers: Justas Sadzevi&#269;ius, Douglas Cerna

Release Manager: Gediminas Paulauskas

---

### Post by Ethen_Crowl on 2015-09-15
Thanks all, this really helped a lot. However, is there any way to mount a network drive based off the user name upon login? I would like to have the kid's personal/private network folders mount and become available upon login. The available computers are chromebooks, so there isn't much space for files on the internal drives, and the computers are constantly being used by different students, so syncing the files across all devices would be ineffective. Mounting personal network drives is the best option. Another reason for the network drives is the fact that kids will need to be able to access their files from their home computers after editing them on their school laptops.

---

