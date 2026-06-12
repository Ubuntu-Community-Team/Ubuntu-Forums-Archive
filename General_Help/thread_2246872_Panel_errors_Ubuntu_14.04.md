---
title: "Panel errors Ubuntu 14.04"
date: 2014-10-03
forum: General Help
---

### Post by Rifester on 2014-10-03
I am pulling my hair out.   If I log into the other user on my 14.04 install I have no issues/errors with the panel indicators.   If I log in under my user name the volume and messaging indicators show a circle with a line through it.   The icons for my Empathy status in the message indicator do not exist.    I cannot figure out how to correct this.   If I enter:  

```
dconf reset -f /org/compiz/

```

and

```
setsid unity

```

the problem is corrected, but how do I make this persistent?   Do I have a corrupted config file? 


I appreciate the help!

---

