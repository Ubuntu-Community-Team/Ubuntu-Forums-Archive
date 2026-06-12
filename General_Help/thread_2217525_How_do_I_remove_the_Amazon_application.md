---
title: "How do I remove the Amazon application?"
date: 2014-04-17
forum: General Help
---

### Post by ccmiller12 on 2014-04-17
Anyone know how I can completely remove the Amazon application? I never use Amazon, and don't need that program. I tried typing in the terminal:

```
sudo apt-get remove amazon
```

but it can't locate the package. I'm assuming its the wrong name for the amazon app. What can I type in so that I remove amazon browser.

~Cmiller

---

### Post by bapoumba on 2014-04-17
You should be able to remove it from System> Privacy settings.

---

### Post by m-dw on 2014-04-17
> **ccmiller12 said:**
> Anyone know how I can completely remove the Amazon application? I never use Amazon, and don't need that program. I tried typing in the terminal:

```
sudo apt-get remove amazon
```

I'm assuming its the wrong name for the amazon app. What can I type in so that I remove amazon browser.



Try ```
sudo apt-get remove unity-webapps-amazoncloudreader
```

Or....
```
 sudo apt-get install synaptic
``` 
Then run synaptic (a graphical package manager front-end) and search for amazon

---

### Post by ccmiller12 on 2014-04-17
Thanks for the quick replies. Problem solved; managed to remove amazon app.

Cmiller

---

### Post by slickymaster on 2014-04-17
Can you please share with us the solution you used to solve your problem and at the same time mark this thread as SOLVED, using the Thread Tools in the top right for the effect.

Doing so you will not only benefit who answered your thread letting them know that everything is working but also it will let other people searching the forums know that this thread provides a working solution for their problem.

---

