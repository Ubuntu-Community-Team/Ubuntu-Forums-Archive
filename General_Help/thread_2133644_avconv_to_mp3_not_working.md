---
title: "avconv to mp3 not working"
date: 2013-04-08
forum: General Help
---

### Post by AgentZ86 on 2013-04-08
Hi 


I can use avcon to convert from wma to wav but not to mp3

avconv -i 4_5_2013.wma -b 128k 4_5_3013.wav 
works fine

avconv -i 4_5_2013.wma -b 128k 4_5_3013.mp3
Does not work

I get this error:
Encoder (codec id 0) not found for output stream #0:0

Please advise

P.S sound converter works perfectly what do they use ?

---

### Post by AgentZ86 on 2013-04-08
it seems that lib3lame is not enabled by default and I am having trouble finding the folder in order to ./configure --enable libmp3lame0

---

### Post by SeijiSensei on 2013-04-09
Install ubuntu-restricted-extras.

---

### Post by AgentZ86 on 2013-04-09
I'll try that and post back

---

### Post by frewq on 2013-10-04
Encoding to mp3 using avconv works right after:
> sudo apt-get install ubuntu-restricted-extras

Thanks, SeijiSensei !

P.S. Ubuntu 13.10 Saucy Salamander

---

