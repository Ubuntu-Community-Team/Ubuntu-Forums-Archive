---
title: "Persistent overclocking AMD cards in Ubuntu (script needed?)"
date: 2014-08-03
forum: General Help
---

### Post by 5mZKCMUmw1Le on 2014-08-03
Hi all,

I'm using overdrive to overclock my GPU, a XFX HD 5750 with fglrx updates driver.

I'm using aticonfig to set my new frequencies as this guide proposes:
[http://www.overclock.net/t/517861/how-to-overclocking-ati-cards-in-linux](http://www.overclock.net/t/517861/how-to-overclocking-ati-cards-in-linux)

after using 
```
aticonfig --odsc=x,y
``` 

to set the desired frequencies, AMD Catalyst control center, still produces stock frequencies, but running:

```
aticonfig --odgc
```
produces the desired frequencies. 

However, I am unable to make these changes stick when I reboot.


1. How do I know which program that gives me the correct frequencies?
2. Assuming aticonfig is correct: Any ideas how to make these frequencies stick? I'm willing to do a script here, although I'd prefer a less techy option.

Thanks!

---

