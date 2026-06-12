---
title: "[SOLVED] Restart PC Script?"
date: 2008-01-17
forum: General Help
---

### Post by dirtmaster88 on 2008-01-17
Hello,

I set up a locked down xfce environment to use in my workplace. I locked down everything very well but have no way for the user to reboot or shutdown the machine. I would not like them to have access to log out or switch user or anything like that, reboot and shutdown only. I don't know how to script very well and need some help. Is there maybe some way to have the script pop up a window asking to either reboot or shutdown? I have a custom menu and could create a shortcut launcher to the script. Any help would be GREATLY appreciated!

The user does not have any sort of root privileges, is this still possible to let them shutdown or reboot?


Thanks!

---

### Post by meindian523 on 2008-01-17
1]sudo init 0 or sudo shutdown -h 
for shutdown

2]sudo init 6 or sudo shutdown -r
for reboot

You will have to give them privileges to shutdown/reboot from System>>Administration>>Users and Groups

You can use zenity to handle the popup window.

---

### Post by dirtmaster88 on 2008-01-17
xubuntu (xfce) is a little different I guess. There aren't permissions available for shutdown/reboot in the users and groups editor

---

### Post by meindian523 on 2008-01-17
oops,the privileges for shutdown and reboot are not available in the Users and groups in Gnome too,but the commands are the same,possibly zenity too,look it up in the terminal using man zenity.

---

### Post by dirtmaster88 on 2008-01-17
is there a specific group that I could put the user in or possibly create a group and give the shutdown command excecutable permissions for that group?

---

### Post by meindian523 on 2008-01-17
I guess either the root or admin group would have those privileges,but you will have to wait for more experienced people to tell you how exactly those privileges can be added to a group.Just a thought,I guess in modern *nix systems,the shutdown and reboot privileges are default for all users.Not sure since I'm the only user on my Ubuntu.:( You might have to create a test user to find out.Just put him in only the default group ie the group with groupname=username and see whether he has shutdown/reboot privileges.

---

### Post by dirtmaster88 on 2008-01-17
I figured it out.... I had to go into the file /etc/sudoers and give access to the shutdown command. I created a group called shutdown and added my restricted user to it then granted permissions for the shutdown group to the file /sbin/shutdown.

This is the page that really helped me out alot:
[http://gentoo-wiki.com/HOWTO_Let_a_common_user_shutdown/reboot](http://gentoo-wiki.com/HOWTO_Let_a_common_user_shutdown/reboot)

---

### Post by meindian523 on 2008-01-17
Ah,the gentoo wiki,wonder it didn't strike me earlier.#-o
Cool,mark the thread as solved.

---

