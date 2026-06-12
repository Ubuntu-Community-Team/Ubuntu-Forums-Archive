---
title: "Xubuntu stuck in Login Loop"
date: 2016-01-14
forum: General Help
---

### Post by raju5 on 2016-01-14
My Xubuntu has been stuck in a login loop problem. The login screen appears and it accepts my password. The screen flashes and again returns to the login prompt. I can't even login as root or guest. Tried googling the problem but nothing came up. I am working in a proxy environment. Help would be highly appreciated.

---

### Post by ajgreeny on 2016-01-14
When you get to the login screen hit Ctrl+Alt+F1 and see if you can login there by typing your username, and then your password which will not show on screen.

If that logs you into the command-line we will at least know that your password is correct and your username is still usable.  We can then try to figure out why you can't get to a GUI desktop.

---

### Post by raju5 on 2016-01-15
When I log in the terminal, it says incorrect login. So I logged in as root and created another user. I can login into the terminal using the second username.

---

### Post by ajgreeny on 2016-01-16
If you have set a root password I will have to leave this to others to sort out for you as I have always stuck with the Ubuntu way of only using sudo to raise my rights to those of root.

However, if you can not even log in as your original user to the command line either your username or password must be incorrect, or there is some corruption of the system causing this problem.

As a start can you check the ownership of your old home with command ```
ls -la /home/oldusername
``` from a terminal of the new user you have made, using your old name, of course, where I show oldusername.

---

### Post by pqwoerituytrueiwoq on 2016-01-16
the 1st thing i check is the x.org log and lightdm logs
[FONT=courier new]sudo cat /var/log/lightdm/lightdm.log
cat /var/log/Xorg.0.log[/FONT]

---

