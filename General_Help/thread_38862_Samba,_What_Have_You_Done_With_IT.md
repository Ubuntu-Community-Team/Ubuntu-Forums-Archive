---
title: "Samba, What Have You Done With IT"
date: 2005-06-02
forum: General Help
---

### Post by patelvishaal on 2005-06-02
Right now in my tech class we have an end of the semester project and my project has to do with samba
i have allready set it up with the basic configurations, and now i am wondering if n e one has worked with it and if u have what are some things you have done.
The more i do with samba the higher my mark will be and right now i am wana know what can be done with samba.

If you have used samba can you post the tutiourls you followed and give me a breif explination of what you have done :D
thanks in advance.

---

### Post by defkewl on 2005-06-02
Using samba waste half of my resources.

---

### Post by patelvishaal on 2005-06-02
can u explain why and stuff cause the more info i get and the more i understand this the higher my mark will be :D
and i really want to know more :P(honestly)
so why did it take so much resources?

---

### Post by localzuk on 2005-06-08
Samba is a good system for integrating Linux file servers into an existing windows NT/200x network. It is also good for running a windows (old style) domain off. It doesn't currently have Active Directory support - at least not useful support.

I have done a lot of work with Samba and find it easier to manage than a windows server.

The tutorials available at samba.org are excellent as are those included with 'SWAT' the online samba administration system.

Some of the things I have done with samba include:

Linking a couple of home pcs together to share music.
Running a school network from 2 samba boxes - 1 as the primary domain controller and 1 as backup.
Set up a samba PDC at one site, and set up bdc's at other sites. The logins were handled by an LDAP server so that it could be scaled to many hundreds/thousands of users.

The software is completely customisable - depending how you want to use it. Just don't expect it to work perfectly with Windows Domain administration tools.

Also, you can't use it in a heterogeneous environment, ie. you can't have a samba pdc and a windows bdc or visa versa.

---

### Post by zyiro on 2005-06-09
Thats exactly what i did i used an older celeron 366 installed a 80 GB drive in and setup a samba share so i can have acsess to my music throught the rest of the house like on my HTPC and in the other office as well have acsess to it from work so i'm not subjected to listen to some stream i can pick and chose what i want to listen to no matter where im at.


-Garrett

---

