---
title: "beryl, aiglx problem."
date: 2006-12-27
forum: General Help
---

### Post by sefk26 on 2006-12-27
Hello it's me again.

I installed beryl+xgl on my computer following the beryl's wiki. Everything work as wished.

Then I decide to switch on aiglx(following the guide on the same website). And when I load beryl within the console, it's says: 

xgl absent.

Then I got windows without borders. :confused:

edit: I have a geforce 7600gt as graphic card and I'm on kubuntu 6.10

---

### Post by tokj on 2006-12-27
Did you remove the Xgl scripts?

Can you post the link to the wiki please?

---

### Post by sefk26 on 2006-12-27
No I didn't remove the xgl script, but I think it shoudn't matter 'cause I have two session(one which would load xgl and the other one no)

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX) for the wiki

---

### Post by d3v1ant_0n3 on 2006-12-27
What happens if you run 

```
 emerald
``` ?

---

### Post by sefk26 on 2006-12-27
I restest it.

When I login, it wont find xgl but beryl load nvidia instead. It works..but still I'm not under AIGLX.

I think that I will stick on xgl. but it's still interesting to know how aiglx works.

---

### Post by d3v1ant_0n3 on 2006-12-27
I *think* that Nvidia's newer drivers handle compositing on their own (i.e. don't need XGL or AIGLX). I might be horribly wrong tho.

---

### Post by sefk26 on 2006-12-27
Yeah Nvidia offer this option on their new driver.

It's not so horrible, but the performance seems slower.

---

### Post by d3v1ant_0n3 on 2006-12-27
I cursed this rubbish Intel 845 chipset in Windows- its slow, laggy and badly supported. Works like a charm in Linux tho, and Beryl runs amazingly well on it:D

---

### Post by tokj on 2006-12-28
You can force Beryl to use Aiglx by click on the icon on the panel, then go on "advanced beryl options"-->"rendering platform"-->"force aiglx".

---

