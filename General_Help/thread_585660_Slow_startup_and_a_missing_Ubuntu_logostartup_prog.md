---
title: "Slow startup and a missing Ubuntu logo/startup progress screen"
date: 2007-10-21
forum: General Help
---

### Post by nisarg on 2007-10-21
Hello all,

I recently installed Ubuntu 7.10 - since then I have been experiencing some problems with the boot process. 
1. It takes incredibly long time to start up. It takes roughly 3-4 mins to startup. I am attaching the bootchart. I am new to Ubuntu and stuff in the chart makes very little sense to me. I would appreciate if someone can please take minute or two and review the chart for me and advice on how can I fix this problem and speed up the boot process.
  
2. On startup the Ubuntu splash screen/logo with boot progress is missing. As I power on my machine, it loads Grub .. prompts starting up.. and goes blank screen ... and after a long wait screen goes little grayish and logon screen pops up. It seems running fine after that. 
Here are the contents of my /etc/usplash.conf
[I]# Usplash configuration file
xres=1280
yres=1024 [/I]

I appreciate all your help or please let me know if I can provide any addition information to help diagnose the issue.
Thanks, Nisarg.

---

### Post by Happy_Man on 2007-10-21
What are the specs of your computer?

---

### Post by nisarg on 2007-10-21
Hello,

It is a IBM T40 with
Intel(R) Pentium(R) M Processor 1500MHz 
512 RAM
14.1" TFT display 
and all other usual stuff.

If you need more info - please tell me a command or way pull out a log of all the info.
Just on a side note - I had Ubuntu 7.04 Feisty earlier and it seemed perfect bootup on that, I would be on desktop in 1 min or so.

Thanks, Nisarg


> **Happy_Man said:**
> What are the specs of your computer?

---

### Post by nisarg on 2007-10-22
Can someone assist with this please?
Thanks...

---

### Post by dayvy on 2007-10-22
[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

---

### Post by nisarg on 2007-10-22
Fantastic. Thanks very much. Thats fixed it.

> **dayvy said:**
> [http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con](http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash.con)

---

### Post by sethtriggs on 2007-10-23
Worked for me too, thank you!

-Seth

---

### Post by mahiyar on 2007-10-23
You never stop learning in Linux and hence a novice. Just from nisarg's post, I learned that there was a programme like boot-chart giving all the fancy details. Nisarg- Can this program be turned selectively off?

---

### Post by nisarg on 2007-10-23
Mahiyar,
Bootchart indeed is an impressive piece of software. I never really dreamed of anything closer on windows.
Can this program be turned selectively off? Thats a good question. Unfortunately, I am a newbie too.I asked the same question to myself when I fixed the issue the issue I was having with the boot process, and tried googling around if there was a way to do it. I did try looking again but unfortunately havent managed to find anything promosing, 
One way that to me seems like the answer is to edit your bootup process so that it loads init instead of bootchart. But as I said I am not sure how to achieve this.
I rather just uninstalled it and installing it is never easier with Synaptic Package Manager. 
Cheers

> **mahiyar said:**
> You never stop learning in Linux and hence a novice. Just from nisarg's post, I learned that there was a programme like boot-chart giving all the fancy details. Nisarg- Can this program be turned selectively off?

---

### Post by Selcal on 2007-10-28
Hey thanks for the info, easy fix for a big problem.  My Gateway laptop is just singing.

---

