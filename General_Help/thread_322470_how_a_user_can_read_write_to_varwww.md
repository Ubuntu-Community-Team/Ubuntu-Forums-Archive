---
title: "how a user can read write to /var/www"
date: 2006-12-20
forum: General Help
---

### Post by nephish on 2006-12-20
lo there all !
i have a regular user that needs permission to write to the /var/www folder so that he can update a website there. I can't chown the folder to him because its owned by www-data.
how would i be able to allow this user to write to this folder without the www-data loosing the ability to write there?
thanks

---

### Post by aysiu on 2006-12-20
Try this: ```
sudo chmod -R 775 /var/www
sudo chown -R www-data:www-data /var/www
sudo adduser nephish www-data
``` The first command makes it read/write/execute for owner and group. The second command makes sure that the owner is www-data and the group is www-data. The third command adds your user (here, for this example, *nephish*) to the group www-data.

---

### Post by po0f on 2006-12-20
nephish,

From the terminal:
```
[FONT="Courier New"]$ sudo gpasswd -a user_name www-data[/FONT]
```
Log out and back in for it to take effect.  To check, type:
```
[FONT="Courier New"]$ groups[/FONT]
```
at the terminal, and www-data should be listed as one of the groups you are in.

---

### Post by nephish on 2006-12-20
well thanks, gents.
appreciate it very much

---

