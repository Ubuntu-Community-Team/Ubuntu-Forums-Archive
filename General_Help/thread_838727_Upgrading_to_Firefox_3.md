---
title: "Upgrading to Firefox 3"
date: 2008-06-23
forum: General Help
---

### Post by LostLake on 2008-06-23
I just installed Firefox 3 but when I run Firefox, Firefox 2 opens. Any Advice?

Thanks

---

### Post by geraldm on 2008-06-23
You may have two different versions of firefox installed.  
From the top directory where you installed firefox-3.0 enter the command
```

./firefox --version

```
You can also check the other executable for its version.  Then set each up in whatever way you want to start the executable.

Gerald

---

### Post by scotcella on 2008-06-23
Did you uninstall Firefox 2 properly?

Then removed the .mozilla folder from your home directory?

THEN installing firefox 3?

In that order?

I had the same problem, this is how I got it solved.

---

### Post by scotcella on 2008-06-23
And of course..  

what version of Ubuntu are you using? I'm assuming it's not Hardy as Hardy comes with FF3 in it.

---

### Post by maheshasolkar on 2008-06-23
> **scotcella said:**
> 
Then removed the .mozilla folder from your home directory?


I would backup my .mozilla folder before I delete it. It has my profiles.

When I upgraded from Firefox 2 to Firefox 3, it automatically upgraded my profiles. Although, if you use some extensions that don't play well with the new version of Firefox, that my not happen. In which case you might want to start afresh - by deleting .mozilla directory.

For what its worth...

---

### Post by scotcella on 2008-06-23
Oops, forgot to add that...  thanks maheshasolkar

---

