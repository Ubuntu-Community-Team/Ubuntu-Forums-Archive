---
title: "Suspend/Hibernate doesn't work."
date: 2008-06-08
forum: General Help
---

### Post by Berethend on 2008-06-08
Hopefully someone can help me with my problem. I am running 8.04 on an older Compaq Presario laptop. I am quite new to Ubuntu so please make an explanation as simple as possible :) Whenever I try and put my computer into suspend/hibernate mode it goes into it just fine but as soon as I press a key or touch my mouse to wake it back up, it boots back up but the screen is black and it's as though nothing happened. I have no way to shutdown the computer from this point except to hold the power button and start again. I've read about similar problems to mine about how suspend/hibernate doesn't work in 8.04 but I haven't found any solutions. Any help would be great.

---

### Post by Pjotr123 on 2008-06-08
This info will clarify things:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 4 )

---

### Post by Berethend on 2008-06-08
So my only options are to wait until July 10th or do a complete reinstall?

---

### Post by drs305 on 2008-06-08
I am exploring an issue I've seen a couple of places in which a user's swap file is either too small or not even active. 

Please run and post the following to show what is happening with your swap file:
```
free
```

Suspend/hibernate is a known problem on some machines, so don't get your hopes up with this post :-)

---

### Post by Pjotr123 on 2008-06-08
Why reinstall? That won't help...

And I hope that this will be fixed by the updates, but I'm not sure. It's the number one complaint on the Ubuntu Brainstorm:
[http://brainstorm.ubuntu.com/most_popular_ever/](http://brainstorm.ubuntu.com/most_popular_ever/)

---

