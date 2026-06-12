---
title: "Ubuntu Slow"
date: 2007-08-13
forum: General Help
---

### Post by Warjo on 2007-08-13
Hello! :)
New ubuntu user here!

I got a slite problem here ppl.
Thing is my ubuntu is getting slow. I used to have beryl but changed that to Compiz Fusion. On beryl i was slow. Now on CF things god much better.
Now, when logging into ubuntu everything goes fine, BUT* when using some desktop effects everything gets slow!!
I am typing "top" in console ( i found that out somewhere in ubuntu forums :p) and i notice that my memory is eaten up and like 100-50mb of ram remain free.

My computer specs are :

Intel Celeron 2.4GHZ
RAM: 1.512 DDR RAM 2x512 - 2x256
nVidia GeForce 6600GT

Also i would like to include that on ubuntu installation i didnt define any swap space as suggested cause thought my ram is enough. Just mentioning this in case has anything to do with this.

Waiting for your reply :)
Please dont let me get back to that crappy Vista :((

---

### Post by Warjo on 2007-08-13
Wrong Section? :(

---

### Post by eentonig on 2007-08-13
CF and Beryl are indeed possible reason for slowing down your GUI. But then, it's alpha software. As in, 'prepare for problems'.

On my machine (2.4Ghz, 2G RAM, 2G Swap, Intel GPU), swap isn't used. But I also notice that CF sometimes gets really ressource hungry.

---

### Post by Warjo on 2007-08-13
Thing is this happens all the time. Not sometimes. But some others are having smooth interfaces. I think there's something wrong there :/ i would like to figure this out

Thanks for your reply :)

---

### Post by ddrichardson on 2007-08-13
There's nothing essentially wrong with allmost all RAM being used - that's there by design (UNIX philosophy is that unused RAM is wasted RAM). What does top show as using the most processor time?

---

### Post by Warjo on 2007-08-13
Processor wont exceed using 1% rofl that's weird also only ram is eaten up :(

---

### Post by Blindraven on 2007-08-13
How much swap are you using?

---

### Post by Warjo on 2007-08-13
no swap partition defined. i just have my whole WD 40gb HD formated into ext3 to install ubuntu. No swap partition, any clues ? o.O

---

### Post by Warjo on 2007-08-13
i just read somewhere that partition is needed in order for the linux to store unusefull data instead of memory. So i guess tha could be it. No swap partition Right?

---

### Post by ddrichardson on 2007-08-13
Yep, I'd put in a swap partition - you can run without one but it leaves no where to page. Lack of swap file usually just stops apps running at all though,

---

### Post by Warjo on 2007-08-13
arhm that must be it cause some times i face firefox closing suddenly :)
Very thank you i will try this when i get back home and paste results here

Thnx again :))

---

### Post by Warjo on 2007-08-14
No that didnt really brought any results :/ Dont know what's happening really there. I get my ram filled up and everything goes slow then
Not so slow but you can notice that interface is not as smooth as it was

So any ideas? I would much appreciate :)

---

