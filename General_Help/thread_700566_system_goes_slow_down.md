---
title: "system goes slow down"
date: 2008-02-18
forum: General Help
---

### Post by amir_s_m on 2008-02-18
hi everyone,my system (cpu:centrino 1.73,1gig ddr2 ram,nvidia geforce 6200 go with 128 mb shared ram-onboard-,ubuntu 7.10 with 2 gig swap) goes slow down when ever ram becomes full.every thing is fine before ram becomes full,but after that a grate load on system and a very serious slow down happens,that even switching between running programs becomes impossible,so I have too reboot or logout and login.your help is very appreciated.

---

### Post by strabes on 2008-02-18
Please paste the output of the following command in a terminal (Applications, Accessories, Terminal).```
free
```

---

### Post by amir_s_m on 2008-02-19
> **strabes said:**
> Please paste the output of the following command in a terminal (Applications, Accessories, Terminal).```
free
```
 
```
 
          total       used           free     shared    buffers     cached
Mem:       1034224    1019724      14500          0       4892      23500
-/+ buffers/cache:     991332      42892
Swap:      2096440     549996    1546444

```

I don't know if it's related but sometimes visual effects goes to none automatically,and I cannot set it to custom,because screen becomes veeerrrrryyyy slow(looks like some refresh rate issue,but the thing is refresh rate is correct!!!!),I've to ctrl+alt+backspace to correct it,and sometimes I have to restart.....

---

### Post by amir_s_m on 2008-02-20
I personally think that compiz is the source of this issue,considering the strange going off of visual effects,after that huge amount of rams becomes free and speed becomes normal!!!so the problem must be the display driver(I got the last one) or the compiz.any ideas to track and solve this issue.

---

### Post by CLomax on 2008-02-20
I had this problem whenever I resized windows.

Type *ccsm* in the terminal, scroll to the bottom and select *Resize Window* under the *Uncategorized* category [Make sure it is checked]. Change the *Default Resize Mode* to *Stretch*.

---

### Post by amir_s_m on 2008-02-20
> **CLomax said:**
> I had this problem whenever I resized windows.

Type *ccsm* in the terminal, scroll to the bottom and select *Resize Window* under the *Uncategorized* category [Make sure it is checked]. Change the *Default Resize Mode* to *Stretch*.

thanx I'll check that and tell the result.

---

### Post by amir_s_m on 2008-02-28
> **amir_s_m said:**
> I personally think that compiz is the source of this issue,considering the strange going off of visual effects,after that huge amount of rams becomes free and speed becomes normal!!!so the problem must be the display driver(I got the last one) or the compiz.any ideas to track and solve this issue.

[QUOTE=CLomax]I had this problem whenever I resized windows.

Type ccsm in the terminal, scroll to the bottom and select Resize Window under the Uncategorized category [Make sure it is checked]. Change the Default Resize Mode to Stretch.[/QUOTE]

this did not fix the problem.

---

### Post by amir_s_m on 2008-02-29
looks like the problem definitely is Compiz,cause Htop shows 80% ram usage for compiz,that is alottt...but how can I address this issue??

---

