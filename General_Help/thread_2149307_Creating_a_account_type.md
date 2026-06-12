---
title: "Creating a account type"
date: 2013-05-28
forum: General Help
---

### Post by Pontinhos on 2013-05-28
Hi,

I would like to know if it's possible to add an "account type" in the application gnome-control-center user-accounts.

Is there a possible do add an option in the "combox" instead of adding by command the user in a certain group? 
Or, perhaps, a tool who helps to manage this kinda of stuff.

---

### Post by sudodus on 2013-05-28
Welcome to the Ubuntu Forums :-)

You can install *** users-admin***, which has more options than the built-in facility in Ubuntu.

```
sudo apt-get install gnome-system-tools
```

---

### Post by Pontinhos on 2013-05-28
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

You can install *** users-admin***, which has more options than the built-in facility in Ubuntu.

```
sudo apt-get install gnome-system-tools
```

Thank you. I always admired Ubuntu large community. :D

That's undoubtedly an option. But I usually have to add users in the same group(which doesn't fit in "Default" neither in "Admin"). 

Whilst gnome-system-tools gives me a help, I wonder if there's an option to add a new combox to select the account type. 
For example, giving me the option to select among "Admin", "Default" and "User for x people", using gnome-control center. Or selecting among Admin, Default, Custom or "User for x people", using gnome-system-tools.

Thanks for your incredibly fast answer!

---

### Post by sudodus on 2013-05-28
There is a button for managing groups in ***users-admin***. There are a couple of default account types available, when you create a new user.

And you can edit the file [FONT=courier new]**/etc/group**[/FONT] manually with superuser privileges with a text editor. What more do you need?

---

