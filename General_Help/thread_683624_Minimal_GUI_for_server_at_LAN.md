---
title: "Minimal GUI for server at LAN"
date: 2008-01-31
forum: General Help
---

### Post by _sAm_ on 2008-01-31
Hi, I have installed latest Ubuntu server, and I am gonna use it as a simple server on the LAN. I am new to all this, so I want/need GUI from time to time. I don't want the entire ubuntu-desktop, just a minimal part of it. I have tired this;

*sudo aptitude install gdm xorg firefox synaptic gedit gksu xterm gnome-terminal *

But now I dont have windows boarders and cant move the programs when I open them. Do you know witch package I am missing, and is the packages that I have installed ok for my purpose(its not a very old pc, so gnome will work fine)?

I will also try to use it without gui, via ssh. Would it be a good solution to just turn off GDM with rcconf later – when I want to try that? 

I have been reading some guides for this, but they where old. So if you know of any new guides pl let me know. 

Thanks for any help:-)

---

### Post by Scarath on 2008-01-31
gnome panel?

---

### Post by kesman on 2008-01-31
try
```

apt-cache search gnome |more

```

to look for gnome-related packages. Maybe it's something like gnome-window-decorator or stuff like that.

---

### Post by _sAm_ on 2008-01-31
Thanks for your replayes. 

It was not gnome panel, and the apt-cache search gnome |more gave me a very long list - so I gave up on that search. 
I then tried some different pacakge but ended up in d hell - so now I will go the easy way and just install xbuntu-desktop and remove the things that I dont want/need.

/Edit: But I still would like to know witch package you need to get the windows boarder in gnome?

---

