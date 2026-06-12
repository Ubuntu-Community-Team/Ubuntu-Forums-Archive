---
title: "[SOLVED] Porblems after running firefox as root."
date: 2008-07-01
forum: General Help
---

### Post by r0b0t1 on 2008-07-01
I doubt this is in the right place, so if someone would be kind enough to report this post and get it moved to the right forum.


So, well, I wanted to use a Java applet which was complaining because it couldn't read/write, so I tried 'sudo firefox' in the Terminal. That didn't work, but what it did was completely screw my firefox installation. I've tried removing it with apt-get from the command line and with synaptic, but it still refuses to work.

Whats actually wrong with it is that it keeps no history, will not back or forward, will not stop loading pages, and does not start at the home page.

Help appreciated :)


Interesting news: I've tried running firefox with sudo again, and it _amazingly_ works. I've modified the icon to be an 'Application run in Terminal', but I hope someone has a more permanent fix. The Terminal window is fairly annoying...

---

### Post by aysiu on 2008-07-01
You should **never** run the command *sudo firefox*. There's really no reason to run Firefox as root, but if you must do so, then use the command *gksudo firefox* instead. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Let's fix the problem, though.

Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username. Then restart Firefox.

---

### Post by r0b0t1 on 2008-07-01
Ok, thank you :).


I didn't know about gksudo after I had read that webpage, so I wouldn't have known. Now its fixed.

---

### Post by acee on 2008-09-30
I was having the exact same problem and this line did not fix it.  This is because I reinstalled firefox-3.0 and my links were still pointing to firefox.

Watch for this!  It's a simple error...so simple it stumped me for a half hour :D

---

### Post by chandrakiran on 2009-07-08
**sudo chown -R username:username /home/username/.mozilla**

Thanks aysiu... Your post fixed my problem.

---

### Post by iGoR83 on 2009-08-11
Solved my problem too. Thank you!

Also the link explaining sudo vs. gksudo was helpful. I'm quite fresh user of Ubuntu and this kind of information will save me from other problems when playing around with Ubuntu :)

---

### Post by michelkogan on 2009-11-28
> **aysiu said:**
> You should **never** run the command *sudo firefox*. There's really no reason to run Firefox as root, but if you must do so, then use the command *gksudo firefox* instead. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Let's fix the problem, though.

Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username. Then restart Firefox.

After I upgrade my ubuntu from 9.04 to 9.10 my firefox runs as root. I just type:
```
firefox
```

and firefox runs as root. I chown .mozila directory in my home folder but still have same problem.

any suggestion ?

---

