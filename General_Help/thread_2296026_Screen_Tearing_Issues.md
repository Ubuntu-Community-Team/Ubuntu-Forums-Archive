---
title: "Screen Tearing Issues"
date: 2015-09-23
forum: General Help
---

### Post by Afnan on 2015-09-23
Hello everybody, I am a new ubuntu user and have been extremely satisfied with the OS so far. Everything is perfect and working just fine except for one issue. I am using a Dell Inspiron N5110. Whenever I am browsing through the net I experience a bit of screen tearing when I am scrolling through the web pages. Can anybody tell me a way to fix this issue? Much appreciated. :)

---

### Post by Bucky Ball on 2015-09-23
Welcome. Please open a terminal and post the output of this command between code tags (see the last link in my signature):

```
sudo lshw -C video
```

Thanks. When you type that in and hit enter you will be asked for your password. When you type it it will be invisible. This is normal. :)

Also, could you update your machine (Software Updater or via a terminal) and then look in 'Additional Drivers'. Anything there related to video cards? Don't enable anything just yet. Let us know what's there.

---

### Post by Afnan on 2015-09-23
All my software are up to date and there are no additional drivers to install. I inputted the code you just gave on my terminal and this was shown:

[http://i.imgur.com/ZYp7T33.png?1](http://i.imgur.com/ZYp7T33.png?1)

---

### Post by mystics on 2015-09-23
Is it with every web browser or just with Firefox? If it is with Firefox, you could try disabling smooth scrolling at Preferences -> Advanced.

---

### Post by Afnan on 2015-09-23
Both Mozilla and Chrome, though its a lot less on firefox. It seems to happen during scrolling of web pages on google chrome

---

### Post by Afnan on 2015-09-27
Anybody has any solution for this please?? Really need it.

---

### Post by ogilvierothchild on 2015-09-27
What is the hardware, instructions as listed in post #2?

In case this helps anyone, I have an i5 sandybridge system that I solved screentearing on, by turning off my window manager being a compositing manager.  In my case, running the MATE desktop, that was done by running "dconf-editor" then going to /org/mate/marco/general and de-selecting "compositing-manager".

---

### Post by Bucky Ball on 2015-09-27
> **Afnan said:**
> Anybody has any solution for this please?? Really need it.

> **ogilvierothchild said:**
> What is the hardware, instructions as listed in post #2?



^^^
This. We can't help you if you don't help us. More info, please.

---

### Post by Afnan on 2015-09-28
> **Bucky Ball said:**
> Welcome. Please open a terminal and post the output of this command between code tags (see the last link in my signature):

```
sudo lshw -C video
```

Thanks. When you type that in and hit enter you will be asked for your password. When you type it it will be invisible. This is normal. :)

Also, could you update your machine (Software Updater or via a terminal) and then look in 'Additional Drivers'. Anything there related to video cards? Don't enable anything just yet. Let us know what's there.

Machine is fully updated, and find attached the screen shot of the terminal after inputting the code.

---

### Post by Afnan on 2015-09-29
Please check the attached thumbnail (click on it) to know about the hard ware info after I inputted this code 

"sudo lshw -C video"

---

### Post by Bucky Ball on 2015-09-29
There is no attached thumbnail. 'Adv Reply' and the paperclip icon in the toolbar is how to do it.

But don't give a screenshot. Just copy and paste the output and add code tags, thanks. See the last link in my signature.

---

### Post by Afnan on 2015-10-03
Finally found a solution for those who are interested, the problem of screen tearing mainly persisted on google chrome (not chromium). To solve it I wrote "chrome://flags" (without quotation marks) on my browser tab. Then searched for 'Enable smooth scrolling". Enabled that option and that seems to have fixed this issue for me.

---

### Post by Bucky Ball on 2015-10-03
Great and thanks for sharing. Please see the first link in my signature and good luck with it. :)

---

