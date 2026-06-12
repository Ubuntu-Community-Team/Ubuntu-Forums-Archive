---
title: "Easy tuning for P4 cpu"
date: 2007-07-17
forum: General Help
---

### Post by eentonig on 2007-07-17
I was running the latest linux-image-generic for Feisty fawn. But I noticed that my system was a bit sluggish.

After a few weeks of hunting down what could be the cause of this, I stumbled upon a post that mentioned that some P4 architectures are slow running on the generic kernel and better of running a "-386" image.

so I just did install the latest -386 kernel and I'm impressed on the speed.I gained.
So, if anybody else is running the same architecture, this is a step you might concider.

> rfonteyn@gauloises:~$ uname -a
Linux gauloises 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

---

### Post by zanglang on 2007-07-17
Interesting... I used to think there aren't that much differences in -generic and -386. Can you post some benchmarks (e.g. bootchart)?

---

### Post by eentonig on 2007-07-17
I'll have to check my bootchart differences. But I had the impression that the bootprocess wasn't that different.

With the generic, I had an average boot off 40" So that wasn't bad. It was during general usage that I experienced slowness.

The only 'suspicious' process I could ever find, was xorg. This way generally using between 10% and 40% CPU. This morning, this seemed to be much lower with the 386 kernel. But I'll have to check more thoroughly.

---

