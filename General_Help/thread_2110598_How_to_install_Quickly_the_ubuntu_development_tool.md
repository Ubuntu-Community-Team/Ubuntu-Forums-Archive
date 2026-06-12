---
title: "How to install Quickly the ubuntu development tool"
date: 2013-01-30
forum: General Help
---

### Post by MacPC on 2013-01-30
Hi, I never liked Linux that's why I gave up Linux a few years ago. Recently I am exploring Linux development, so I found the link to Ubuntu Quickly-a development tool. I installed ubuntu 12.whatever on my VM. When I go to the link to download Quickly, it says Please Wait The package you requested will install shortly. Then there is pop up says "The link needs to be opened with an application". Then there is a window pane Ubuntu Software Center, below it says "Choose an Application", next to it a button Choose. What Application do I choose for this download? 

Every time I use Linux, this is what I turn into
:confused::confused::confused::confused::confused::confused::confused

Any help will be greatly appreciated. :)

---

### Post by slickymaster on 2013-01-30
Have you tried to install it via terminal? It's that simple.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install quickly
```

---

### Post by MacPC on 2013-02-01
Thanks for the reply.

> **slickymaster said:**
> Have you tried to install it via terminal? It's that simple.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install quickly
```

"It's that simple' Then why the hell in the world following this link makes it so confusing?
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)

---

### Post by kanikilu on 2013-02-01
> **MacPC said:**
> "It's that simple' Then why the hell in the world following this link makes it so confusing?
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/) Believe it or not, they're trying to make it easier by allowing you to click on a link, and then have it open in the Ubuntu Software Center. From there, you just click "Install".

I just tried it, and it works for me, so I don't know what went awry when you tried to do it that way...

---

### Post by slickymaster on 2013-02-01
> **kanikilu said:**
> Believe it or not, they're trying to make it easier by allowing you to click on a link, and then have it open in the Ubuntu Software Center. From there, you just click "Install".

I just tried it, and it works for me, so I don't know what went awry when you tried to do it that way...

+1
Tried and succeed without any sort of complications along the way.

---

### Post by MacPC on 2013-02-10
Thanks all for the reply. I used slickmaster's suggestion (apt-get...), it worked. :)

" I don't know what went awry when you tried to do it that way..."
I don't know either. I think Linux just hates me! :cry:

---

