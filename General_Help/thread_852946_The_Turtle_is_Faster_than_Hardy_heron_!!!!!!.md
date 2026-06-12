---
title: "The Turtle is Faster than Hardy heron !!!!!!"
date: 2008-07-08
forum: General Help
---

### Post by Uchiha_madara on 2008-07-08
Hi Every one ...

I have Installed ubuntu Hardy for 3 months....

it was very cool and wonderfull and i like it

But in The Last days , ubuntu was very very slow sometimes i say ubuntu dies ,so how can i fix this slow of ubuntu:confused:


thank u

---

### Post by hyper_ch on 2008-07-08
well, you don't really give any information about what is slow and and and...

so being equally vague I can say that faster cpus and more ram normally speed up... but I guess that's not what you're looking for. Hence you need to be more specific.

---

### Post by p_quarles on 2008-07-08
Like hyper_ch says, we need some more specifics before we can help.

If performance is overall sluggish, you should look into what is eating system resources. Open the system monitor and see what is using the most RAM and CPU time.

---

### Post by Uchiha_madara on 2008-07-08
When I Open more than two application the Ubuntu seems to be deadLocked without any reason ...


For example win i open the Word processor and FireFox

This is The Problem

---

### Post by Uchiha_madara on 2008-07-08
When I Open more than two application the Ubuntu seems to be deadLocked without any reason ...


For example win i open the Word processor and FireFox
or pidgin messenger or FireFox ,.... or any Two Application togather
This is The Problem

---

### Post by hyper_ch on 2008-07-08
open a terminal, run
```

sudo apt-get install htop

```
then run
```

htop

```

and see how much ram you have left, what process uses how much cpu....

---

### Post by Uchiha_madara on 2008-07-08
> **p_quarles said:**
>  Open the system monitor and see what is using the most RAM and CPU time.


What is The Processors are for The System

to Avoid Killing them ??????

---

### Post by p_quarles on 2008-07-08
> **Uchiha_madara said:**
> What is The Processors are for The System

to Avoid Killing them ??????
For now, you could just let us know what's taking up the most power, and worry about killing processes later.

That said, this may be the hard lockup bug that I've heard some people talk about with 8.04. I haven't experienced it myself, so I'm not sure what to do about it.

---

