---
title: "Need help with Admin rights to a folder!"
date: 2007-10-17
forum: General Help
---

### Post by zyberican on 2007-10-17
Hello everyone!
I finally made the change to Linux and like it a lot.
I got a calendar program called: Raincalendar and everytime I try to move the program folder into etc/opt/ I get a message saying that I do not have permission to the folder. 

The account I have is and Adminstrator account and I still cannot move the raincalendar folder into the etc/opt/ folder. 

I wanted to know if there's a way to move the folder I have on my desktop into the etc/opt/ folder?

Thanks in advance for any help!:confused:

---

### Post by 505 on 2007-10-17
Ubuntu does not have an real admin account, instead, you have to type your password for admin tasks. If you really want to move the program to that folder you have a couple of options.

1. Move the files in true admin mode. Press alt+F2 and type 'gksu nautilus' in the screen you can move the files. Be careful, because you can do anything in this screen, even delete all files.
2. A bit safe is to move the files in terminal mode. Click Applications, Accessories, Terminal. If you want to move  a whole directory, go to the parent directory using 'cd folder name'. The type 'sudo mv foldername/ /etc/opt'
3. Give yourself right to the opt folder without admin rights. Open a terminal and type 'sudo chown username:username /etc/opt' (substitute username for your own login name)

---

### Post by PmDematagoda on 2007-10-17
The thing about Linux is that certain important tasks such as make install can only be done in root mode which can be initiated for that specific task by appending the command with "sudo", but if you want the whole terminal session to be in root mode, you can start it up using:
```

sudo -i

```
The thing about sudo is that it is very powerful and it is very dangerous as any task with these powers can change the very core of the system, so be careful about issuing these powers to an untrusted application or task as you could break your system in that process.

---

### Post by zyberican on 2007-10-17
Thanks a million guys!!!
It all worked out!!

It's nice to be part of a knowledgeable community!

---

