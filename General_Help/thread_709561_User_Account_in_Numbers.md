---
title: "User Account in Numbers"
date: 2008-02-27
forum: General Help
---

### Post by asharma on 2008-02-27
Hi all, I urgently need help on how to create username using numbers in Ubuntu Server 7.10. 
For example username= 2005007899 password = hajji&*&(&
 Ubuntu does not let me create username with numbers, how is this possible.
The reason I doing this is due to the requirement of the university I am working for requires username as numbers. Please help i am stuck.
Any help will be really appreciated

---

### Post by lloyd_b on 2008-02-27
> **asharma said:**
> Hi all, I urgently need help on how to create username using numbers in Ubuntu Server 7.10. 
For example username= 2005007899 password = hajji&*&(&
 Ubuntu does not let me create username with numbers, how is this possible.
The reason I doing this is due to the requirement of the university I am working for requires username as numbers. Please help i am stuck.
Any help will be really appreciated

I think you're getting nailed by the default value of NAME_REGEX, which is what determines if the username is valid.

Try editing the file "/etc/adduser.conf", and add the line:
```
NAME_REGEX="[a-z0-9]*$"
```
and see if this fixes the problem.

Lloyd B.

---

### Post by astrotech226 on 2008-02-27
That's an issue with the "adduser" command.  This should work if you use "useradd".  How exactly are you trying to add the accounts?

---

