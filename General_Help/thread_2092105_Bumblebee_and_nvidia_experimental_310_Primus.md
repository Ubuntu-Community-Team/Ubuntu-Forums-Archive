---
title: "Bumblebee and nvidia experimental 310? Primus?"
date: 2012-12-06
forum: General Help
---

### Post by axy_david on 2012-12-06
How should I proceed if I want these 2 to work together, should I just use additional drivers to get it working?
Any information about what Primus is all about?

UPDATE:
[http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html](http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html) explains my first question.
However, what is Primus and how can I install it, I\m no pro on linux so keep it simple, thanks.

---

### Post by UltimateCat on 2012-12-06
Hi:
*Primus* is a small lightweight GPU offloading implementation written in about 500 **...** in order to ultimately support technologies like *NVIDIA* Optimus.
Here is the website that supports that:

[http://www.phoronix.com/scan.php/www.phoronix.com/scan.php?page=news_item&px=MTE3NDk](http://www.phoronix.com/scan.php/www.phoronix.com/scan.php?page=news_item&px=MTE3NDk)
**[Primus: Better Performance And Less Power Consumption For Bumblebee [Optimus Hybrid Graphics Chipsets]]("http://www.webupd8.org/2012/11/primus-better-performance-and-less.html")**


[http://www.webupd8.org/2012/11/primus-better-performance-and-less.html](http://www.webupd8.org/2012/11/primus-better-performance-and-less.html)
[http://bumblebee-project.org/](http://bumblebee-project.org/)

[http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)

Until today I only knew about Optimus-

Hope this helps

---

### Post by axy_david on 2012-12-06
What is it so diffrent about it?
If it's all so good, why isn't it inncluded in the official pack?

---

### Post by UltimateCat on 2012-12-06
You asked:
> If it's all so good, why isn't it included in the official pack?


Not sure why but it most certainly doesn't make it easy and here's an article that will enlighten you but it's long-

What other option have I got? Intel/Optimus? Or, at the cheap end, Intel alone?
[http://www.linuxquestions.org/questions/linux-hardware-18/got-to-replace-with-what-4175436559/page2.html](http://www.linuxquestions.org/questions/linux-hardware-18/got-to-replace-with-what-4175436559/page2.html)

I learned a lot from reading what this thread said between the 2 men and the graphics issues.

---

### Post by axy_david on 2012-12-09
Well thanks for the reply I foundout the diffrence,
Optimus renders the whole application whie primus only renders the OpenGL inside the application.
Because of that, you gett better FPS in Primus but also the chance that it will not work.
So far it wprked without any errors for me. AAR
thanks for the replies.

---

