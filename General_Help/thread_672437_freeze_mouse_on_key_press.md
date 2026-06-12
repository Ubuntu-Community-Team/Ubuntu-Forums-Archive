---
title: "freeze mouse on key press"
date: 2008-01-19
forum: General Help
---

### Post by kerheol on 2008-01-19
i don't know why, when i press a key mouse freezes (less than a second, then works again). if i continuously press a key i can't mouse pointer =(

anyone can help me pls?

---

### Post by kerheol on 2008-01-20
if i execute "top" at console and start press keys, nautilius process goes top.. i don't know if this could help

---

### Post by kerheol on 2008-02-05
any help, pls?

---

### Post by FRuMMaGe on 2008-02-11
I have the exact same problem.

Please help us!

---

### Post by apetresc on 2008-02-11
You are probably running the syndaemon. It's a feature, not a bug -- it's meant for trackpads so that you don't accidentally hit the trackpad while typing. With a mouse, though, it's annoying.

Kill the syndaemon process and your problems will be over :)

---

### Post by FRuMMaGe on 2008-02-11
> **AdrianP said:**
> You are probably running the syndaemon. It's a feature, not a bug -- it's meant for trackpads so that you don't accidentally hit the trackpad while typing. With a mouse, though, it's annoying.

Kill the syndaemon process and your problems will be over :)

Close but I have found the reason!

It was so simple!

----------------------------------------

To fix it for the current session, type in the terminal:
```
sudo killall mouseemu
```

----------------------------------------

To fix it permanently, type in the terminal:
```
sudo nano /etc/default/mouseemu
```
Then uncomment the TYPING_BLOCK line and change the 300 to 0 and save it.

Finally
```
sudo /etc/init.d/mouseemu restart
```

---

