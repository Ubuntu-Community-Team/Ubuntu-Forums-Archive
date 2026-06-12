---
title: "Wall Command Not Outputting Chinese"
date: 2023-06-20
forum: General Help
---

### Post by mrbenmould on 2023-06-20
Hi my fellow ultra nerds, I used the wall command and successfully outputted a file, however the file contained Chinese characters, the English came out fine, but instead of characters I got a bunch of numbers, I swear it looked like the output of some 1970s Chinese nuclear missile silo, (any one seen the TV show Three Body Problem?) Chinese commies talking to aliens saving the world, impossible math, and video games, if you watch it you'll get my reference about the numbers I got outputted, check it........

[FONT=monospace][COLOR=#000000]sudo wall /home/b/Desktop/dtest[/COLOR]

[/FONT]

[COLOR=#000000][FONT=monospace]\343\200\220\347\254\254\344\270\200\347\253\240\343\200\221\351\201\223\345\217\257\351\201\223\357\274\214\351\235\236\345\270\270\351\201\223\357\274\233\345\220\215\345\217\257\345\220\215[/FONT][/COLOR]
[FONT=monospace]\357\274\214\351\235\236\345\270\270\345\220\215\343\200\202\346\227\240\345\220\215\345\244\251\345\234\260\344\271\213\345[/FONT]
[FONT=monospace]\247\213\357\274\214\346\234\211\345\220\215\344\270\207\347\211\251\344\271\213\346\257\215\343\200\202\346\225\205\345\270\270\346\227\240\346\254\262\357\274\214\344\273\245\350\247\202\345[/FONT]
[FONT=monospace]\205\266\345\246\231\357\274\233\345\270\270\346\234\211\346\254\262\357\274\214\344\273\245\350\247\202\345\205\266\345\276[/FONT]
[FONT=monospace]\274\343\200\202\346\255\244\344\270\244\350\200\205\345\220\214\345\207\272\350\200\214\345\274\202\345\220\215\357\274\214\345\220\214\350\260\223\344\271\213\347\216\204\357\274\214\347\216[/FONT]
[FONT=monospace]\204\344\271\213\345\217\210\347\216\204\357\274\214\344\274\227\345\246\231\344\271\213\351\227\250\343\200\202    [/FONT]
[FONT=monospace](Section 1) The path perpetuates the path, glorious is the path; notoriety perpetuates notoriety, glorious is the bright; without character, bright creation begins; by its being, all glorious creation is nourished. Always creating without greed, by means of observation it is intelligent, by modest means it sees its frontier. Here and now it is dual, they arise from the same origin, yet they are different in nature. It is synonymous with the black, the black perpetuates the black, the gateway to enlightenment for all.                                     [/FONT]
[FONT=monospace]                                               [/FONT]

---

### Post by Rubi1200 on 2023-06-21
Is the output you want in dtest? Saved as .txt?

First try this:

```
cat dtest.txt
```

If the terminal displays it correctly then...

```
sudo wall dtest.txt
```

---

