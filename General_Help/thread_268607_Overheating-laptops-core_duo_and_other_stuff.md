---
title: "Overheating-laptops-core duo and other stuff"
date: 2006-09-30
forum: General Help
---

### Post by Fred Doolie on 2006-09-30
I'm getting a Dell E1505 in a few weeks and have been reading all the overheating problems with Ubuntu and using only one cpu and so on. Here's a suggestion and what I'm going to do unless somebody knows this won't work.

If you don't really need the full graphic and sound power of your laptop (IE: no games and multimedia why not run Ubuntu in a virtual system (vmware)simulating a single CPU system?

That way Winblows is still controlling the hardware. The CPUs, fans and whatever will be monitored and controlled by software that was designed for that job. You'll still have the media center and all the other stuff too.

Dumb idea?

---

### Post by 23meg on 2006-09-30
Windows will keep acting under covers. Apps will call home without your consent and send confidental data, and other similar nastiness reserved to commercial closed source OSes will persist.

---

### Post by got_nix on 2006-09-30
i use gkrellm and the i8kutils plugin for dell systems i have a inspiron 6400 which is practically the same as what your gonna be getting.system never gets too hot.. you have manual controlls of the fans or you can let em run on automatic if you want. my processor generally doesn't go over 40C

---

### Post by David Corrales on 2006-09-30
> **got_nix said:**
> i use gkrellm and the i8kutils plugin for dell systems i have a inspiron 6400 which is practically the same as what your gonna be getting.system never gets too hot.. you have manual controlls of the fans or you can let em run on automatic if you want. my processor generally doesn't go over 40C

I do exactly the same. I cut all options except fans and use the transparent theme. Looks great actually :)

---

### Post by Fred Doolie on 2006-10-01
> **got_nix said:**
> i use gkrellm and the i8kutils plugin

system never gets too hot.. you have manual controlls of the fans


That's good to know. Those posts concerned me. I paraphrase:

"Under Ubuntu only one of the two cpus runs and that causes massive over heating and damage"
"With Windows the fans run and everything stays cool. With Ubuntu the fans never come on and my system overheated and fried everything"
"Ubuntu causes core duo cpus to overheat and burn out"

Those are paraphrases from various places around the net. If you have a working Ubuntu on a core duo with running fans, PLEASE post "Dell Core Duo Ubuntu Install And Get The Hardware Working For Dummies" for me and perhaps those others too.   

Did you get all the fancy hardware to work too? That's why (even though I hate it) I was going to keep Winblows. Well, that and it  likely added $100 to the price of the computer.

---

### Post by andiii on 2006-10-01
> **Fred Doolie said:**
> 
Those are paraphrases from various places around the net. If you have a working Ubuntu on a core duo with running fans, PLEASE post "Dell Core Duo Ubuntu Install And Get The Hardware Working For Dummies" for me and perhaps those others too.   

Did you get all the fancy hardware to work too? That's why (even though I hate it) I was going to keep Winblows. Well, that and it  likely added $100 to the price of the computer.
Core Duo is running here. You need the 686 (smp) kernel.

Fancy Hardware? he function keys (volume, brightness) just worked.

---

### Post by JamesB on 2006-10-01
I'm running dapper with 686 kernel and edgy with generic kernel on an asus a8j with intel duo, and i've had no problems, bar nvidia graphix, but thats now sorted, in dapper anyway, edgy's another story, ha ha.
From what I've read it been mainly ppc or compaq laptops... may be wrong thou....

---

### Post by Fred Doolie on 2006-10-02
> **andiii said:**
> Core Duo is running here. You need the 686 (smp) kernel.

Fancy Hardware? he function keys (volume, brightness) just worked.

Automatic fan speed control. Automatic throttle-down on the CPU as the battery dies. Multimedia playback controls on front without having to boot an OS. Auto hybernate when you close the lid. There's a lot more stuff the E1505 does. I meant that fancy hardware.

---

