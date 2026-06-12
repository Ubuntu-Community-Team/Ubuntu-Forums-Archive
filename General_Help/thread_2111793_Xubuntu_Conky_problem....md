---
title: "Xubuntu Conky problem..."
date: 2013-02-02
forum: General Help
---

### Post by joemartin on 2013-02-02
On login/startup my Conky config loads five times.  

I then have to close four of the five windows manually.

Loaded in startup applications once.  

Any ideas on how I can fix this?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2013-02-02
try putting a few seconds of sleep before it starts 
where you have it in startup apps make it run
```
sh -c 'sleep 4;conky'
```
make sure session restore is set to never restore conky

---

### Post by joemartin on 2013-02-02
Unfortunately, that was not the solution.

Any other ideas would be appreciated.

---

### Post by QIII on 2013-02-02
When you logout or shut down, do you save the current session and then have conky in your startup?

---

### Post by joemartin on 2013-02-02
No..

I never resume previous session....

---

### Post by joemartin on 2013-02-02
But Conky is in my startup applications...

---

### Post by QIII on 2013-02-02
What happens if you take it out?

---

### Post by joemartin on 2013-02-03
unticked Conky box in startup applications, logged out, then back in.  Five Conky's still loaded at login.

Strange.

---

### Post by Toz on 2013-02-03
Clear out your saved sessions cache:
```
cd $HOME/.cache
rm -rf sessions
```

Make sure conky in Application Autostart is ticked.

---

### Post by joemartin on 2013-02-03
Thank you Toz!

That did it.

Your knowledge is appreciated.

---

