---
title: "'Send to' from desktop"
date: 2007-03-01
forum: General Help
---

### Post by avantgardaclue on 2007-03-01
Hi Folks, i use thunderbird as my email client, even went so far as to declare this in 'prefered applications' so that i could boot the prog up when i hit an email link in a web page. All is well, except.... I want to send a file via email from my desktop. I right button click to 'send to', the dialogue box opens giving me the choice to use only evolution. There is no alternative available when i click the down arrow for more choices.

Velly annoying!

Comments gratefully received

Simon
Hampshire England

---

### Post by yopnono on 2007-03-01
Create a nautilus action or a script.

---

### Post by avantgardaclue on 2007-03-01
> **yopnono said:**
> Create a nautilus action or a script.

Thankyou, i'm sure you're right. Unfortuneatly i have no idea how to do either!

If it makes a difference i am using 6.10

Simon
Hants England

---

### Post by yopnono on 2007-03-01
> **avantgardaclue said:**
> Thankyou, i'm sure you're right. Unfortuneatly i have no idea how to do either!

If it makes a difference i am using 6.10

Simon
Hants England

:) ok..
Install nautilus-action from synaptic
then open it from the system > Preferences > Nautilus Action
Then add a new action
```
Label: something like.. Attach and send to mail
Icon: pick an icon
Path: your mail client (mozilla-thunderbird)
Parameters: -compose "attachment=%u"
```

---

### Post by sebastjanp on 2007-03-03
Great solution and thank you very very much :D

---

### Post by avantgardaclue on 2007-03-09
Bingo! Works ace, thanks!! :)

---

### Post by sefs on 2007-05-13
hi, this does not work for me, after following the instructions, and then right clicking on a file on the desktop i dont see the new action in the menu.

Do i have to reboot?

EDIT: yes a reboot was neccessary.  But it does not however work for mutiple selections.

---

