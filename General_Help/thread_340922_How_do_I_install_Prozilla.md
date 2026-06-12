---
title: "How do I install Prozilla?"
date: 2007-01-17
forum: General Help
---

### Post by Coop on 2007-01-17
Hello

I am trying to install the Prozilla download accelerator for Linux,and its graphical frontend Prozilla gui.

As you can see in the attached screenshot,I have successfully installed Prozilla but need help installing Prozilla gui.

I have downloaded the Prozilla and Prozilla gui debs from the official Debian website.

I have successfully installed Prozilla,but when I try to install Prozilla gui it says I need libfltk,even though I have both libfltk and libfltk-dev installed.

Please tell me what to do

Ahmed

---

### Post by Coop on 2007-01-17
Here's the two attached screenshots.

---

### Post by Coop on 2007-01-17
Please reply to me.
Ahmed

---

### Post by Coop on 2007-01-17
Please answer me
Ahmed

---

### Post by mdurham on 2007-01-17
maybe it needs a different version of libfltk from the one you have installed?
try starting the graphical frontend from a terminal, you often get more info on problems that way.

---

### Post by Coop on 2007-01-17
Hello
I can not start the graphical frontend from a terminal,as I do not have Prozilla gui installed.How do I start the graphical frontend from a terminal?
Also,how do I install a different version of libfltk?Where do I download it from?
Please reply to me.
Ahmed

---

### Post by kerry_s on 2007-01-18
You only need prozilla. Then just create the launcher, here's the command->

```
xterm -T "Prozilla" -e dproz
```

---

### Post by Coop on 2007-01-18
Thank you kerry_s,I think that'll work.
By the way,how do I pause,stop,start,resume and restart downloads?
And how do I schedule downloads?
And how do I control the preferences?
Please reply to me
Ahmed

---

### Post by kerry_s on 2007-01-18
When your downloading you will see the options at the bottom.
preferences = /etc/prozilla.conf
To schedule downloads you have to create a script.

I normally just use it with firefox>right click>copy link location and middle click it right into prozilla.

---

### Post by Enverex on 2007-01-18
> **Coop said:**
> Please answer me
Ahmed

It sometimes takes hours or days, maybe even weeks to get answers. Please don't spam the thread and keep bumping it. A least give it a day or two before doing that.

---

### Post by Coop on 2007-01-18
Hello
kerry_s thank you for your answer and your cool screenshots.
Please tell me how to create a script to schedule downloads
Ahmed

---

