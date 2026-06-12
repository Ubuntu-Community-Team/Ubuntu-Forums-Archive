---
title: "Evolution Crash Detection"
date: 2008-05-15
forum: General Help
---

### Post by maitrebart on 2008-05-15
The window appeared empty and then froze over tonite. No way to kill it using the x (upper right corner). xkill did the job though.
I rebooted: same thing.
I wonder if it will start again one day?

Did this happened to one of you before?

(Ubuntu 8.04 LTS)

---

### Post by maitrebart on 2008-05-15
Sometimes the window's content is displayed, but the widgets are dead. Have to xkill it.

---

### Post by maitrebart on 2008-05-15
While looking into the problem, I found .running in ~/.evolution . I deleted it and evolution started, but it greys out after few seconds and stays like that forever.

The left side indicates "Search Folders" and "Loading" under it.

---

### Post by RavanH on 2008-08-31
> **maitrebart said:**
> While looking into the problem, I found .running in ~/.evolution . I deleted it and evolution started, but it greys out after few seconds and stays like that forever.

The left side indicates "Search Folders" and "Loading" under it.

Hi maitrebart,

I have run into exactly the same thing... Have you ever found a way out ? What is causing this hang in Evolution (for which crash detection obviously provides no solution) ?

Thanks for any info.

---

### Post by RavanH on 2008-08-31
> **RavanH said:**
> Hi maitrebart,

I have run into exactly the same thing... Have you ever found a way out ? What is causing this hang in Evolution (for which crash detection obviously provides no solution) ?

Thanks for any info.

UPDATE: I found that when starting Evolution from terminal window, I got this response just before hanging:

```
ravan@packardbell:~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

```

So I opened up the System Monitor and killed all processes starting with 'evolution' including the data server... After that, starting Evolution again went smooth :)

I have the impression that this was caused by having saved my session with Evolution open. Since then, after each login Evolution wanted to start but hung. Strange...

---

