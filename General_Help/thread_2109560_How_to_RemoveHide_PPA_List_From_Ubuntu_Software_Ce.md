---
title: "How to Remove/Hide PPA List From Ubuntu Software Center"
date: 2013-01-27
forum: General Help
---

### Post by mardangga on 2013-01-27
Hello everyone...

I just wanna know, is it possible to hide or remove PPA list or menu from Ubuntu Software Center without remove or disble the PPA itself? So, I still can update my application from those PPA.
I've ask this question on my previous thread: [http://goo.gl/CUUPx]("http://goo.gl/CUUPx"). But, to keep those thread on the right track, I choose to create a new thread for these question. Hopefully I do the right thing :D

Thanks for the attention and sorry about my poor English.

---

### Post by papibe on 2013-01-27
Hi mardangga.

Uncheck the ppa in question here:
```
Software Center -> Edit -> Software Sources -> Other Software (tab)
```
It may take a few seconds to take effect on the Software Center.

Let us know how it goes.
Regards

---

### Post by mardangga on 2013-01-28
> **papibe said:**
> Hi mardangga.

Uncheck the ppa in question here:
```
Software Center -> Edit -> Software Sources -> Other Software (tab)
```
It may take a few seconds to take effect on the Software Center.

Let us know how it goes.
Regards

Thanks for the answer. But if I do this, do I still get an update (if available) from these PPA?? :D

---

### Post by claracc on 2013-01-28
> **mardangga said:**
> Thanks for the answer. But if I do this, do I still get an update (if available) from these PPA?? :D

No, you won't get updates from these ppas since they are uncheched in software sources. To get the updates, you have to check them again and run ```
sudo apt-get update
```

---

### Post by mardangga on 2013-01-28
> **claracc said:**
> No, you won't get updates from these ppas since they are uncheched in software sources. To get the updates, you have to check them again and run ```
sudo apt-get update
```

So, that's mean we can't hide or remove PPAs from Ubuntu Software Center menus without remove or disable those PPAs. Am I right??

---

### Post by claracc on 2013-01-28
> **mardangga said:**
> So, that's mean we can't hide or remove PPAs from Ubuntu Software Center menus without remove or disable those PPAs. Am I right??

Yes, I think so.

---

### Post by mardangga on 2013-01-30
> **claracc said:**
> Yes, I think so.

Should I mark this thread as "Solve" with a conclusion that we can remove or hide PPAs from Ubuntu Software Center without remove or disable those PPAs??
Or should I keep this thread as Unsolve, so maybe someone can give another solution??
I know, my question in this thread is not really important. I just wanna know, if it possible or not.

Thanks for the attention and sorry about my poor English.

---

