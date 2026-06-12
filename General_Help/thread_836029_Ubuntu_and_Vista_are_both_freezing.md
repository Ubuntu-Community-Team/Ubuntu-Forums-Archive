---
title: "Ubuntu and Vista are both freezing?"
date: 2008-06-21
forum: General Help
---

### Post by donniezazen on 2008-06-21
Ubuntu and Vista are both freezing at startup and while running or whenever they can? First mouse stops moving then it freezes. sometime it starts working after a while but most of time i have to  restart it(by pressing power button). I have Dell E1505/6400. This has got very annoying guys please help.

---

### Post by hal8000 on 2008-06-21
Its unusual for two Operating Systems to suffer from the same symptoms. Because they are both freezing you may be looking at either bad memory or overheating.

Easy things you can do, unplug the system remove the case, and vacuum all ventilation slots, fans, and air intakes. Perhaps use compressed air spray near the CPU. I've seen systems power up and reboot in 30 seconds, all because of a highly blocked fan.

If that doesnt help, try unplugging and reseating each memory stick.

---

### Post by VMC on 2008-06-21
> **hal8000 said:**
> Its unusual for two Operating Systems to suffer from the same symptoms. Because they are both freezing you may be looking at either bad memory or overheating.

Easy things you can do, unplug the system remove the case, and vacuum all ventilation slots, fans, and air intakes. Perhaps use compressed air spray near the CPU. I've seen systems power up and reboot in 30 seconds, all because of a highly blocked fan.

If that doesnt help, try unplugging and reseating each memory stick.

After you do the above maintenance, then put in livecd disk and run memory test.

---

### Post by donniezazen on 2008-06-21
Thanks.

I am getting this message when i boot Windows Vista

*** Hardware Malfunction
Call your hardware vendor for support
NMI: Channel Check / IOCHK
*** The system has halted ***

and similar in Ubuntu.

It is a Dell Inspiron E1505/6400 laptop and i am kind of scared to open it.

Any suggestions!!!!!

---

### Post by bijeeshvs on 2008-06-21
just run the memory check from the live cd or from system boot menu ( grub)
and see if the memory is faulty.........................

---

### Post by donniezazen on 2008-06-23
> **bijeeshvs said:**
> just run the memory check from the live cd or from system boot menu ( grub)
and see if the memory is faulty.........................

I ran Memtest for around 3 hours after that it froze but i ran without any error.
I have removed one of the Memory stick which i think is faulted. Now i am getting this error.

I/O card parity interrupt at F000:ED67.c

Please any help would be appreciated.

Thanks

---

### Post by psykospun on 2008-06-23
my best bet would be to wipe your hardrive and start from scratch.

I know its brutal, but sometimes you just got to.

:-|

It might be something wrong in the registry. Try a repair installation first.

---

### Post by donniezazen on 2008-06-24
Thanks 

lemme reinstall everything.:mad:

---

### Post by Dutch70 on 2008-06-24
> **hal8000 said:**
> Its unusual for two Operating Systems to suffer from the same symptoms. Because they are both freezing you may be looking at either bad memory or overheating.

Easy things you can do, unplug the system remove the case, and vacuum all ventilation slots, fans, and air intakes. Perhaps use compressed air spray near the CPU. I've seen systems power up and reboot in 30 seconds, all because of a highly blocked fan.

If that doesnt help, try unplugging and reseating each memory stick.

+1, sounds like a hardware issue to me also, check the links below, and dont forget to touch your power supply before touching anything inside your PC.(to discharge any static electricity in your body) or get a wrist strap. 
 If reseating the memory sticks doesn't work, you can try moving them to a different slot(if available). Dirt is a PCs worst enemy.


[http://www.youtube.com/watch?v=AFTJpGCfTBo](http://www.youtube.com/watch?v=AFTJpGCfTBo) <<< clean
[http://www.youtube.com/watch?v=zkweJKSOYgo](http://www.youtube.com/watch?v=zkweJKSOYgo) <<< lube
[http://www.youtube.com/watch?v=IeZnHSnxS0I...feature=related](http://www.youtube.com/watch?v=IeZnHSnxS0I...feature=related)
[http://www.google.com/search?hl=en&q=r...amp;btnG=Search](http://www.google.com/search?hl=en&q=r...amp;btnG=Search)

If these aren't helpful now, they may be soon!
Best of luck!
Dutch

---

### Post by donniezazen on 2008-06-24
> **Dutch70 said:**
> +1, sounds like a hardware issue to me also, check the links below, and dont forget to touch your power supply before touching anything inside your PC.(to discharge any static electricity in your body) or get a wrist strap. 
 If reseating the memory sticks doesn't work, you can try moving them to a different slot(if available). Dirt is a PCs worst enemy.


[http://www.youtube.com/watch?v=AFTJpGCfTBo](http://www.youtube.com/watch?v=AFTJpGCfTBo) <<< clean
[http://www.youtube.com/watch?v=zkweJKSOYgo](http://www.youtube.com/watch?v=zkweJKSOYgo) <<< lube
[http://www.youtube.com/watch?v=IeZnHSnxS0I...feature=related](http://www.youtube.com/watch?v=IeZnHSnxS0I...feature=related)
[http://www.google.com/search?hl=en&q=r...amp;btnG=Search](http://www.google.com/search?hl=en&q=r...amp;btnG=Search)

If these aren't helpful now, they may be soon!
Best of luck!
Dutch

Hi,

I have Dell E1505/6400 Laptop not PC but anyways thanks-a-lot.

Strange things are happening with this laptop. I am currently in India on vacation and it is very hot and humid here. It used to work excellently in US. The strange thing is that some times it even wont start at all(not even the startup thing where you choose if you wanna enter setup or boot menu) then i just leave it for few hours and it starts automatically. I have clean installed the original OS(Vista) that came with it but it is still not working. 

I ran Memtest from grub menu it worked fine for 3 hours but froze during PASS 2. Windows hardware diagnostic utility ran without error or hardware problem. Windows memory diagnostic test came out without any error.

I dont know how to run Memtest from Live CD. Can anybody explain me how to do it?

I appreciate your help.

Thank.

---

### Post by Dutch70 on 2008-06-24
sorry I missed that, but to run memtest, you should just be able to put the live cd in and reboot, when you get to the screen that ask if you want to run it with no changes to your computer, or install etc, memtest should be about the 3rd option down.  you should just be able to hit enter, but I have never done this. so good luck!

edit: of course use the arrow keys to highlight memtest. :) then hit enter. remember, the longer memtest runs, the more accurate it is.

---

### Post by Dutch70 on 2008-06-24
I just noticed you said earlier that memtest froze on you in pass 2. it may run better from the live cd, but if it does, that "MAY" be a sign of a bad hdd. Maybe someone with more knowledge could add to this.

 You can try this link for help, but they're busy/slow...lol, but free!
[http://www.bleepingcomputer.com/forums/forum7.html](http://www.bleepingcomputer.com/forums/forum7.html)
if that's not where they want you they'll send you to the right area.

 Hope that helps!

---

### Post by vincentaii on 2008-06-24
Sounds exactly like what I experienced a couple of months back, whether booting into Ubuntu or Windows. It was driving me nuts, and I tried all sorts of things, including running memtest which, after a couple of hours, didn't report any faults. 

I finally figured out it WAS in fact a faulty RAM by removing all the RAM and testing each stick on its own using memtest. Maybe this is something you can try and see whther it detects better for you. Cheers.

---

### Post by Dutch70 on 2008-06-25
Well, vincentaii, sounds like faulty RAM to me also, worst case scenario being RAM connection to the mobo. been checking this thread first, every time I log on, hope to hear something soon.

Dutch

---

