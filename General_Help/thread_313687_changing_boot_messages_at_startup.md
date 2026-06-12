---
title: "changing boot messages at startup"
date: 2006-12-06
forum: General Help
---

### Post by KriC on 2006-12-06
hi there,
i don't wanna bother no-1, but i have a little curiosity i'd like to expose.
In a verbose mode splash screen at boot, there is some way to change the messages returned by the console??
Will explain, when some service starts good, it display an "ok", message, when starts bad display "fail" message.
I'm tired of this, it's too static, i wanted to change that messages.
I don't know, simply from "ok" to "yes" or "done". Got it?
I tried to search the net, but the keyword i type redirect me to forums with problems of bootsplash, usplash or other startup problems.
I don't have problems, i just want to change the messages of the console, that's all.
If someone has just solved this, please, reply me.

bye

[KriC]

p.s.:i got a kubuntu 6.06.1 with usplash (obviously) ;-D

---

### Post by yopnono on 2006-12-06
look in. /etc/init.d there is the boot script.

PS: what? > i don't wanna bother no-1

---

### Post by KriC on 2006-12-06
i taked a look in /etc/init.d but i don't know where is the file i have to search and edit. There's too much files, i'm afraid i can make some disaster, i'd rather prefer to take a good chance with a direct shot.

[KriC]

p.s.: no-1 means noone, or nobody :-| . Tought it was nice to modify it in that way :cool:

---

### Post by yopnono on 2006-12-06
> **KriC said:**
> i taked a look in /etc/init.d but i don't know where is the file i have to search and edit. There's too much files, i'm afraid i can make some disaster, i'd rather prefer to take a good chance with a direct shot.

[KriC]

p.s.: no-1 means noone, or nobody :-| . Tought it was nice to modify it in that way :cool:

Well the files in there are the boot scripts for different things. Just open one by one and check for what you like to change. Make backup of the file/s you change.

hehe I know what it means. I mean. You don't bother anyone. that is what internet and forums are for. Ask and disturb :)

---

