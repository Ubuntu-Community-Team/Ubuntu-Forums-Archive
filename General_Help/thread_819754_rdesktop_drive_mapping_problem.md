---
title: "rdesktop drive mapping problem"
date: 2008-06-05
forum: General Help
---

### Post by Rush_898 on 2008-06-05
I can rdesktop to a win2k3 server and it will redirect the disk drive just fine. I can connect to an xp host from another xp host and it will redirect the drive just fine. But when I rdesktop from my laptop to the same xp host it just worked with I get the following error:
Quote:
\\tsclient\Local is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
Normally this would seem like a windows issue, but it works fine between windows hosts. I have tried changing the permissions on the folder I am trying to map without success. The really confusing part is that the same command with a 2003 server will work fine.

What I am trying:

rdesktop -g 800x600 -r 'disk:test=/home/me/test' $xpip

I have tried it also without the '

rdesktop -g 800x600 -r disk:vss=/home/cpettet/vss $xpip

This did previously work. Maybe someone else out there has had this issue? Thanks for any help!  I am using Hardy.

---

### Post by gdwatson on 2008-07-14
I'm having the same trouble.  Did you figure out the cause?

I've found that for some reason I can mount /tmp this way, but not a lot of other stuff, including /home/gdwatson or its subdirectories.  Weird.

Stopping samba didn't help.

---

### Post by samden on 2009-07-16
Exact same problem here. //tsclient/local appears to be available, and I can browse through the drive briefly, but as soon as I open my home folder I get "//tsclient/local is not accessible". After this point I cannot access the drive at all, even folders I could access beforehand.

Any ideas? Running 9.04.

---

### Post by Jack-87 on 2010-08-04
Was there ever a solution to this? I am faced with the same issue

---

