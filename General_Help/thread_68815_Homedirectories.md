---
title: "Homedirectories"
date: 2005-09-24
forum: General Help
---

### Post by karmah on 2005-09-24
Hiya
I wanna make one of my FTP users, music, have it's home directory inside mine, /home/karmah/music is that possible?

---

### Post by mlomker on 2005-09-24
Sure.  You can either edit the /etc/passwd file to change the directory or use the graphical user manager to change it.

---

### Post by karmah on 2005-09-24
Ok I have allready tried changing it with the graphical one, but when I log in to the ftp with that user it gives an errormessage about incorrect pathname!
Don't know what I did wrong. I know I typed the right pathname in the users and groups editor (doh) so that's not it.

---

### Post by GTvulse on 2005-09-24
Although you have given the "music" user a home directory inside yours, the former user has different UID and GIDs as you (user id number and group id number). That's what causes the problems you see.

Now, for basic security reasons, I would not assign the "music" user the same UID and GID as your account, unless you make sure that it's pasword locked. Else, you are creating a backdoor to your personal data.

EDIT: I forgot to mention that as well you have to make sure the FTP server you decide to use allows you to chroot the user's directory or anyone can do a simple ```
cd ..
``` and still get at all the contents in your home directory.

---

### Post by karmah on 2005-09-24
Oh ok......hmpf....

---

### Post by mlomker on 2005-09-24
Yeah, the user would need permissions to the directory.  You could **sudo chmod 777 /home/username/music** if you weren't too concerned about security.

---

