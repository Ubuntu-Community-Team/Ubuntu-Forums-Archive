---
title: "How to fix “The system is running in low-graphics mode”?"
date: 2014-10-05
forum: General Help
---

### Post by thumper2 on 2014-10-05
Hello,

I just saw today this error “The system is running in low-graphics mode” 

I have dualboot windows 8 and ubuntu (x64) last version, i have tired few tips how to fix it but wont work for me.

I can open terminal but i cant activate 'network'. I have LIVE USB (Ubuntu) if i need to boot from USB please tell what i should do. 

Graphic details: http://m.imgur.com/Fn0LTlp

Please help me.

Thanks!

---

### Post by Bashing-om on 2014-10-06
thumper2; Hi !

The advisory "“The system is running in low-graphics mode”" indicates a graphics driver problem.
As you are able to obtain a terminal, please show us the result of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` which shows the graphics chip in use and IF there is a driver loaded.

Maybe then we can see
[INDENT][INDENT]what is to be done
[/INDENT][/INDENT]

---

### Post by thumper2 on 2014-10-06
> **Bashing-om said:**
> thumper2; Hi !

The advisory "“The system is running in low-graphics mode”" indicates a graphics driver problem.
As you are able to obtain a terminal, please show us the result of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

``` which shows the graphics chip in use and IF there is a driver loaded.

Maybe then we can see[INDENT][INDENT]what is to be done
[/INDENT]
[/INDENT]


Thanks for your reply!

If you wanted to see my graphics details here is screenshot: [https://i.imgur.com/VZOKqP2.jpg](https://i.imgur.com/VZOKqP2.jpg)

---

### Post by Bashing-om on 2014-10-06
thumper2; Well,

To this time we know you are running a 3rd generation Intel graphics controller.

Is there a driver loaded ? (hint: "sudo lshw -C display" ).

[INDENT][INDENT]it's all a process of learning
[/INDENT][/INDENT]

---

### Post by thumper2 on 2014-10-06
> **Bashing-om said:**
> thumper2; Well,

To this time we know you are running a 3rd generation Intel graphics controller.

Is there a driver loaded ? (hint: "sudo lshw -C display" ).[INDENT][INDENT]it's all a process of learning
[/INDENT]
[/INDENT]


There you go: [https://i.imgur.com/ZeexL6e.jpg](https://i.imgur.com/ZeexL6e.jpg)

Thank you!

---

### Post by Bashing-om on 2014-10-06
Thumper2; Yeah !

That do tell the tale, no driver is loaded.

However, as I know nothing about Intel, others will have to advise on a means to load an appropriate driver.
(it is Intel, It is supposed to be perfect, right out if the box !)

I too, am open to this as a learning experience.

---

### Post by thumper2 on 2014-10-06
Hi,

Can i re-install ubuntu and right after i install it can i install intel driver for linux? [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) 

Please tell me which one i should install. Thanks!

---

