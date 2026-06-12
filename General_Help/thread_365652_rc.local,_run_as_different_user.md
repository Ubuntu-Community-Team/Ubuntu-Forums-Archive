---
title: "rc.local, run as different user?"
date: 2007-02-19
forum: General Help
---

### Post by kvonb on 2007-02-19
I have a few daemons that I wish to start on my server, but I would like them to run as another user, NOT root.

I'm guessing that I can put them in /etc/rc.local, but I don't know how to change the user, any help appreciated.

Thanks, Kev :)

---

### Post by dcstar on 2007-02-20
> **kvonb said:**
> I have a few daemons that I wish to start on my server, but I would like them to run as another user, NOT root.

I'm guessing that I can put them in /etc/rc.local, but I don't know how to change the user, any help appreciated.

Thanks, Kev :)

I believe that the **sudo** command has the option to specify a user, check the man page and see if you can use it.

---

### Post by mistik1 on 2007-02-22
su - <username> -c "command -args -arg2"
something like the above will do the trick

---

