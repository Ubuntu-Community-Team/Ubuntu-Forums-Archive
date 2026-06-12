---
title: "Ubuntu 17.10"
date: 2017-11-08
forum: General Help
---

### Post by fanialivio on 2017-11-08
Hi everyone,

It's been a while now I'm experiencing constant (at least 3-4 times a day) freeze 

[COLOR=#181818][FONT=Consolas]<script src="https://pastebin.com/embed_js/87YCfuGJ"></script>[/FONT][/COLOR]


[COLOR=#181818][FONT=&quot][/FONT][/COLOR]

---

### Post by RobGoss on 2017-11-08
You will need to give more details on your issue, what are you doing when your system freezes? 

And you might what to change the title of your thread to address your problem

---

### Post by fanialivio on 2017-11-08
Hi Rob, thank you for your reply. 

[COLOR=#111111][FONT=Ubuntu]As far as I discovered, it is not linked to any particular activity or software I'm using. Just, randomly, the screen freeze. I can still move the pointer in this case but nothing happens and I'm forced to hard reboot.  I had this problem with Ubuntu 16.04, I decided to install Ubuntu 17.10 (fresh install) in order to solve it, but it's worse than before (more frequent). 

 Here is the complete pastebin for one session where the computer froze found in /var/log/kern.log :[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://pastebin.com/87YCfuGJ](https://pastebin.com/87YCfuGJ)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can see this error :[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://pastebin.com/mB5Ebn17](https://pastebin.com/mB5Ebn17)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But I'm not sure it is the primary cause. I'm thinking about a hardware freeze more than a software freeze.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help is appreciated.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you[/FONT][/COLOR]

---

### Post by RobGoss on 2017-11-08
Can you provide the specs for your machine it will help to see if your machine is able to handel Ubuntu

Sometimes you may not have the correct amount of Ram this can be  the biggest problem

---

### Post by #&amp;thj^% on 2017-11-08
> **RobGoss said:**
> 
Sometimes not have the correct amount of Ram is the biggest problem
+1 And GPU's

---

### Post by RobGoss on 2017-11-08
You might even consider trying a lightweight distribution like Lubuntu or Xubuntu, these distributions work well on older machines that don't have a lot of resources

---

### Post by fanialivio on 2017-11-09
Hi everyone,

After another freeze I discovered that the problem was related to nouveau. These are the last lines in the /var/log/kern.log in a crashed session :

[https://pastebin.com/Ym4T7uVC](https://pastebin.com/Ym4T7uVC)

Changing the video drivers from nouveau to NVIDIA solved the issue. 

Thank you

---

