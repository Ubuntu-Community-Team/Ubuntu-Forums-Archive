---
title: "shift keys not working"
date: 2020-10-20
forum: General Help
---

### Post by mauroleandro on 2020-10-20
Hi everyone, 
First of all, greetings to all the ubuntu and linux community. Surely my problem is not new, but I haven't been able to solve it by myself. After the last automatic updating in my ubuntu bionic 18.04, the right and left shift keys stop working. Can anybody help me with this issue¿
thanks

---

### Post by T6&amp;sfpER35% on 2020-10-20
weird 
i searched cause i'm curious but could only find [this]("https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Both-Shift-keys-not-working/m-p/6239760#M3145252") , its for windows but i'm sure if you read through it something might give you a clue?

---

### Post by Autodave on 2020-10-20
Is this a laptop or desktop?  Have you tried another keyboard?

---

### Post by Impavidus on 2020-10-20
Can xev detect your keypresses? xev is a small tool you can run from the command line. It shows keyboard and mouse events. It should tell whether the keys aren't detected at all or not mapped to shift.

---

### Post by HermanAB on 2020-10-20
There is a weird bug in X which sometimes make it forget a key or three.

As mentioned above, you can use *xev* to see the key codes, then use *xmodmap* to set the key to itself again.

A little googling will get you going, since many people use the same technique to change the CapsLock key to a Control key.

---

