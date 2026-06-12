---
title: "[SOLVED] Update Manager issue"
date: 2008-05-14
forum: General Help
---

### Post by meazz1 on 2008-05-14
I am not sure why but my update manager has these updates but I am not able to check any of them. When there's new updates, I have the option to put check marks, or when I do Check all, these don't get checked.

Any idea?

[IMG]http://img108.imageshack.us/img108/9919/screenshotupdatemanagerle8.png[/IMG]

---

### Post by chrisccoulson on 2008-05-14
Strange. At a guess, I'd say they were being held back due to missing dependencies. Could you post your /etc/apt/sources.list?

---

### Post by pointone on 2008-05-14
I notice they're all updates from the medibuntu repository...

---

### Post by meazz1 on 2008-05-14
> **pointone said:**
> I notice they're all updates from the medibuntu repository...

Now that you mention this, I remember that I checked and enabled one mediabuntu repository.

So what do I do now to fix this, apparently these are the pending updates?

---

### Post by chrisccoulson on 2008-05-14
You can uncheck them in System -> Administration -> Software Sources. Click on the 'Third Party Software' tab.

---

### Post by meazz1 on 2008-05-14
> **chrisccoulson said:**
> You can uncheck them in System -> Administration -> Software Sources. Click on the 'Third Party Software' tab.

By unchecking, do I miss anything in the future, like any critical updates top that application?

---

### Post by chrisccoulson on 2008-05-14
You will miss out on updates to anything installed from Medibuntu. I'm still confused about the problem you're having though. Could you post your /etc/apt/sources.list? I'm just wondering if you're accidentally using the Hardy Medibuntu repositories on a Gutsy install. This might cause this

---

### Post by meazz1 on 2008-05-14
> **chrisccoulson said:**
> You will miss out on updates to anything installed from Medibuntu. I'm still confused about the problem you're having though. Could you post your /etc/apt/sources.list? I'm just wondering if you're accidentally using the Hardy Medibuntu repositories on a Gutsy install. This might cause this

I will as soon i get home from work.

---

### Post by meazz1 on 2008-05-14
> **chrisccoulson said:**
> You will miss out on updates to anything installed from Medibuntu. I'm still confused about the problem you're having though. Could you post your /etc/apt/sources.list? I'm just wondering if you're accidentally using the Hardy Medibuntu repositories on a Gutsy install. This might cause this

You all are just geeks....(lol)
yes, there were 2 Hardy repositories in the list. I commented them out and problem resolved.

---

### Post by chrisccoulson on 2008-05-15
Glad it's sorted now:)

---

