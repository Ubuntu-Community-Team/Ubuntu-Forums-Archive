---
title: "Permissions for read/write files? Not sure what the go is"
date: 2006-10-16
forum: General Help
---

### Post by dwightwatson on 2006-10-16
Hi,

I have installed Ubuntu Server, and then installed xubuntu-desktop on top of that. What I am trying to do now is edit files on the hard disk so that I can change settings, and add pages to the server.

However, it will not let me save any files in var/www.

I looked around, and then installed vsftp to see if that would solve my problem, however I cannot edit the vsftp configuration file either...](*,) 

My account is called admin, and in the admin group, and I'm not sure how to use the root account or whatever I need to fix this (I'm told I shouldn't chmod the directory because that could cause security holes), and I'm not to good with terminal...

Can anyone suggest how I could fix this problem, or give my account permission to edit files on the hard disk?

Cheers

---

### Post by jd65pl on 2006-10-16
Have you tried using the command below? Have a look [here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo") for some information on the "superuser" and "sudo"

```
sudo *{your command}*
```

---

