---
title: "System problems detected"
date: 2016-11-08
forum: General Help
---

### Post by at35z on 2016-11-08
Hello there,

I've recently installed the GNOME on my computer. Since then, after booting up and logging in, two "System Problem detected" windows show up every time.

One of which is this:

[IMG]http://i.imgur.com/ryFJZbM.png[/IMG]

And this is the other one:

[IMG]http://i.imgur.com/tsjBOx0.png[/IMG]

These are obviously my fault, since they only appeared since I installed the DE, and looking at the descriptions, they seem to be related to this. How can I fix these? Do I need to install missing packages, or alter some already existing ones?

Thank you so much in advance!

---

### Post by alexjpowell on 2016-11-08
Afternoon,
Open a terminal and type:

sudo rm /var/crash/*

This will remove all old crashes
Reboot

If they keep appearing, post them up here again

---

### Post by at35z on 2016-11-08
I did what you told me and the same appeared.

Though only one bug report window followed, [Here's the whole thing in an imgur album](http://imgur.com/a/WAKzU).

---

### Post by at35z on 2016-11-08
Update: the other one's back, too.

---

### Post by Bashing-om on 2016-11-08
at35z; Hello;

With just a cursory look at the 2, I see no correlation between them.

Do we get any hints from:
```

sudo apt install --reinstall xserver-xorg-core

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See here that perhaps we get a fix for this one situation, then address plymouth .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

