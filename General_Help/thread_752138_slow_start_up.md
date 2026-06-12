---
title: "slow start up"
date: 2008-04-11
forum: General Help
---

### Post by morphis on 2008-04-11
Hello, first of all I have to apologize for my really bad english.

That's my problem, 
  after the login procedure the system needs approximately 5 to 7 minutes in order to become functional. 
But, the really weird thing is that my hdd is not running at full load but with spaces, that is a few desktop icons are opened, then for a minute nothing, then smth else and that's stands for several minutes.
  I checked if there are processes that may be responsible for that , but i found nothing.

  Moreover, after this malfunction the whole system has a bad response time( when i open the terminal, programms or folders ).

Can anyone help me, because i dont know from where to start. Thank you


P.S: That day, when this start to happen i had installed mysql, virtualbox, ntok(as I can remember), which after that i removed them

---

### Post by ajgreeny on 2008-04-11
Did your system start up in a more normal time scale previously?  It sounds as if that was so from your post.  Try renaming your current .gconf folder as .gconf.old (it is hidden, so press Ctrl+h to see hidden folders and files) and then login again.  A new .gconf will be made and some of your settings will change for the time being, but it will at least let you know if anything other than the gnome desktop is to blame.  You could also make a new user to see if that starts quickly.

Post back anything that happens when you try these two things and we'll see if we can get back to where you should be.

---

### Post by morphis on 2008-04-11
> **ajgreeny said:**
> Did your system start up in a more normal time scale previously?  It sounds as if that was so from your post.  Try renaming your current .gconf folder as .gconf.old (it is hidden, so press Ctrl+h to see hidden folders and files) and then login again.  A new .gconf will be made and some of your settings will change for the time being, but it will at least let you know if anything other than the gnome desktop is to blame.  You could also make a new user to see if that starts quickly.

Post back anything that happens when you try these two things and we'll see if we can get back to where you should be.


Thank you for your quick response.:)

Yes, that happened suddenly one day. Before this everything was ok, and my system was really fast.

I will try what you suggested me, and I will post if there was an improvement.

:KS

---

### Post by morphis on 2008-04-11
Hello,
I'm really happy because I created a new user and everything is fine. also I changed the .gconf folder and my system has the functionallity that had once.

  My question is that finally the problem is gnome or sth else in my settings. The new .gconf folder that automatically created by the system has anything different than the old one, I mean that there are only desktop settings or sth more vital.

  Thank you very much for your answer

---

### Post by morphis on 2008-04-11
And sth else,

what can I do so as not to happen again sth like this?

thank you!

---

### Post by ajgreeny on 2008-04-11
Sorry, but I don't think I can answer your question, but I am glad that everything is back to full speed.  Just change your gnome settings back to what you want, but do it one thing at a time and then you will know what it was that upset everything last time.

---

### Post by morphis on 2008-04-15
Thank you

---

