---
title: "adminstator problem"
date: 2006-10-24
forum: General Help
---

### Post by jay941 on 2006-10-24
my ubuntu dapper has stopped allowing me to open system files like adminstarting the 
internet connection. i cannot get to the screen that will allow me to choose which
method i will use to connect. cannot do wireless, lan nothing. any help would be appreciated. do i have to reinstall?

---

### Post by matthewstory on 2006-10-25
did you alter your sudoers file?  And if so did you alter it with visudoers, or just edit it?  If you did alter it badly, you'll need to restart in single user mode to make the fix . . . to check to see if sudo is working at all try this:

sudo gedit <some text file>

If that doesn't work, then your sudo is screwed up and you'll need to edit the /etc/sudoers file.

---

### Post by jay941 on 2006-10-26
i can't get sudo to work with anything. this is a single user laptop, so there are no other passwords. when i try to access the /etc/sudoers file,
it won't let me. says i don't have permission. can you think of anything else
i can try?
thanks

---

### Post by aysiu on 2006-10-26
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by matthewstory on 2006-10-27
to edit the /etc/sudoers file you'll need to boot into recovery (single user) mode, from the grub boot menu.  You could use sudo to edit it . . . but sudo is broken . . . ha!  Gotta love it, so yeah boot into single user mode and edit the file.  Technically, there is a program specifically for editing the sudoers file called visudo, which uses vi, and it checks the config file after you save, and asks you if you want to save it for sure if there are configuration issues . . . to avoid the problem of not being able to sudo at all, and therefore not being able to edit the sudoers file.

---

