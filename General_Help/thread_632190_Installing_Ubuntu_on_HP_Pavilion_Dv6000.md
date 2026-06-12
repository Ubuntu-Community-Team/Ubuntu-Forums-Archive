---
title: "Installing Ubuntu on HP Pavilion Dv6000"
date: 2007-12-05
forum: General Help
---

### Post by Gigologio on 2007-12-05
Hello everybody.. I'm looking into join Ubuntu community because I've gotten sick of MS windows OS. 

I have an HP Pavilion Dv6000 with AMD turion 64-bits. a friend of mine provided me with a CD with Ubuntu 7.10 for 64 bits processors. He told me that I can keep windows on another partition (My little sister still needs windows for school duties).

OK, So I put the CD in, start PC, it boots from CD, got to the Ubuntu menu, I chose Start or Install Ubuntu, then it shows Ubuntu logo like loading, then a bunch of commands shows on the screen, with an [OK] at the end of each line.. then it says something about GNOME error (too fast) and then it goes completely black, the CD stops spinning. I cannot get any further...

Any ideas? Should I try the 32 bits version? 

Thanks in advance to all of you for your advices!

Gio

---

### Post by odiseo77 on 2007-12-05
Try the following: reboot the machine with the Gutsy CD inside. When you see the first boot screen where you are presented with a set of options, press the F6 key and write ***noapic*** at the end of the boot parameters line.

---

### Post by Gigologio on 2007-12-06
**[SIZE="4"]THank YoU[/SIZE]**!.. I tried that.. pressed F6 and typed noapic.. it loaded all right... first of all it loaded in Live CD mode... now.. i Decided to try it a little bit.. but.. I realized that Wireless internet won't connect... I plugged in my USB flash memory and it did not recognize it, also, i Have a USB mouse that did not work..
I also tried to play some music but it was asking to install some sort of "drivers" :confused:

Is this because I have not installed it completely on my HD (running only from CD) ?

Thank for your Time and SuPPorT

---

### Post by odiseo77 on 2007-12-06
Hi, well, I'm not sure since I don't have a laptop; I just tried this solution on a friend's HP Pavilion dv6000 and it worked (have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=515386")). I couldn't test it thoroughly, but I do remember the cd's played fine (didn't test inserting an USB key); so, maybe it's because it's not installed, as you say? If this helps, I used the alternate install cd by that time (which only installs the system; no live-cd mode). 

Oh, and one more issue: you'll probably get annoying IRQ messages at the terminal. I think there's a boot option to get rid of them, but I don't remember it now :-? Maybe someone with more knowledge about laptops can lend us a hand here? :)

Greetings.

---

