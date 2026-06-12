---
title: "Set a Web-managed FTP"
date: 2008-07-01
forum: General Help
---

### Post by Xi0N on 2008-07-01
Hi!
This is my idea:
I want to set a FTP server up.
The problem is that it will be managed by win-users remotely (they dont have any linux knowledgement) and i have been thinking that maybe it would exist some software that makes it possible to add/remove FTP users remotely, through a web interface.
I dont know if such thing exists, and i want to ask you for some advice on the subject.

Thanks!

---

### Post by ddixonr on 2008-07-01
I use gproftpd to run my ftp site, and when I'm not at home and need to add users, I just vnc in and make the user. Do you need something to add users automatically without your assistance at all?

---

### Post by Xi0N on 2008-07-01
Well, the point is to make it easyer for my mates to create the ftp accounts.

Each time we have a new client that wants to upload something to us, we have to create a new account for them (and a new folder).
My idea is to share a global folder that contains all the client's folders by smb (the ftp is on a server without any screen, just remotely-managed by me), that way we can create the new folders easily.
the problem is for creating the new ftp users. My mates, the ones that will create the ftp users for our clients, dont have any kbowledgement about unix, vnc or anything... and i was wondering if there would be any ftp server software that allows to add the new ftp users through a web interface..... that would make it more simple for my mates to do their job.
i dont actually know if im asking for something impossible... :P

Thanks

---

