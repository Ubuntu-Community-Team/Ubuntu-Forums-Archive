---
title: "Accidentally deleted home directory. :/"
date: 2007-03-25
forum: General Help
---

### Post by sharkbaitbobby2 on 2007-03-25
I accidentally deleted my home directory. There is only one user. As soon as that happened, everything froze (including the cursor), so I did Ctrl-Alt-Backspace and got back to the greeter. I entered my name and password, and it alerted with saying a file in $HOME is being ignored or something like that. Basically, after cd'ing to /home (in the terminal (Ctrl-Alt-F1)), I tried to cd to matt (my username), but it could not be found. /home/matt has been deleted, and of course along with all the files in it. I have some pretty valuable source code on my hard drive (not in /home/matt), so I have two questions:

Is there a way to somehow get a /home/matt directory there along with all the files that are needed, (I didn't really have any valuable data there) without reinstalling? And if not, then how can I somehow copy the code in one directory to a flash drive (or somehow back it up)?

I know how to switch from X and the terminal and stuff, but I am not an expert at commands.
I can reinstall, no big deal, but either way I need to get that source code backed up somehow.
Please help. :)

---

### Post by user1397 on 2007-03-25
> **sharkbaitbobby2 said:**
> I accidentally deleted my home directory. There is only one user. As soon as that happened, everything froze (including the cursor), so I did Ctrl-Alt-Backspace and got back to the greeter. I entered my name and password, and it alerted with saying a file in $HOME is being ignored or something like that. Basically, after cd'ing to /home (in the terminal (Ctrl-Alt-F1)), I tried to cd to matt (my username), but it could not be found. /home/matt has been deleted, and of course along with all the files in it. I have some pretty valuable source code on my hard drive (not in /home/matt), so I have two questions:

Is there a way to somehow get a /home/matt directory there along with all the files that are needed, (I didn't really have any valuable data there) without reinstalling? And if not, then how can I somehow copy the code in one directory to a flash drive (or somehow back it up)?

I know how to switch from X and the terminal and stuff, but I am not an expert at commands.
I can reinstall, no big deal, but either way I need to get that source code backed up somehow.
Please help. :)try restarting, and in the grub boot menu, select the recovery option.  this will take you to a root terminal.  in there, type:
```
useradd *username*
```of course changing username to whatever login name you desire.

---

### Post by flyboy_2003 on 2007-03-25
> **ubuntuman001 said:**
> try restarting, and in the grub boot menu, select the recovery option.  this will take you to a root terminal.  in there, type:
```
useradd *username*
```of course changing username to whatever login name you desire.

Actually, you want to add the -m switch to the useradd command

You don't have to reboot either. You can do the CTRL + ALT + F1 and then

$ sudo useradd -m username
$ sudo passwd username

You can now log in as username. 

Cheers.

---

