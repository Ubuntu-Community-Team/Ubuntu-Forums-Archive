---
title: "Samba"
date: 2005-09-15
forum: General Help
---

### Post by lordgibbness on 2005-09-15
Hi,

I am currently trying to get my music (which resides on my windows pc) to be mounted in linux when i start it up.

I can mount the share via a terminal with: sudo mount -t smbfs "//windows/music" /media/music -o uid=1000 -o username=user -o password=pass

However, I am unsure of what command to add to my /etc/fstab file. At the moment I have: "//windows/music" /media/music smbfs noauto,user,uid=1000,username=user,password=pass,rw 0 0

which I found on a website, but it doesn't seem to work. I'm not sure I need all the options. To test the fstab file do I have to keep rebooting when I make a change?

Any suggestions would be welcome! Cheers!

---

### Post by FLeiXiuS on 2005-09-15
Of course!  

$ sudo mount -a

That'll force to re-reead and re-mount anything in the fstab.

---

### Post by lordgibbness on 2005-09-15
Thanks. Seems that the line is not quite right though:

[mntent]: line 11 in /etc/fstab is bad

Can you see anything wrong with it? Has anyone managed to mout a samba share using fstab?

---

### Post by FLeiXiuS on 2005-09-16
[QUOTE=lordgibbness]Thanks. Seems that the line is not quite right though:

[mntent]: line 11 in /etc/fstab is bad

Can you see anything wrong with it? Has anyone managed to mout a samba share using fstab?[/QUOTE]

Those quotes aren't needed.  You should remove them immediately.

---

### Post by lordgibbness on 2005-09-17
Actually the path names aren't exactly what I have written. It is actually //COMPUTERNAME/My Music, and so the quotes are required.

This works from the terminal as I showed below, but not in my fstab file.

Thanks again.

---

### Post by ISBB on 2005-09-18
[QUOTE=lordgibbness]Actually the path names aren't exactly what I have written. It is actually //COMPUTERNAME/My Music, and so the quotes are required.

This works from the terminal as I showed below, but not in my fstab file.

Thanks again.[/QUOTE]
 I thought for those funky names with the spaces in em you need to do //putername/My\ Music/  or something like that..

---

### Post by professor_chaos on 2005-09-18
I noticed a possible typo.  
You have... ```
password=pass,r w 0 0
```
The space between the "r" and the "w", shouldn't be there.

---

