---
title: "Giving guest access to specific folders"
date: 2018-05-17
forum: General Help
---

### Post by webmiester on 2018-05-17
Hi eveyone,

I am using ubuntu 16.04 for x86 architecture.

I want to have a guest session with a specific look and feel.  so I set up an account named "user", set it up, then made a symbolic link to skel using  sudo ln -s /home/user /etc/guest-session/skel

It works except for one icon which fails to appear properly on the panel.  When I investigated, it says that while I am in guest session, I cannot access the home/user/desktop directory where the icon is located, thus it does not display.

I tried using "chmod 777 home/user" and "chmod 777 home/user/desktop" which I read from another forum post, but this didnt work either.  I was thinking of putting the user and the guest user on the same group, however, everytime we log-in as a guest user, the system spawns a new randomly generated guest username, so I dont think this will also work.

So my question here is, how do I give access to the guest session to this user directory where the icon file is located?

What is strange is that I don't have any problems of this sort with my ubuntu 16.04 running in my Raspberry pi units.

I will appreciate any inputs.  Thank you

---

### Post by dino99 on 2018-05-17
[https://www.linux.com/learn/how-manage-file-and-folder-permissions-linux](https://www.linux.com/learn/how-manage-file-and-folder-permissions-linux)

---

### Post by yancek on 2018-05-17
The default guest user on Ubuntu is extremely limited and nothing is saved on reboot.  You might try reading the documentation on this if you want to create a new 'guest' user.

[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

---

