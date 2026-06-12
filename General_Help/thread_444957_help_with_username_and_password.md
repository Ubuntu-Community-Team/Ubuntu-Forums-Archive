---
title: "help with username and password"
date: 2007-05-15
forum: General Help
---

### Post by spangltk on 2007-05-15
I ran wubi last night on my computer, it started downloading and I walked a way.  A few hours I came back restarted and selected ubuntu on the boot screen.  It started installing ubuntu and I walked away again.  I came back later to a red screen saying my login name wan incorrect because of a certain char.  I looked at what it said was my user name and it said Foo Bar, which is my user name for my XP machine.  I thought it might have been the space inbetween the two words making it invalid so I changed it to "spangltk" and it seemed to have fixed the problem and I left again.  

I came to it this morning and it was on the windows login screen, I rebooted it, selected ubuntu and now I can't log into it.  I've tried all the passwords I know it could have picked of the XP I've also tried nothing and blank spaces as passwords.  Do i have to resort to a re-install?
thanks

---

### Post by heimo on 2007-05-15
Reboot - select revocery mode in boot menu (grub menu), and use passwd to change your password.
```
passwd spangltk
```

---

### Post by logan1441 on 2007-05-19
how do i open the grub menu?? sorry im really a newbie @ this

---

### Post by logan1441 on 2007-05-19
like if its where you reboot and it asks you which operating system, i have that but theres no recovery mode

---

### Post by heimo on 2007-05-19
At the beginning of boot process - when your computer starts - there's should be grub menu, and if it's not there, you could hit ESC couple times at the correct moment to enter it. If you see something flashing on the screen about grub - hit ESC.

---

### Post by heimo on 2007-05-19
> **logan1441 said:**
> like if its where you reboot and it asks you which operating system, i have that but theres no recovery mode

Ok. Then there is probably some way of doing this in Live-CD too. I'll try to figure it out and I'll write back.

---

### Post by logan1441 on 2007-05-19
when installing, i get this thing like apt-get something or other failed. it then says i dont even have the apt-get program.

---

### Post by heimo on 2007-05-19
EDIT: Oh - Now I see that you're not the original poster. And these instructions were written like if you were.

Ok, untested instructions which should do it, but may still contain errors:[LIST]
[*]Boot from your install / Live-CD.
[*]open a terminal window
[*]sudo fdisk -l
[*]you'll get a list of partitions, see which one is your Ubuntu root partition (should be one "Linux" under system column), see what's the "device" on that one
[*]sudo mkdir root
[*]sudo mount /dev/sda1 root (use the /dev/ from the fdsik -l output above)
[*]sudo chroot root
[*]sudo passwd spangltk
[*]give new password twice, close terminal, reboot to your Ubuntu[/LIST]

---

### Post by heimo on 2007-05-19
> **logan1441 said:**
> when installing, i get this thing like apt-get something or other failed. it then says i dont even have the apt-get program.

Please open a new thread for your question. It's very confusing when people jump into threads with their questions.

---

### Post by logan1441 on 2007-05-19
ok i did:
[http://ubuntuforums.org/showthread.p...46#post2683146](http://ubuntuforums.org/showthread.p...46#post2683146)

---

### Post by logan1441 on 2007-05-19
ok i did:
[http://ubuntuforums.org/showthread.php?p=2683146#post2683146](http://ubuntuforums.org/showthread.php?p=2683146#post2683146)

---

