---
title: "[SOLVED] Output installed package history?"
date: 2008-01-28
forum: General Help
---

### Post by dustigroove on 2008-01-28
Is there any way to output the install history of packages you have installed through apt without going into synaptic? Ideally I would like to export this install history to a text file...

Cheers,

---

### Post by aysiu on 2008-01-28
Try [this](http://ubuntuforums.org/showpost.php?p=841409&postcount=6).

---

### Post by bodhi.zazen on 2008-01-28
There is also dpkg -l

which you can pipe to a file as well :

```
dpkg -l
```

---

### Post by dustigroove on 2008-01-28
Unfortunately both answers don't quite do what I am looking to accomplish. [FONT=Courier New]sudo dpkg --get-selections >packages.txt[/FONT] and [FONT=Courier New]dpkg -l[/FONT] both output the full listing of  what packages are installed on the system. What I am trying to gather is only the packages that I have installed myself (basically the same contents as going to the *File* menu and selecting *History* in Synaptic Package Manager).

That being said I did scour through the man page for dpkg again after receiving your suggestions to see if I perhaps missed something the first time around. Indeed I did notice at the bottom of the man page that dpkg writes a log to /var/log/dpkg.log, and likely this is where the history is stored... I'll just need to script something to parse the log and grab what I need out of it.

So much thanks to you both for the suggestions and getting me to open my eyes and take another look... think I have what I need for this one and can mark her "closed".

Cheers,

---

