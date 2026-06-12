---
title: "Ubuntu 16.04 Pink Screen"
date: 2017-04-08
forum: General Help
---

### Post by alexalmighty on 2017-04-08
Hello everyone. 

I'm new to Ubuntu and I just installed it via USB to an older desktop which had a previous install of Windows 7.

I'm sure a rundown of my hardware will help.

Compaq Presario
2GB DDR2 RAM
250GB HDD
Processor: AMD Sempron LE-1300 @2.30GHz
64 bit processor

Not too sure about graphics.

The OS installed fine, the problem was a few minutes after using it. I probably used a few things like system settings, Firefox, and played around a bit. Doesn't seem to matter what I do, it gives me a pink screen after a while of using it. 

Here's the screen:
[http://i.xomf.com/bywds.jpg](http://i.xomf.com/bywds.jpg)

If anyone can help me with this issue you're the greatest, thanks.

Also I'm new on these forums, if I'm posting somewhere wrong I'm sorry.

---

### Post by RobGoss on 2017-04-08
Hello and welcome to the forums, This should allow us to see what graphic card your using, look like it might be a driver issue

Try running the following code:

```
 lspci -v
```

---

