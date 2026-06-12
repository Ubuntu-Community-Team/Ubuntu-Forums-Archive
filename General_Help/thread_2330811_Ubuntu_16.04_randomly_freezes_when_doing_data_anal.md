---
title: "Ubuntu 16.04 randomly freezes when doing data analysis"
date: 2016-07-15
forum: General Help
---

### Post by Loopster on 2016-07-15
Recently when doing data analysis, I started having issues with Ubuntu completely freezing: screen stops changing, mouse and keyboard do not respond, and hard drive light does not flash. I have tried waiting up to an hour for the system to unfreeze, but it doesn't and requires a manual reboot.

Looking into this issue, I have been able to reproduce the freezing by filling up the main memory and making the system use swap. For example, in R (with either the terminal or RStudio) I can use the following code to consistently freeze the system:
```

x <- replicate(1000000, 1:1000)

```
My computer has 8GB of RAM and 8GB swap. I ran this code while observing system monitor, and the system froze when resource usage was at 98% for RAM and 44% for swap.

I first thought this may be an issue with R, so I ran the same code on Windows 10 (I dual boot on the same computer). On Windows, this code ran for a while, caused some unresponsiveness, and then gracefully stopped with an error:
```

> x <- replicate(1000000,1:1000)
Error: cannot allocate vector of size 3.7 Gb
In addition: Warning messages:
1: In array(r, dim = d, dimnames = if (!(is.null(n1 <- names(x[[1L]])) &  :
  Reached total allocation of 8135Mb: see help(memory.size)
2: In array(r, dim = d, dimnames = if (!(is.null(n1 <- names(x[[1L]])) &  :
  Reached total allocation of 8135Mb: see help(memory.size)
3: In array(r, dim = d, dimnames = if (!(is.null(n1 <- names(x[[1L]])) &  :
  Reached total allocation of 8135Mb: see help(memory.size)
4: In array(r, dim = d, dimnames = if (!(is.null(n1 <- names(x[[1L]])) &  :
  Reached total allocation of 8135Mb: see help(memory.size)

```
I don't understand why running some R code on Ubuntu causes the entire system to freeze, but on Windows it just gives an error and moves on. Is this a problem with R or with Ubuntu? (I'm using Ubuntu 16.04 with default settings and the most recent updates). Has anyone else had similar issues with freezing? Is there any way to make Ubuntu not freeze up in situations like these?

---

