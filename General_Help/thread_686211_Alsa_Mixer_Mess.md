---
title: "Alsa Mixer Mess"
date: 2008-02-03
forum: General Help
---

### Post by anotherdisciple on 2008-02-03
I wanted to make my laptop speakers louder.... so someone suggested going to the terminal and typing "alsamixer" and turning up the volume. Well, that just turned up the volume like normal... it didn't turn up the gain like I wanted. Now, my media buttons don't turn up the volume since I changed the alsamixer in the terminal!!! What made that happen? How do I make them work again?

I have a Dell Inspiron E1505 by the way.... and once I figure out how to make thing return to normal... how can I make my speakers louder.... back in my windows days the volume seemed to get much louder... there has to be a way to do this in Ubuntu... I'm just not slick enough to figure it out just yet.

---

### Post by jan quark on 2008-02-04
have a look at the volume control

right-click on the volume applet and open the volume control

there you can increase the volume level of the master, pcm and cd and ... see picture

---

### Post by anotherdisciple on 2008-02-04
Well.. I have the PCM all the way up... it's still pretty quiet compared to when I used windows... but the bigger problem is that I can't use my media buttons to turn up the volume ever since I used "alsamixer" in the terminal!!!! I want my media buttons to control the volume...

I checked the keyboard settings... volume up and down are set to the correct buttons... when I hit volume up.. that icon that shows you how loud the volume is comes up... it just doesn't turn up the volume... wierd eh?

What caused this? And what will fix the buttons? I need to know this before I start worrying about making it louder.

---

### Post by anotherdisciple on 2008-02-05
anyone?

---

### Post by Kiri on 2008-03-25
I have the same problem with low volume...

---

### Post by northern lights on 2008-03-25
Can you both please post the output of ```
cat/proc/asound/cards
```

Thanks.

---

### Post by SLK55_AMG on 2008-03-25
> **northern lights said:**
> Can you both please post the output of ```
cat/proc/asound/cards
```

Thanks.



mine is:


xxx@postgreeskwill:/lib/linux-sound-base$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x80120000 irq 16

---

### Post by northern lights on 2008-03-25
Intel High Definition Audio Controllers have proven quite problematic, this [wiki]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") might help.

I got it done on a Dell Latitude D630, I'm sure one of the many workarounds works for you. It's a bitch though, granted...

---

### Post by Kiri on 2008-03-26
I'll give that a try, thanks

---

### Post by Kiri on 2008-03-26
Following the guide at:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

When I try to run 'sudo module-assistant update'

I get 'sudo: module-assistant: command not found'

Any ideas?

---

### Post by danwood76 on 2008-03-26
```
sudo apt-get install module-assistant
```
will install it so that command will work

---

### Post by Kiri on 2008-03-27
Following the guide did not seem to increase the volume for me. 
Nothing is audible until master volume gets to 60%, and doesn't become of an actual listenable volume until 80%+ depending on the source.

I can make do with it for now, hopefully it will get louder one day ;)

---

