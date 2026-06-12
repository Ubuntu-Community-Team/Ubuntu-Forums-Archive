---
title: "A few &quot;errors&quot; at startup"
date: 2008-03-27
forum: General Help
---

### Post by starfox5194 on 2008-03-27
when i boot into ubuntu there is a quick error message 

all i was able to see was kernel alive and then my computer continues to boot.

between the time of startup and login the monitor loses its signal.

I was just wondering if any of these problems were normal. or if they are problems.

My computer boots ok any i have full gfx support, but those problems just make me curious.

Specs

Q6600
Geforce 8800 GTS 512
4 Gb ram
1680 by 1050 monitor
Ubuntu gutsy latest updates

Thanks

P.S. I probably wonty reply untill tomorrow,

---

### Post by jpkotta on 2008-03-27
Are you sure it's an error message?  Linux spits out all sorts of info when it starts, most of it just says stuff like "I found this piece of hardware and it's ok."

---

### Post by dcstar on 2008-03-27
> **starfox5194 said:**
> when i boot into ubuntu there is a quick error message 

all i was able to see was kernel alive and then my computer continues to boot.

between the time of startup and login the monitor loses its signal.

I was just wondering if any of these problems were normal. or if they are problems.
........,

Unless you can exactly tell people what the "quick error message" is, then there is no way in the world to determine if there is a problem.

As far as the monitor is concerned, that is because the video mode changes from Grub to Splash screen to X Login screen, and your monitor cannot display whatever mode is used in the middle bit.

---

### Post by starfox5194 on 2008-03-28
ok the closest i can get to seeing the error message is
Starting up...




Kernel Alive 
Mapping tables 130000 @ 8000 - e000

I was just wondering if that meant like if the kernel was dead and it got revived in between that 1 second period.

those are the ONLY system messages i get at startup because of the black screen?

I was just really used to seeing all of those cool system diagnostic messages coming up and that is all i see.

---

### Post by danwood76 on 2008-03-28
They are normal messages.

The blank bit you see (monitor off) can be fixed by editing the usplash.conf and updating the initramfs.

in terminal do:
```

sudo gedit /etc/usplash.conf

```
and change it so that xres is 1024 and yres is 768 (gives you 1024x768 resolution)
then save it and run the following command:
```

sudo update-initramfs -u

```
then when you restart you should see the ubuntu logo with a progress bar below it instead of the blank screen you currently get.

---

### Post by starfox5194 on 2008-03-28
well i did what you said but i changed it to 1680 by 1050 and no dice...

---

### Post by danwood76 on 2008-03-28
try changing it to 1024x768 or if that doesnt work 800x600, its only a low res image so it doesnt really matter, the problem is I doubt your card can take a higher resolution when not loaded with the proper driver.
It will look a little out of aspect but its only a splash screen.

---

