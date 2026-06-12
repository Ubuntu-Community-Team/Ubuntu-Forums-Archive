---
title: "no password"
date: 2007-04-06
forum: General Help
---

### Post by anafshalom on 2007-04-06
When I installed Ubuntu 5.10 i386 I was asked to enter an username and pasword.  That is the only password I ever entered.  

Now I'm trying to update to [I]Edgy[I].  If I use Synaptic I am asked for a pasword for root, and the one I used during installation does not work.  If I us a terminal entering [FONT="Fixedsys"]gksu "update manager -c[/FONT]"  it also asks for the root password, and appearently I don't have one.  I did check in Users and groups and the user I created during installation does have admin privlidges.  

What to do?

anafshalom

---

### Post by taurus on 2007-04-06
what's the output of this command from a terminal?

```
id
```

---

### Post by anafshalom on 2007-04-06
damita@ubuntu:~$ id
uid=1000(damita) gid=1000(damita) groups=4(adm),20(dialout),24(cdrom),25(floppy) ,29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),10 00(damita)
E]

---

### Post by jbumgar on 2007-04-06
go to terminal

code:

passwd uid  enter new password and verify

then you should be ok.

---

### Post by anafshalom on 2007-04-06
Thank you!  it worked!

Reuven

---

