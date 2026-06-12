---
title: "Strange Login Message Error"
date: 2008-02-17
forum: General Help
---

### Post by strange_cathect on 2008-02-17
Hello Ubuntu Users,

This morning when I fired up my machine and logged in I got an error message:

> User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users

I did not change the permissions to my /home partition so I am flummoxed as to how this occurred.  It looks like others have had this issue.

I tried to issue: 

> chmod 644 /home/lantern/.dmrc

However, after logging out and back in I am still getting the same message.

Any ideas?  Thanks for your help.

---

### Post by bwhite82 on 2008-02-17
Also do a:

> sudo chown yourusername /home/lantern/.dmrc

Also try the same 2 commands on your home directory.

---

### Post by strange_cathect on 2008-02-17
Ok,

So first I issued your commands for the file.  But it didn't work.  So then I issued the commands for the /home directory.

BUT NOW I CAN"T LOG IN at all!

I think I screwed up the permissions to my /home.

What should I do?

---

### Post by sisco311 on 2008-02-17
reboot in recovery mode(select it from the grub menu)

restore the owners:

```
chown root:root /home
chown -R your_username:your_username /home/your_username
chmod 0644 /home/your_username/.dmrc
reboot
```replace your_username from the commands with your user name(lantern)

reboot in normal mode

---

### Post by strange_cathect on 2008-02-17
Wait, I think I already got it.  Thanks to you both.

---

