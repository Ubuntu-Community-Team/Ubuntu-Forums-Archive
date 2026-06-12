---
title: "How can I activate SU account?"
date: 2005-09-10
forum: General Help
---

### Post by juantxorena on 2005-09-10
Greetings.
Maybe the title of the post is a bit confusing: I wan't the good old linux account system: A SU account, and user accounts, without any administration permissions. I created the SU account with
 ```
sudo passwd root
``` 
But now I wan't to make the user's accounts as they are in other distros (all distros, I should think), that is, without sudo permissions. How can I do that?

---

### Post by adwait on 2005-09-10
Use the users and groups app, Systen>Admin>Users and Groups and move all the users out of the Admin group, or edit their permissions.

---

### Post by juantxorena on 2005-09-10
But then I couldn't use apps like Synpatic, because I must enter the user password, not the SU pasword.
Also, there aren't users in the admin group, they are in groups with the user's name.
Any ideas?

---

### Post by adwait on 2005-09-11
That's what you wanted right? That other users should not be able to enter their own password to carry out admin tasks? Now you will have to use sudo or su even to execute GUI tasks.

---

### Post by gny on 2005-09-11
Maby I'm not understanding the question but:
To be able to use the sudo command for a user you have to add them in the file 
/etc/sudoers
So if you remove the line 
%admin  ALL=(ALL) ALL
You would have get what you want, that would remove the sudo permission for the group admin.

---

### Post by juantxorena on 2005-09-11
But then, if I open an admin app, like synpatic, I will be asked for the user's password. I want to be asked for de SU password. IOW, when I launch an admin app, the shell launch, for example, ```
gksudo synpatic
``` I want the shell to launch ```
gksu synpatic
``` instead.

I didn't tried the things you said me, just in case I couldn't launch admin apps.

---

