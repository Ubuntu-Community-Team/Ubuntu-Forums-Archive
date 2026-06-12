---
title: "CPU idles at 10-20% constantly"
date: 2008-06-22
forum: General Help
---

### Post by waapwoop1 on 2008-06-22
I have a compaq n610c laptop. So does the guy sitting next to me.

My resources graphic shows my CPU is running at 10-20% depending on when 'm looking at it, with no apps open. I check the processes tab and it says the "gnome system monitor" is the only thing running, at around 4-8% and nothing else
Firstly this doesn't match at all.
I am running Ubuntu 8.04, my friend with the same laptop, same specs etc is running XP Home and his cpu sits at around 3%.  His laptop seems a bit cooler than mine too, haven't measured it.

His XP home boots twice as fast too.  What is going on.

---

### Post by macaholic on 2008-06-22
Is the same output given when you run top from a terminal? Sometime there are discrepancies between the two.

---

### Post by waapwoop1 on 2008-06-22
how do i do that?

---

### Post by macaholic on 2008-06-22
Applications > Accesories > Terminal (on gnome) and type top and hit enter.

---

### Post by sdennie on 2008-06-22
Using the gnome system monitor won't get you accurate results.  The sticky at the top of this forum has the bug listed.  The best workaround is to use top or htop.  As macaholic said, you just open a terminal and type top.  To use htop instead, try:

```

sudo apt-get install htop

```

Then

```

htop

```

---

### Post by waapwoop1 on 2008-06-22
Ok, cool, you guys are right.

Funny thing was, when i had teh resource thingy open, top said it was running at 10-11%.... with the resource monitor closed it went to 1.3%

I guess that is where the anomally is, the resource monitor increases the cpu by quite a lot.

---

