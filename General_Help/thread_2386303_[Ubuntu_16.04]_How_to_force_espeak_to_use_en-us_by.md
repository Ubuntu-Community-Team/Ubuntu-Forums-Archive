---
title: "[Ubuntu 16.04] How to force espeak to use en-us by default"
date: 2018-03-03
forum: General Help
---

### Post by porparek on 2018-03-03
Hi,
espeak by default uses en-uk. I would like it to use en-us in emacspeak.
How can I do it ?
thanks in advance

---

### Post by #&amp;thj^% on 2018-03-03
```
espeak --voices
```
Now if your not comfortable with CLI Terminal use>> there is also a GUI called "gespeaker" with all kinds of options for you to choose from.
```
sudo apt install gespesker
```
Ok I'll take that as not interested in "gespeaker"
CLI it is then, but I use mbrola voices us-eng:
```
espeak -v mb-us1 -s 120 "Hello world and Ubuntu Users"

```
-s 120 will slow the speed of the voice itself.

---

### Post by porparek on 2018-03-07
Thanks for answer but question was rather about how to force espeak to use en-us voice in emacspeak.
I put the following line in /etc/emacpseak.conf
DTK_PROGRAM="espeak -v en-us"
but it causes emacspeak to fail to start
My question is where I should put "espeak -v en-us" to let emacpseak speak in en-us.
By the way I have the same question for speech-dispatcher.
I found:
/home/osboxes/.config/speech-dispatcher/modules/espeak.conf

but there is no place to add the espeak's "-v en-us" argument.
Please help me.
Thanks

---

### Post by #&amp;thj^% on 2018-03-07
Sorry but your title reads **"How to force espeak to use en-us by default "**
I stopped using emacpseak due to those limitations and defaults, and "my" needs were handled well enough with gespeaker. 
> Gespeaker A GTK frontend for espeak
I'm afraid this is all "I" can offer.

---

### Post by sudodus on 2018-03-07
> **1fallen said:**
> Sorry but your title reads **"How to force espeak to use en-us by default "**
I stopped using emacpseak due to those limitations and defaults, and "my" needs were handled well enough with gespeaker. 

I'm afraid this is all "I" can offer.

+1

I can also suggest that you use **espeak** or **gespeaker**.

I have used both, and I use 'plain' espeak everyday for example as a talking clock.

---

