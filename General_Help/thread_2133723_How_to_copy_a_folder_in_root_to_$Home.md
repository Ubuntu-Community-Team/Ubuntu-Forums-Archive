---
title: "How to copy a folder in /root to $Home"
date: 2013-04-09
forum: General Help
---

### Post by babakflame on 2013-04-09
Dear Buddies
Hi
I have accidentally downloaded a huge file into /root directory that is not accessible for me. Now, I want to move this folder to my home directory. Would u plz help me for the required directive in terminal that does this change? I have changed my access to root by typing [HTML]sudo su -[/HTML]  in terminal.

my current situation is:

[HTML]root@combustion:~# ls
OpenFOAM-2.2.x
root@combustion:~# pwd
/root
root@combustion:~# [/HTML]

I want to move OpenFOAM-2.2.x to my home directory.

   
  Regards
    Bobi

---

### Post by ppjdee on 2013-04-09
Hey, you could try
```
gksudo nautilus
```

I can't test this since my Ubuntu comp is in the bedroom, with my prego gf...and I am to much afraid of waking her :p

---

### Post by babakflame on 2013-04-09
Hi ppjdee
After typing 
[HTML]gksudo nautilus [/HTML]
then what should I do?

I am waitingfor ur gf to wake up and get a complete answer;);)

---

### Post by deadflowr on 2013-04-09
> **ppjdee said:**
> Hey, you could try
```
gksudo nautilus
```

I can't test this since my Ubuntu comp is in the bedroom, with my prego gf...and I am to much afraid of waking her :p

Yes this will start you out in the /root folder.
Simply use 'move to' and move it into your home folder.
Look for the file system menu item and then go to home, then your username folder.

I say move because there is no need at all to have a copy in the root folder.

---

### Post by babakflame on 2013-04-09
Thanks ppjdee and ur gf, also deadflower, I think my probl;em is solved.:guitar:

---

### Post by ppjdee on 2013-04-09
I have been ninja'ed by deadflowr :P

---

