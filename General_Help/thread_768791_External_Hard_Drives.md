---
title: "External Hard Drives"
date: 2008-04-26
forum: General Help
---

### Post by Michael Hanson on 2008-04-26
Why can't I move folders and docs unto my seagate ext hard drive? Message pops up saying I don't have permission to do this, so I check properties and the permission  tab and its not an active window where I can make any changes.

Where do I go to make the change where I will be able to move doc's unto my external hard drive?

---

### Post by Claus7 on 2008-06-21
Hello,

I do not know if you have figured this by now, yet this is my reply:
```
sudo chown (user name) /media/(name of your drive)
```

Hope this helped,
Regards!

---

### Post by geo909 on 2008-06-21
Btw freeagent drives have a little issue in linux.
Try googling "linux seagate freeagent drive spindown problem".

When you let the disk idle for 10-20 mins, it will not respond
afterwards until you plug it out and replug it in.

Just have this in mind, for your case the solution seems to be Claus7's reply.

---

