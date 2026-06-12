---
title: "XChat-Gnome not opening!"
date: 2008-01-08
forum: General Help
---

### Post by LoneWolfUK on 2008-01-08
For some reason when I open XChat it immediately closes... I can see Xchat come up on the screen, but after a second it just closes again...

I have tried reinstalling it with the Synaptic package manager and it made no difference. I have also tried rebooting.

Do you know what might have caused this? It was working fine yesterday...

Are there any alternatives to XChat? I really need to use IRC.

---

### Post by mcduck on 2008-01-08
Try the real xchat instead of xchat-gnome. xchat-gnome is very limited and seems to have a lot more problems than xchat has..

Also, removing it's configuration files from your home directory might help. At least for the normal xchat they are in a hidden directory called .xchat2, press Ctrl-H in the file browser to see it.

---

### Post by LoneWolfUK on 2008-01-08
> **mcduck said:**
> Try the real xchat instead of xchat-gnome. xchat-gnome is very limited and seems to have a lot more problems than xchat has..

Also, removing it's configuration files from your home directory might help. At least for the normal xchat they are in a hidden directory called .xchat2, press Ctrl-H in the file browser to see it.


I just completely uninstalled Xchat-Gnome and installed Xchat -- it doesn't exactly the same thing... When I first opened XChat it looked completely corrupt, now it closes everytime I open it... :confused:

---

### Post by cdaringe on 2008-01-08
open up a terminal, type xchat, enter, and then paste the output. that should help discover your problem here

---

### Post by LoneWolfUK on 2008-01-08
> **cdaringe said:**
> open up a terminal, type xchat, enter, and then paste the output. that should help discover your problem here

Segmentation fault (core dumped)

:shock:

What does that mean?

---

### Post by cdaringe on 2008-01-08
hm, yea, that definitely above/beyond me.  i did some googling, and that error is not specific to xchat.  id say try 'completely removing' both using synaptic.  then install it from the source. if you visit sourceforge.net you can probably find a tarball download for it.  then install it on your own.  if you dont want to go that route, Kirc is a KDE irc client.  you can give that one a whirl

---

### Post by mcduck on 2008-01-09
Did you try removing the settings files? Even dong a complete remove will not remove these files, so you'll need to do it yourself..

---

### Post by LoneWolfUK on 2008-01-09
> **mcduck said:**
> Did you try removing the settings files? Even dong a complete remove will not remove these files, so you'll need to do it yourself..

Oops, I forgot to do that when you asked in one of the posts above. I just tried it and so far so good, XChat seems to be working nicely.

Thanks both of you for your help.

---

