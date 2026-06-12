---
title: "bash: apt-get command not found"
date: 2005-05-19
forum: General Help
---

### Post by void_false on 2005-05-19
After restoring my[crashed Ubuntu](http://ubuntuforums.org/showthread.php?t=35257) I got some issues.
Xorg says it cant find some font: unix007 or smtng similar. Gnome boots OK but some icons are missing. 
But the worst problem is that apt-get gone!  ](*,) Bash cant find this command although "man apt-get" and "apt-cache" works.
Plz tell me how can I get back apt-get package so I can reinstall xorg and kde-core.

---

### Post by sonny on 2005-05-19
There's two ways I can see, the first one; and the one I'd prefer, re-install (k)ubuntu. If you did a good install then your /home folder should be on antoher partition, and the / folder in another one, so put your (k)ubuntu cd in the cd-rom and reboot, if you don't have the boot from cd feature then enable it via your bios, when the installation  ask you about your disk say you'll mange it, then make it to format your / partition and to keep the files in you're /home, by selecting each partition and told it to do so. I prefer this one cuz it makes the system cleaner and as you had problems by speeding up your HD I think this would be better, because all the problems not founded by knnopix will be fix, you have to remember to backup all your files you've modified (xorg.conf, smb.conf, sources.list, etc).

If you don't have your /home in a separate partition then, download the apt-get library from the ubuntu source [here](http://packages.ubuntu.com/hoary/) and see if you can install it manually.

Good luck.

---

### Post by void_false on 2005-05-19
Thx m8. Now gonna try to reinstall apt.

---

### Post by void_false on 2005-05-19
OK. After fixing apt dpkg I used Gnome to repair rest of my system. Now it's running fine. Oh... I'm feeling so 1337... I'm ub3r l33t h4x0r!   :)  :)  :) 

Maybe I should stick with Gnome? He survived the crash?  ;-) 
Blah, sound quality in Totem sux. Installing KDE.  \\:D/ 

THX everyone for help.

---

### Post by void_false on 2005-05-19
...but here comes problem  :neutral: I cant log in into gnome as non-root. It says that it has no permission to write in /home although /home has permission 755. I tried to change it to 777 - same result.

---

### Post by derrick1985 on 2005-05-19
[QUOTE=void_false]...but here comes problem  :neutral: I cant log in into gnome as non-root. It says that it has no permission to write in /home although /home has permission 755. I tried to change it to 777 - same result.[/QUOTE]

you should just write own's for the directories:

EX. your user is joe

sudo chown joe:joe /home/joe

---

### Post by void_false on 2005-05-19
Same thing. I'm getting this message:
> 
GDM couldnt write to your authorization file. THis could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator.


---

### Post by void_false on 2005-05-19
Hello?

What is the authorization file, that GDM writes something into it on logon?

---

### Post by sonny on 2005-05-19
I'm guessing it's the .ICEauthority file, you should enter in console mode, and type:

$ cd /home/"your-user-name"
$ sudo chmod 775 .ICEauthority

Do that and tell us what happened... cuz I'm not so sure if that is the file the message  is talking about.

Good Luck

---

### Post by void_false on 2005-05-19
[QUOTE=sonny]I'm guessing it's the .ICEauthority file, you should enter in console mode, and type:

$ cd /home/"your-user-name"
$ sudo chmod 775 .ICEauthority

Do that and tell us what happened... cuz I'm not so sure if that is the file the message  is talking about.

Good Luck[/QUOTE]

Nope. Same message. Strangt.  :neutral:

---

### Post by sonny on 2005-05-19
I guess the only solution would be to add another user, and then copy and paste all your old files to your new account, unless one of the grand linux masters wandering around says otherwise.

---

### Post by void_false on 2005-05-19
When adding new user it complaints about permission to /tmp. :|
All those things are very strange to me. System works just perfect exept the non-root user issue.

---

### Post by void_false on 2005-05-19
OK thx everybody for help - all my problems are solved.  :D
I've changed /tmp ownership from root to my username. Now system works like a charm.  :-P Even better than before crash.
I restored my system from ashes.... I'm leet... I'm ub3r 1337 h4x0r!!111 

j/k :-P

---

