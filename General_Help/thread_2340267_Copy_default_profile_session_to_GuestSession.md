---
title: "Copy default profile session to GuestSession"
date: 2016-10-17
forum: General Help
---

### Post by carlxz on 2016-10-17
Hi ubuntu community, I'm a trainee at this IT shop and my mentor gave me the task to work around ubuntu for the 1st time to provide a solution to a potential customer, and also to make me do something since there's not much for me to do atm.

I've never used ubuntu until 1 week ago and I managed to create an openbox acc that I'm proud of :D (very basic stuff following a bunch of tutorials hehe)

So, I wanted to know if it's possible to make a full copy of my Administrator account which I'm editing, and just Paste it into the GuestSession account. So the next time I boot ubuntu and chose to login in GuestSession I will get everything as if I was logging my default account.

Also, is there any way possible to deny access to open the settings panel at all?

Thanks everyone who took the time to read this question/ help request. :)

Best regards,
Eduardo.

---

### Post by sotiris2 on 2016-10-17
Check [this](https://help.ubuntu.com/community/CustomizeGuestSession) out.

So copy the appropriate files from your home folder to /etc/guest-session/skel  will probably do the trick. 

To prevent running the settings panel you could remove the execution bit for others. It works on me. Though only root will be able to run it. You could change it's group to something like sudo (the group) so that 'admins' will be able to use it. I can't guarantee it won't cause problems though.

---

### Post by carlxz on 2016-10-17
I just came across with this after I posted this thread. and it worked like a charm! :D

Now I just need to figure out how to remove access total access to the system panel. How do I remove the execution bit for the guestSession? (sorry, I have no idea what that even is ._.)

---

### Post by sotiris2 on 2016-10-17
The system panel is actually unity-control-center . Please read about [file permissions](https://help.ubuntu.com/community/FilePermissions) first and make sure you understand them. unity-control-center is owned by root and group root so if you remove permission for others you will be able to make it non executable but by root.

---

### Post by carlxz on 2016-10-17
I just fixed it by using this command :D

sudo chmod 700 /usr/bin/unity-control-center

thanks for the help sotiris2!

---

