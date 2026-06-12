---
title: "Difficult ubuntu question"
date: 2008-05-13
forum: General Help
---

### Post by kforum on 2008-05-13
how do i edit/change the priority in which things are loaded when the system start?

for instance, firestarter is set to load at startup, but when it loads it says that the network device is not ready yet, then after a split second it doesn't complain.

now... how do i tell the system that i want it to load a network device -before everything else.
(and im not talking about boot-time loading, just on startup)

tough question, didnt find anyone asking it around the forum.
' how to edit startup priorities ' basically.


also... why do my nvidia server settings reset every time... anything happens?!(screensaver(blank screen), for instance. and some other times).

i feel like im running it over and over all the time.
any clues?


any answers to any of the above questions are well appreciated, thank you.

---

### Post by pointone on 2008-05-14
To clarify: I assume you're talking about services started after logging in to GDM/KDM. For scripts run before the GUI loads, you should look in "/etc/rc#.d/".

Is it not possible for you to simply add a sleep command before starting firestarter? For example, create a simple shell script:

```
#! /bin/bash
sleep 10
/commands/to/start/firestarter
```

...and run this at startup instead of the default program. This should allow enough time for the network to connect.

---

### Post by kforum on 2008-05-14
i looked under rc0.d and a question poped, isnt the network device already loaded as soon as it can be?

also, any clues on teh nvidia question.

---

### Post by kd7lxl on 2008-05-14
> **kforum said:**
> isnt the network device already loaded as soon as it can be?

Yes.

Use the script above.

---

### Post by danwood76 on 2008-05-14
how are you launching firestarter?
As pointone said a simple shell script would solve your issues, where you hook it in depends on how you launch firestarter!

The nvidia thing is a common bug that arises from using a closed source driver.
Go complain to nVidia!

---

