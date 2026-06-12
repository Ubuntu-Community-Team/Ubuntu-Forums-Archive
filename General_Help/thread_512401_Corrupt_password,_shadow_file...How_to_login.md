---
title: "Corrupt password, shadow file...How to login?"
date: 2007-07-29
forum: General Help
---

### Post by darkmediator on 2007-07-29
Hi,

My friend tried to play smart. He changed the login password and grub password! I removed the grub password through windows, but then I read and acted accordingly to remove the password for users. This was when I didn't have knoppix/Ubuntu CD there!

I also tried changing the root password initially, but it said "passwd" isn't installed! But its man pages were available there. Neways after fiddling through windows and removing the user's password so that it doesn't asks for anything, it didn't even boot through grub where u have to press "e" two times, write single and press "b"!!

Now I guess the password and shadow files are corrupt and I dont have the user password to login via GUI. What can I do to restore the system back to normal? I do have knoppix and Ubuntu cd! I guess it might help, but alternative solutions wud be appreciated!

Please gimme all solutions that one knows!

---

### Post by Eddy Dean on 2007-07-29
Try to modify /etc/shadow and put an empty password after your user. I am not sure if it would work (you usually can't change your password), but it's my best bet...

---

### Post by darkmediator on 2007-07-29
Well, thats what I said that I tried that. But it seems I'm not able to boot to single user mode too  after that (for which u do "e" 2 times, write "single" and then "b")! It says 'corrupt password file sulogin can't continue'...something like that then!

---

