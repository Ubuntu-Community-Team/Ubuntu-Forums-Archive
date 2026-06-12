---
title: "Fresh install login drama after restoring backed up files"
date: 2017-12-23
forum: General Help
---

### Post by MibunoOokami on 2017-12-23
Hi all. Following a fresh install after a UEFI drama, the machine was working perfectly fine until putting all backup files back on.
Now when trying to login, type password, hit enter, the screen flashes black momentarily then goes right back to the login screen. I'll be honest with you, the owner is starting to get ticked off with me for the number or problems and duration it's taking to get the machine back in efficient working order.

I'm guessing that something is off with one of the backed up files associated with logging in as I was able to update the machine, restart and log back in without issue. Only since putting backup files back on there and restarting has this problem occurred. 

Does anyone have any troubleshooting tips? Oh, it's an Acer Aspire Z3-710 model desktop FWIW. As always thanks in advance.

---

### Post by MibunoOokami on 2017-12-23
Turned out I made a typo when creating the user account and so it didn't match the backed up data. At least that's what I think the problem was, although changing the user name via tty1 didn't help. I did yet another fresh install and now everything seems to be working perfectly and the owner is somewhat happy. (a bit unhappy because I don't have a Windows installation disk and couldn't reinstall it for them).

Hopefully this thread can be use to someone in a similar situation.

---

### Post by leunam12 on 2017-12-23
login problems after restoring backed up data usually have to do with the method or command you used to backup
because some commands don't preserve permissions and that prevents you from login in.
The right way to backup is using a method that preserves permissions, I always use rsync to
backup my home partition and I always back it up to an ext4 filesystem, NTFS always gives me some kind of error. 
There are other programs that are just as good but the important part is that permissions have to be preserved on the backed up files.

---

