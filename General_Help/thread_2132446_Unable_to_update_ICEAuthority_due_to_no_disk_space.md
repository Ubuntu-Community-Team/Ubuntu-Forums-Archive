---
title: "Unable to update ICEAuthority due to no disk space left"
date: 2013-04-04
forum: General Help
---

### Post by phu004 on 2013-04-04
Hi guys, I have an ubuntu environment that each user is given a fixed amount of disk space for their home folder.  Unfortunately once the users filled up their home folder, they will not be able to login, simply because ubuntu is unable to update the file .ICEAuthority stored in users' home folder.  

It's not feasible to allocate more diskspace to each user, so I am asking is there a way to tell the system to bypass updating ICEAuthority duing login? 

Cheers,
Pan

---

### Post by phu004 on 2013-04-17
I am still banging my head trying to figure out a solution :( . Can anyone tell me what process/script is updating ICEAuthority? If I can pin point the event which ICEAuthority is updated, then I will be able to do something before it. (such as deleting the browser cache folder)

---

### Post by Impavidus on 2013-04-18
When I used such an account I had a soft limit and a hard limit. When going over the soft limit I received a warning on login, when going over the hard limit I couldn't create any more files and couldn't login any more (never happened to me). When staying over the soft limit for more than one week login was blocked too. That happend once for me (didn't use that system during vacation, so never received the warning). I needed help from someone else to log in and then use su to switch user and delete my browser cache. That was of course a system I didn't manage myself. If I remember correctly, it was a Fedora system using a Solaris UNIX server for my home directory. It indicates what's possible, but I've no idea how it was set up like that.

---

