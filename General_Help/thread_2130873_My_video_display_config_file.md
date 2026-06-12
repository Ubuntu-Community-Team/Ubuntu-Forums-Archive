---
title: "My video display config file"
date: 2013-03-30
forum: General Help
---

### Post by rmcellig on 2013-03-30
I have no video on my laptop because of a config error I made. How can I get my screen back. Do I just have to trash the config file or edit it? If so, what is this file called and where is it located?

---

### Post by mikewhatever on 2013-03-30
Could be /etc/X11/xorg.conf, but it sounds strange that you do not know which file you've edited. I mean, if you don't, how should enyone else.

---

### Post by rmcellig on 2013-03-30
What I did was go into the GUI display settings and disable the use this monitor option not knowing that it would totally disable my screen. Now I need to get my screen back so I thought if I trashed the file responsible for this setting was trashed so a new one would be created on startup, that would be great. If this is not possible, I would need to know what the config file is called and how to edit it so that I have my screen back.

---

### Post by Bashing-om on 2013-03-30
rmcellig; Hi !
The config file " /etc/X11/xorg.conf " is largely depreciated now-a-days and will not exist on a standard install.
If you are running version 12.04 and have unity as your desktop; try terminal code:
```
 unity --reset
```which should first reset compiz then unity to the default settings.

Advise if otherwise ->[INDENT=4]
just try'n to help

[/INDENT]

---

### Post by rmcellig on 2013-03-30
I am running xubuntu 12.10

---

### Post by Bashing-om on 2013-03-30
try:
```
setsid unity
```

---

### Post by mikewhatever on 2013-03-31
Then you'll probably need .config/monitors.xml. Either edit, or delete it.

---

### Post by rmcellig on 2013-03-31
There is no monitors.xml file in my .config directory

---

### Post by steeldriver on 2013-03-31
so how are you connected right now? are you using an external monitor? or ssh'ing in?

---

### Post by rmcellig on 2013-03-31
Problem solved. I found a file called Displays.xml and trashed it. All is well now.

---

### Post by deadflowr on 2013-03-31
> **rmcellig said:**
> Problem solved. I found a file called Displays.xml and trashed it. All is well now.

Where was it?
So as to help someone later on who somehow, by chance, does the same thing.

---

### Post by rmcellig on 2013-03-31
Sorry about that! I meant to include the path but wasn't at my computer at the time. Here it is:

~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

I trashed this file, restarted and it worked!!

---

