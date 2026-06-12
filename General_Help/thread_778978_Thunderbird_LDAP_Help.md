---
title: "Thunderbird LDAP Help"
date: 2008-05-02
forum: General Help
---

### Post by bstan2 on 2008-05-02
I am trying to setup Thunderbird 2.0.0.12 to connect to our Microsoft LDAP server.  I am have used the following information to no avail:\

NAME:  Test
Hostname:  server1.domain.edu and server1
Base DN:  DC=school.name,DC=edu
Port Number:  389, 3268, 636
Bind DN:  domain\username
SSL:  Yes and No

It does not matter what I type in, I keep getting a message that Replication failed when I click on Download Now.  I am never prompted for my password.  I have setup Thunderbird to use IMAP to check my e-mail and that works great.  I just cannot get LDAP to work.

I went to our DC and ran ldp.exe  I verified that the port number is 389 and I can bind myself to the directory.

HELP!!

Thank You

---

### Post by wolfteeth on 2008-10-30
I am encountering the same problem but no findings so far..

I can confirm my LDAP settings are correct because I used the same settings on Outlook Express Address Book and which can search the users' information via LDAP, however, when I do the same settings on Thunderbird, it didn't request me to input domain password..and when I click Offline to download, it just shows Replication failed...do you have any good ideas? (I am using ubuntu8.04)

---

