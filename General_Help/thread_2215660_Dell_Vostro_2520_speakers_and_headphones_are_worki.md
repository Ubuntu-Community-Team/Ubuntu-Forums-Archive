---
title: "Dell Vostro 2520: speakers and headphones are working together"
date: 2014-04-07
forum: General Help
---

### Post by Gvi9 on 2014-04-07
i have recently purchased  new dell vostro 2520  in my laptop speakers and headphones are working together please help me out .. i have tried previous posts but its not working

---

### Post by grier-devon on 2014-04-07
```
[COLOR=#000000][FONT=Ubuntu Mono]lsb_release -a[/FONT][/COLOR]
uname -a
 [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 audio[/FONT][/COLOR]
```
please post output.

---

### Post by Eric_Atwood on 2014-04-08
If you have PulseAudio Volume Control installed, it should allow you to adjust both to your tastes.

---

