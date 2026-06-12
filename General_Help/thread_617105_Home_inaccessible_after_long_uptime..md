---
title: "Home inaccessible after long uptime."
date: 2007-11-19
forum: General Help
---

### Post by Megatog615 on 2007-11-19
After my computer has been up for a long time(more than 24 hours), my home directory becomes inaccessible by all programs, including Konqueror. I have to reboot to fix the problem. Directories inside my home directory work just fine, though.

I've had this issue for years now, ever since I used Slackware on my laptop years ago(when I started with Linux) I've had this problem.

---

### Post by Megatog615 on 2007-11-20
*bump*

---

### Post by Megatog615 on 2007-11-22
*bump*

---

### Post by Megatog615 on 2007-11-23
*bump*

Seriously people. Come on.

---

### Post by Megatog615 on 2007-11-27
After much frustration and googling I have fixed the problem. Turns out, if an NFS share is mounted in a directory, the directory above it will cease to work when the nfs server goes down. I confirmed this by doing the following(music/ is the directory where the nfs share is mounted):
```
$ sudo umount -f -l music/
```
I was able to use the "ls" command in my home directory again.

Has someone filed a bug?

---

### Post by scxtt on 2007-11-27
> Has someone filed a bug?that's not a "bug" ... if you just remove (intentionally or not) a NFS mount you have to expect problems to ensue ... if you don't want to have ~ problems cause of an (unreliable?) NFS server, mount it somewhere else, like /mnt or /media ...

---

### Post by Megatog615 on 2007-11-27
I don't understand how this isn't a bug. This kind of stuff *isn't supposed to happen*.

---

### Post by mbeierl on 2007-11-27
Well, yes it is supposed to happen.

The mount options that are used for NFS tells it to wait for a response from the server.  So it is doing exactly what it should do.  If you want it to time out instead, look into adding timeo=X to the mount options.

---

### Post by Megatog615 on 2007-11-29
I already had. The timeout is set to 14. "intr" is also used.

---

