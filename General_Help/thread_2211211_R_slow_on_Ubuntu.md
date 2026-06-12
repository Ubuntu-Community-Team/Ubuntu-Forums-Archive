---
title: "R slow on Ubuntu?"
date: 2014-03-14
forum: General Help
---

### Post by Peterlorre on 2014-03-14
Hi All, 

I've run across an odd phenomenon and I am wondering if someone might be able to provide insight as to what is going on. I'm running some R code that was provided by a collaborator, who is not a very experienced R programmer (e.g., the code is functional but not very efficient). When I run it from the terminal or command line everything executes, albeit very slowly- the logfile suggests that the program is about 5% done after running over last weekend. Top indicates that it is maxing out one of my CPUs and chewing up a lot of memory, which I expect. 

The strange thing is that my collaborator insists that the code executes on the order of minutes on his 2012 macbook pro with 8G of memory. I am running it with ubuntu 12.04 on a dual-core i7 with 32G, and it's slow as molasses. That suggests a configuration issue of some kind with R that I might not be aware of (I am more experienced in R and usually don't write code that requires resources like that). I have played with my swappiness and the effect seems to be minimal. Can anyone suggest something else that could be going on? I have considered trying to run it directly on a unix server, but the code has a lot of third-party dependencies that would be a pain in the ass to set up for simple troubleshooting. And naturally I'd prefer that R be configured correctly in the event that I need to locally run something more intense in the future. 

Thanks in advance for any advice you can give.

---

### Post by monkeybrain20122 on 2014-03-14
I think you need some packages for R to utilise multi-core. This kind of questions are probably better asked on the R mailing list.

---

