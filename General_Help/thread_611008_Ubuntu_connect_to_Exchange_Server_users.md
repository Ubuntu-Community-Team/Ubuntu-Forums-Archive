---
title: "Ubuntu connect to Exchange Server users?"
date: 2007-11-12
forum: General Help
---

### Post by dboot on 2007-11-12
I administer an Exchange 2003 Server with around 60 users. I would like to set up an Ubuntu public desktop that requires each user to login using their Active Directory credentials and (hopefully) open Evolution or Thunderbird to check their email. 

Each user should have their own desktop with a set size of /home/username that only they can access, printing limitations (10 pages per week for instance), and Evolution immediately connects to their Exchange email.

Is this possible using Ubuntu or should I stick with Windows? I would be thrilled if they can only login to the domain and have a unique desktop.

Thanks for any help!

---

### Post by jpietari on 2007-11-12
Setting up Evolution is very easy;  Active Directory and Linux requires some fiddling around.  Look up Samba and Winbind.

---

