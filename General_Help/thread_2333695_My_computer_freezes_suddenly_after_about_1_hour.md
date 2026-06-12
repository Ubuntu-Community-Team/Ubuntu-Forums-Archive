---
title: "My computer freezes suddenly after about 1 hour"
date: 2016-08-12
forum: General Help
---

### Post by waterforce on 2016-08-12
Hello, I'm new to Ubuntu. My laptop is running Ubuntu 16.04.

Today, while I was listening music and writing some stuff, my computer suddenly froze (The music freeze too). I turn it off using power button and notice the same thing happened after about 1 hour. 

I don't remember clearly but maybe this thing happen after I use ```
sudo apt upgrade
``` and a package called ubuntu-core-launcher was upgraded. Could this be the cause?

I don't know what to do know. Please help me. Thank you so much!

---

### Post by coldraven on 2016-08-12
If your laptop is a few years old it might need the fan cleaned. Does the fan make a lot of noise?
To see if this is a temperature related fault you could install Psensor. See here:
[https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/](https://itsfoss.com/check-laptop-cpu-temperature-ubuntu/)

---

### Post by waterforce on 2016-08-12
No I just bought it last year. And It does not seem to be hot as I touch it, so I don't think that the problem.

---

### Post by coldraven on 2016-08-14
Maybe we can get a clue like this. Open a terminal with Ctrl+Alt+T then run the command "top" like this
```
top
```
The top command shows what processes are running, the ones that use the most resources are are the top. 
See on the white bar where it has %CPU and %MEM, if a program is using 100% of your processor there will be a problem. 
If you can leave the terminal window open and in front of your music player you might get to see which process is causing the freeze. To quit "top" press Q.

The only other thing I can think of is that you have a problem with your memory cards. Hopefully someone more clever than me will join in.

---

