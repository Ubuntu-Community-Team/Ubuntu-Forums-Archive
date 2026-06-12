---
title: "LDAP user accounts concerns"
date: 2012-12-04
forum: General Help
---

### Post by edbtzy on 2012-12-04
I'm relatively new to linux and I am currently working on a project which consists of creating an LDAP server and client for authentication.  I am currently running Ubuntu 10.04.  I followed tutorials online to get my LDAP server running, adding users, and clients properly authenticating.  However, I did notice that on my LDAP server, my /etc/passwd file does not have any of the LDAP users I recently added.  The only entry I see is an "openldap" user entry belonging to "OpenLDAP Server Account".  This project is all done in virtual machines so any changes can be easily made.

Besides this, everything is working fine. I am able to search my ldap database for the users I created and login using these users credentials.  I also updated my nsswitch.conf file to point to the LDAP files for passwd, group ect.  I was wondering if this is normal behavior.  Thank you in advance. 

For reference, this is the tutorial I followed:
[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

As the tutorial shows, they were able to SSH to the LDAP server using the credentials they created.  However, I am not able to do this since my LDAP users are not populating the /etc/passwd file.

---

