---
title: "NO synaptic or updates"
date: 2008-07-09
forum: General Help
---

### Post by DarknessEnemy on 2008-07-09
Hello and good day/afternoon/night.

I have a problem, I installed medibuntu and tried to install GOogle earth,but came out a screen to accept installation consitions, I didnt knew how to accept (since I dont know how to do it on terminal screen) so I closed it. and now my Synaptic P.M. and updates doesnt work and an error screen comes out:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

What should I do?

Thank you in advance.

---

### Post by Malac on 2008-07-09
> **DarknessEnemy said:**
> Hello and good day/afternoon/night.
 
I have a problem, I installed medibuntu and tried to install GOogle earth,but came out a screen to accept installation consitions, I didnt knew how to accept (since I dont know how to do it on terminal screen) so I closed it. and now my Synaptic P.M. and updates doesnt work and an error screen comes out:
 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
 
What should I do?
 
Thank you in advance.
Open Terminal and run ```
sudo dpkg --configure -a
``` 
this will take some time just answer the defaults to any prompts.
 
Or less drastic try deleting /var/apt/cache/lock and try running ```
sudo apt-get clean
sudo apt-get update
```
This last ones may not work either but are worth a try.
Then try Synaptic
 
Hope this helps.

---

### Post by DarknessEnemy on 2008-07-09
I think that did it! Thanks.

It was pretty fast.

---

### Post by Malac on 2008-07-09
> **DarknessEnemy said:**
> I think that did it! Thanks.

It was pretty fast.
You're welcome. :)

Out of curiosity which one did you try or did you do both?
Plus anyone else coming across this thread would find it useful to know.
And could you mark the thread as solved using the Thread Tools menu at the start of the thread if this has worked.
Thanks.

---

### Post by DarknessEnemy on 2008-07-11
I did the firs one, the second method didn't worked because the directory was nonexistent O.O

Anyway, thanks again ^^.

-Listening: More - Sisters of Mercy-

---

### Post by dexter.deepak on 2008-07-11
the second method didnt work bcoz, the right file is /var/lib/dpkg/lock, try deleting this one.

---

