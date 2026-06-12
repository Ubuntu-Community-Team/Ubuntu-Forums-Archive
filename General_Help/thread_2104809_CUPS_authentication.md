---
title: "CUPS authentication?"
date: 2013-01-14
forum: General Help
---

### Post by watgrad on 2013-01-14
Hello,
I'm using a fresh install of 12.04 
Logged in through an admin account...

When I attempt to add a printer, change a printer or access the print server settings in the "Printing" application, an authentication window pops up preventing me from accessing the settings. (see attached)
My admin password will not work...

I am not used to this behaviour [in the past, I never had to use a password to access printing features] and don't know why it suddenly started.  How do I turn off this authentication - or at least determine what login/password this is looking for?

Can anyone help me out?

---

### Post by Morbius1 on 2013-01-14
The only thing I can think of is that somehow you are not a member of the right group. So add yourself:
```
sudo gpasswd -a your-user-name lpadmin
```You will have to logout and login again for the group membership to take affect.

---

### Post by watgrad on 2013-01-14
> **Morbius1 said:**
> The only thing I can think of is that somehow you are not a member of the right group. So add yourself:
```
sudo gpasswd -a your-user-name lpadmin
```You will have to logout and login again for the group membership to take affect.

Thanks!! That worked!

---

