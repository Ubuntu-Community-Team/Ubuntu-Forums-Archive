---
title: "CD does not mount"
date: 2006-10-25
forum: General Help
---

### Post by ucd on 2006-10-25
A friend has given me a CD and it does not mount. :-( All others CD I 
have used so far worked well, and were mounted automatically. This one
does not. I do not why and I do not know what can I do. :-(

I have tried to mount it manually ('sudo mount /media/cdrom0') but it 
just hangs up and nothing happen. No messages are written on the screen
and nothing appears on /var/log/messages nor in /var/log/kern.log. The 
system is not hanged up, just the terminal with the 'mount' command. 

'sudo fuser /dev/scd0' didn't bring anything either. No users.

This is the line in my /etc/fstab
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto 0 0

The CD runs in other machines, so it looks like the problem is in my machine.

I use Ubuntu 5.10 upgraded up to now. 

Any other information that you would like to see, just ask. Thank you 
very much for any help. I've been googling and looking on former posts
on these fora but I haven't found anything related...

Thanks again,

---

### Post by CatKiller on 2006-10-25
Maybe your drive just doesn't like the media that your friend used. It happens. Ask him to try burning it on a different brand of disc, or use one of the computers that the disc works on to do the same.

---

### Post by ucd on 2006-10-25
Thanks for the reply, CatKiller.

Is there anything I can do to test this hypothesis (command to try, log to
watch, etc)? I do not have access to my friend (or a burner) until new week... :-(

---

### Post by CatKiller on 2006-10-25
> **ucd said:**
> Is there anything I can do to test this hypothesis (command to try, log to
watch, etc)? I do not have access to my friend (or a burner) until new week... :-(

Not as far as I know. You could search the Internet for reports of that media either working or not with your drive, but other than that I don't know what to suggest.

---

