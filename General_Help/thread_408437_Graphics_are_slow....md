---
title: "Graphics are slow..."
date: 2007-04-13
forum: General Help
---

### Post by ChrisUK on 2007-04-13
Hi all.

I installed Ubuntu for the first time a few days ago and I thought I installed nvidia drivers for my 7900GS.
When I couldn't figure out why Beryl was working, is when I realised the nvidia graphic drivers were not actually installed at all.
So I just installed these drivers with the help from some people on IRC, and Beryl is now working OK.
However, when I open and minimize windows and scroll it seems very slow/laggy. For example, if I quickly scroll down a page with my mouse wheel, it is very laggy and slow. If I scroll the mousewheel with my finger 3 times, it will take some seconds before the page actually stops scrolling down.
When I use the Beryl cube it seems OK and not laggy at all, also when I move windows around it's ok, it's only when I open windows, scroll, minimize, etc.

Does anyone know what could be causing this?
I don't know if it's Beryl or the GFX drivers I just installed, I think it could be the drivers.

---

### Post by tgm4883 on 2007-04-13
> **ChrisUK said:**
> Hi all.

I installed Ubuntu for the first time a few days ago and I thought I installed nvidia drivers for my 7900GS.
When I couldn't figure out why Beryl was working, is when I realised the nvidia graphic drivers were not actually installed at all.
So I just installed these drivers with the help from some people on IRC, and Beryl is now working OK.
However, when I open and minimize windows and scroll it seems very slow/laggy. For example, if I quickly scroll down a page with my mouse wheel, it is very laggy and slow. If I scroll the mousewheel with my finger 3 times, it will take some seconds before the page actually stops scrolling down.
When I use the Beryl cube it seems OK and not laggy at all, also when I move windows around it's ok, it's only when I open windows, scroll, minimize, etc.

Does anyone know what could be causing this?
I don't know if it's Beryl or the GFX drivers I just installed, I think it could be the drivers.

Sounds like drivers.  Do this in terminal and give us the output 

```
glxinfo | grep direct
```

---

### Post by ChrisUK on 2007-04-13
> **tgm4883 said:**
> Sounds like drivers.  Do this in terminal and give us the output 

```
glxinfo | grep direct
```

It said:

> direct rendering: Yes

---

### Post by compiledkernel on 2007-04-13
Here you go 

[https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)

---

