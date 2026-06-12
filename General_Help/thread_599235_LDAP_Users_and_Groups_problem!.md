---
title: "LDAP Users and Groups problem!"
date: 2007-11-01
forum: General Help
---

### Post by Steve_Ub on 2007-11-01
Hi there,

I am a new user on these forums, so please excuse me if this topic has been raised before. I did a general search, but could find nother relevant to my problem.

While using the Webmin console in Ubuntu 7.04, I am trying to add users using the LDAP Users and Groups under the System heading. When I click on it, it comes up with the Create User screen that asks me to complete details such as First Name, Last Name, etc, etc. After I fill in the basic stuff, I click on the Create button at the bottom of that page. On clicking on the Create button, I get the following error:

Failed to save user : Failed to add user to LDAP database : objectclass: value #3 invalid per syntax

Anyone have any idea what this problem could be talking about? Please help.

Thanks in advance,

Steve.

---

### Post by Steve_Ub on 2007-11-01
Is there no one who can help with this problem???

---

### Post by WrathofthePenguin on 2007-11-01
Failed to save user : Failed to add user to LDAP database : objectclass: value #3 invalid per syntax

What is value #3? It looks as though you are trying to enter a piece of data into a field that only accepts a certain kind of data.

---

### Post by Eightplant on 2008-02-21
I am also having this problem.
Thought it was because I had not included the samba.schema file in ldap but I added that and still no joy.
Ubuntu server 7.10
Webmin 1.370
Openldap 2.3.35

---

### Post by kngunn on 2008-04-17
I'm seeing something very similar.  I'm using JXplorer to try to add objects to my LDAP database, but the schema appears broken.

For example, if I try to add a person/inetorgperson, most of the required and optional attributes (such as sn) are missing.  Therefore, the addition fails.

I'm looking further into it as I have a pretty good deal of experience in this area.

---

