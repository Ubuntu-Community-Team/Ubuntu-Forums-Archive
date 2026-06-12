---
title: "qpaeq - python jumps to 100% CPU usage"
date: 2014-11-26
forum: General Help
---

### Post by fondatommaso2 on 2014-11-26
Hello guys,
I'm writing because since I installed (from scratch, no upgrade) Utopic I can't use qpaeq anymore. qpaeq is a python program and in order to install it I've followed this tutorial, which I've been following for 2 years when I had to install qpaeq without a single problem: [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

Now, after I open a terminal and launch qpaeq this is what happens
[ATTACH=CONFIG]258222[/ATTACH]

python is using all my CPU and obviousky qpaeq is not starting. On Trusty, Saucy etc it was working flawlessly.
Should I file a bug on launchpad or what?
Thanks ;)

---

### Post by Al1000 on 2014-11-26
I see from the screenshot that uptime is only 1:40. Python frequently uses 100% of CPU resources for a short time after I boot my laptop, and I regard it as completely normal.

How long does Python continue to use 100% of CPU resources for, after booting up?

I've never even heard of qpaeg, but just thought I'd point out that Python using 100% of CPU resources for a short time after boot up, may not be related to your problem with qpaeg.

---

### Post by fondatommaso2 on 2014-11-27
> **Al1000 said:**
> I see from the screenshot that uptime is only 1:40. Python frequently uses 100% of CPU resources for a short time after I boot my laptop, and I regard it as completely normal.

How long does Python continue to use 100% of CPU resources for, after booting up?

I've never even heard of qpaeg, but just thought I'd point out that Python using 100% of CPU resources for a short time after boot up, may not be related to your problem with qpaeg.

It happens also after hours of uptime. If I type qpaeq in terminal and hit Enter, python immediately jumps to 100% CPU usage until I open another terminal and I type "sudo killall python".

---

