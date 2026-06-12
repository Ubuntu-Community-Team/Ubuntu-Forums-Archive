---
title: "How to log in as root instead user at login?"
date: 2007-09-17
forum: General Help
---

### Post by jcer93705 on 2007-09-17
so i can do some administrator stuff in grahpical like drag files from cd to files to root? I know its bad but i need to. At login i cant login using root and password it wont let me login as admin. At fedora i can do it but not in here. Can someone help me?

---

### Post by Bachstelze on 2007-09-17
You can do *gksudo nautilus* to run Nautilus as root. Logging in as root graphically is *very* bad.

---

### Post by agathreya on 2007-09-17
i need to log in as root to change the permission of file httpd.conf which is in /etc directory, how do i do it???

---

### Post by Wim Sturkenboom on 2007-09-17
> **agathreya said:**
> i need to log in as root to change the permission of file httpd.conf which is in /etc directory, how do i do it???Open a terminal and use *sudo -i* to get a shell with root permissions. Next you can use chmod to change the permissions.
By the way, it's confusing to hijack somebody else's thread.

---

### Post by Tsu Dho Nimh on 2007-09-17
> **HymnToLife said:**
> You can do *gksudo nautilus* to run Nautilus as root. Logging in as root graphically is *very* bad.

Why is logging in as root "graphically" a bad thing? 

When you type as badly as I do, and have days where typing is painful, pointy-clicky GUIs are not only easier to use, they hurt less.

---

### Post by anaconda on 2007-09-17
You can enable root, just give root a password with:

sudo passwd root

and then to enable graphical root logins:
go to system>Administration>Login window and there under the security tab select the allow graphical root login.. or similar..


Another temporary solution is to type Ctrl-Alt-F2 and then run 
sudo startx
it will get you to x with root rights. 

And why is it BAD.. I dont think root user is bad, but it is against ubuntu-philosophy, and for beginners it is a good idea not to enable root.

---

### Post by anaconda on 2007-09-17
And why do you want to change the permissions of that file?

I wouldnt touch the permissions of any file in the /etc folder. If you need to edit it just use sudo.

---

### Post by mikewhatever on 2007-09-17
> **anaconda said:**
> You can enable root, just give root a password with:
Another temporary solution is to type Ctrl-Alt-F2 and then run 
sudo startx
it will get you to x with root rights. 

And why is it BAD.. I dont think root user is bad, but it is against ubuntu-philosophy, and for beginners it is a good idea not to enable root.

Here is why running as root is bad [http://psychocats.net/ubuntu/security#sudoisnotroot](http://psychocats.net/ubuntu/security#sudoisnotroot)
The reason there are so many wildly propagating viruses in the world of Windows is, at least in part, because the default user account has administrator rights. Most users do not know or care to change it. Do yourself a favour, do not run as root. It's dumb and irresponsible.

---

