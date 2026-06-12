---
title: "Please help with this i8k problem"
date: 2007-02-02
forum: General Help
---

### Post by Fred Doolie on 2007-02-02
Installed the i8k stuff and it always reports that the i8k process isn't there.
This can be solved by manually entering "sudo modprobe i8k force=1" EVERY time I reboot.
I put "i8k" in /etc/modules but that doesnt work. I tried putting "i8k -force" in /etc/modules but that doesn't work either. I also like to run gkrellm every time I boot so my fans will run.

My solution is an executable script on my desktop saying:

sudo modprobe i8k force=1
/usr/bin/gkrellm

If I choose "Run In Terminal" gkrellm wont start. If I use choose "Run" then the i8k module wont load so I have to click on it twice and choose each option. Annoying!

---

### Post by Fred Doolie on 2007-02-02
The "have to run it twice" problem solved by using "gksudo" instead of "sudo".

I just wish that i8k thing could be solved.

---

