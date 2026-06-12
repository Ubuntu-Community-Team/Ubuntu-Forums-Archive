---
title: "Duplicate Entries for IDLE in Applications Menu"
date: 2017-05-05
forum: General Help
---

### Post by Lord Dark Star on 2017-05-05
Greetings,

This appears the most appropriate area to ask my question.  If I am mistaken, please forgive me and direct me to where the question is better suited to be.

I am running Kubuntu 17.04. I am starting a class in Python and needed to install IDLE. I did so through the [COLOR=black]CLI[/COLOR] using apt commands. IDLE was installed and no issue were encountered during the installation.  However, when I opened the applications menu, in the Development section I found two entries for IDLE. Since Kubuntu reported that IDLE was NOT installed prior to the installation I performed, I don't understand why there are two entries. They both point to the same path and both open the identical window.  Is there a reason I should have two entries or is this some sort of fluke [COLOR=black]occurrence[/COLOR]?  And if it is only a fluke, can someone explain to me how to remove one of the entries from the applications menu?

Many thanks in advance!
Frank

---

### Post by dragonfly41 on 2017-05-05
On Ubuntu 14.04 I see two IDLE entries under Programming ..

IDLE3 
IDLE (using Python 3.4)

I don't remember when I installed these since I use eric6.

...

When I launch IDLE3 I see this

```
Python 3.4.3 (default, Oct 14 2015, 20:33:09) 
[GCC 4.8.4] on linux
Type "copyright", "credits" or "license()" for more information.
>>>
``` 

When I launch IDLE (using Python 3.4) I see this

```
Python 3.4.3 (default, Oct 14 2015, 20:33:09) 
[GCC 4.8.4] on linux
Type "copyright", "credits" or "license()" for more information.
>>> 
```

Looking in /usr/bin/
I see

idle-python2
idle-python3
idle3


...

To remove one of the links I can go to Applications > Edit Menus (right click on Applications)
and under Programming untick one of the apps so that it doesn't show.

But I would try eric6 instead of IDLE.

[http://eric-ide.python-projects.org/eric-download.html](http://eric-ide.python-projects.org/eric-download.html)

---

