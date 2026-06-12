---
title: "How to change home directory(HELP! I messed up)"
date: 2008-01-31
forum: General Help
---

### Post by Stemman on 2008-01-31
So i changed my only account's home directory to /root instead of /home/ian... and... yeah I can't log in, I made another account but I am not administrator on this account and I need to install some stupid DVD files.  

I basically need to change the administrator account's home directory.  What kinda command line stuff do i need to do?

Thanks!
-Ian

---

### Post by ocwo92 on 2008-01-31
If you can login but get to an empty text console, you probably still have your user ID, and unless you deleted your home directory, it's probably an easy fix. Edit the /etc/passwd file so that the line with your use name looks something like this:

yourusername:x:1000:1000:Your Real Name:/home/yourusername:/bin/bash

where "yourusername" is your login name, "1000" is your uid and gid, and "Your Real Name" is your name in the real world.

If you can't login, boot in safe mode where you'll be logged in as root. From there, edit the /etc/passwd file.

Just make sure you don't ruin the password file, or you may be unable to login. To be safe, you may want to add another user and add this user to the admin group. This will create a backup login name for you that you can use to repair the /etc/passwd file.

---

### Post by Fraktyl on 2008-01-31
If you can't get logged in, you won't be able to use sudo since any new account you create will probably not have admin access.

I'd try to solve it this way.  Reboot into recovery mode.  If you haven't modified the menu.lst file for grub you should have that as your second option on the boot menu.

That'll boot you into a console session (no graphics) and you should be root.

Edit /etc/password using your favorite editor.  nano should be there.

Find your name in that list.  It'll look something like this:
```

user:x:1000:1000:Some Name,,,:/root:/bin/bash

```
Since you changed the home directory to /root.  The second to last field is the one you want to change.

Change it to /home/user where user is your username.  Exit from the editor, and reboot your system.  That should fix it.

---

### Post by Trevorius on 2008-02-13
I did something similar; I changed my username and now the desktop environent won't load after  I login. I tried going in and editing /etc/password, but  the file isn't there.

I just want things back the way they were...

---

### Post by mordox on 2008-02-13
check for the file permissions for the home folder that you are changing to. You should be the owner of that directory and should have read write execute permissions on it.

---

### Post by ocwo92 on 2008-02-13
> **Trevorius said:**
> I tried going in and editing /etc/password, but  the file isn't there.
Hopefully it isn't. The proper file to edit is /etc/passwd.

---

### Post by Trevorius on 2008-02-13
I logged in by recovery mode and edited back my username in the passwd file, and now it's my old login name that appears on the bootscreen, but now my password will not work for either the old name or the new. Btw, when I tried before to login with the new name, it gave me a message saying that it can't start Kstartupconfig. Anyone know where to find that and how to fix it?

---

### Post by Trevorius on 2008-02-14
Any ideas? 

I'm thinking it shouldn't be too serious a problem for someone who knows what they're doing

---

