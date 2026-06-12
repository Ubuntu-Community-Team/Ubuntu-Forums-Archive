---
title: "Clean printers heads Epson"
date: 2007-09-07
forum: General Help
---

### Post by Osvaldo on 2007-09-07
Hi.

How do I clean the printers heads in Ubuntu ?

I've instaled **escputil** but i don't know how to use it... is this the right tool ?

My printer is a Epson D88 and it's connected trough lpt1 

I dont use it for a long time, and now only blue works !!!!

Best regards

Osvaldo

---

### Post by Osvaldo on 2007-09-09
No way (that works) of cleaning printer heads in Linux for a Epson D88 ?

---

### Post by Alex1770 on 2007-09-09
What happens if you type

escputil -c -u

?

Or, as a test, what happens if you type

escputil -s -u

?

---

### Post by Osvaldo on 2007-09-09
Thanks,

I'm away from my Ubuntu, now. I'll try it next Sunday.

Thanks


Osvaldo

---

### Post by Alex1770 on 2007-09-09
No problem. Do you know about man pages? If you type ```
man escputil
```, it will give information about how to use it.

By the way, I think Epson inkjets can be very poor, especially the cheaper ones (possibly other inkjets too, but I've only tried Epson myself). I wouldn't be surprised if it failed to work even after you clean the heads.

---

### Post by dasunst3r on 2007-09-09
I remember driving an Epson printer into the ground when I had one.  It lasted only two years or so before malfunctions galore.  HP printers, on the other hand, have been good for at least four years in my experience.  In any case, inkjets are a rip -- get a laser printer if you can afford one.

---

### Post by Alex1770 on 2007-09-09
I agree. I drove myself nuts trying to get Epson inkjets working. Finally gave up and purchased a colour laser printer (Xerox 6110N, which I think is the same as a Samsung CLP-300N). Works under Ubuntu if you follow the instructions on [http://www.dusted.dk/?view=linux-xerox-phaser-6110n-howto](http://www.dusted.dk/?view=linux-xerox-phaser-6110n-howto). The colour images won't be as good as a good photo inkjet can manage, but compared to the inkjets it's reliable, fast and cheap to run.

---

### Post by Alex1770 on 2007-09-10
Hmm. I should add to the above that although I have that particular laser printer working in Dapper, I'm having some problems with Feisty.

---

