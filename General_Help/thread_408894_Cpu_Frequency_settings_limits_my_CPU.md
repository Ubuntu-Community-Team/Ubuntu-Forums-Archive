---
title: "Cpu Frequency settings limits my CPU"
date: 2007-04-13
forum: General Help
---

### Post by Dougga on 2007-04-13
I have an AMD64 3000+ and have found that Ubuntu is limiting it to a max of 2000 for some reason.  I can find no easy way to change any settings.  The cpufreq applet has only the most rudimentary configuration and I can't log in as root to see if it would function any better.

Q: How do I get Ubuntu to recognize my cpu correctly?
Q: How do I get the cpufreq applet to how the more advanced features that I read about on this forum?

Much thanks

---

### Post by thegreenblob on 2007-04-13
Run this command in the terminal -

```
sudo chmod +s /usr/bin/cpufreq-selector
```

And then add the cpu frequency scaling monitor to one of your panels. 

(Right click on panel and "Add to panel".)

See if that will let you do it.

---

### Post by raja on 2007-04-13
You can follow [this post]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/") to find what frequency steps are available for your cpu and how to get more control from the applet.

---

