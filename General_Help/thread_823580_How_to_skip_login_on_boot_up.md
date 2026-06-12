---
title: "How to skip login on boot up"
date: 2008-06-09
forum: General Help
---

### Post by atthecoast on 2008-06-09
I want to make a system boot up (from power on) such that a particular user is logged on to the desktop. I wish to allow multiple users on the system, and would like to retain a standard login screen if the user logs out.

Is there a reasonably clean way to accomplish this? (Meaning that I don't need to recompile the code behind the login window to recognize first boot.)

---

### Post by brendon on 2008-06-09
I wouldn't recommend this if the PC is in an insecure environment.

Open - System -> Administration -> Login window
Select the Security tab
Check - Enable Automatic Login
Select the desired user
Close

---

### Post by zvacet on 2008-06-09
You can do it like** brendon** adviced,but I don´t see the point of doing that.if you,for example,select your account to autologin why will other user logout and then put his/her username and password when they are in position to use your account.Autologin is good if you are only user and you don´t want to type username/password everytime you want to use your comp.Even then you will autologin in non-administer account.

---

### Post by atthecoast on 2008-06-09
Thanks for the quick answer. Exactly what I wanted.

Box is in a secure environment. Just replaced a failed Windows box for my 86 year old mother. All she needs is e-mail and Open Office. I have it set up to share her desktop so I can use VNC to see her screen and drive if need be. I am just trying to keep it as simple as possible so want it to boot up with her already logged in. I have only the ssh port forwarded to this box and have sshd_config set to require an ssh key file and only allow my user name to ssh to the box. I'm opening a tunnel with ssh then launching vnc via the tunnel. Hopefully this is enough security. She is now running Ubuntu 8.04 and with my ability to see her desktop giving remote help is quite easy. So far it is working great.

---

