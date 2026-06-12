---
title: "Root on Ubuntu"
date: 2014-06-26
forum: General Help
---

### Post by ckrles on 2014-06-26
Hi, I have a problem with my hardware and in one of the attempts to solve it I ran an application using sudo su in the terminal.

I have a question. Have I activated the root temporarily or permanently? After the warning of being root I rebooted my. Did I stop being root once I rebooted?

Any way to know If I'm still root?

Thank you.

---

### Post by philinux on 2014-06-26
It was just temporary. When you closed the terminal it was revoked. 

When you use just sudo that also has a timeout.

Look at the prompt in a terminal to see if you are root. Note using just sudo as in sudo apt-get foo will not make you become root either. It just elevates your privilege to root.

---

### Post by uRock on 2014-06-26
Yes, you are no longer root. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

---

### Post by ckrles on 2014-06-26
Thank you

---

### Post by LastDino on 2014-06-26
Open terminal and see if you see this
```

user@pc:~$ 

```
That last part **~$ ** indicates that you're in normal mode.

If you see **#** instead of that, it means you're in root mode, which is unlikely. You can very much exit root mode by just typing ''exit'' without the ''...'' and entering in terminal after using it.

Sudo only allows temporary usage as root and occasionally it can be confusing.

Edit: Looks like I was nijnja'd by more than one person. I should learn to type fast :p

Anyway, one last tip, please don't use ''su'' and become root for whatever reasons you might find it appropriate unless you know exactly what you're doing.

---

### Post by deadflowr on 2014-06-26
Temporarily.
Though it is usually best to type exit when you are finished running the root session(su).
(the reboot would have done this anyway, but still best practices)
So, no, you are stilling running it as your user and not as root.

Edit: super ninja'd.
I guess I should have hit reply faster, instead of stared out at the wall.

---

### Post by ckrles on 2014-06-26
Thank you all for your help  ;)

---

