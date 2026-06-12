---
title: "Playing music (that's on my windows box)"
date: 2005-10-02
forum: General Help
---

### Post by Skara on 2005-10-02
This may go better in the newb section. ^^;

Ok, I have an odd setup.  I have all my music on my windows box, but it's on my local network and I can access it from my ubuntu box.  Yay me. :P
Now whenever I try to play it in totem, though, it can't find the plugins (obviously).  I read somewhere it uses gstreamer plugins, but (I think) synaptic says they're installed.
Oh, and I'd just assume use the winamp playlists I already have made rather than have to update two playlists each time get a new song.

So what's my best course of action?

---

### Post by void_false on 2005-10-02
Ehm... Have you installed w32codecs?

---

### Post by Skara on 2005-10-02
and how would I do that?  I don't see anything that has 'w32' or 'codec' in synaptic.

---

### Post by void_false on 2005-10-02
There're no more w32codecs in repos due to legal issues. Plz read this thread for more info:
[http://ubuntuforums.org/showthread.php?t=67412&highlight=w32codec](http://ubuntuforums.org/showthread.php?t=67412&highlight=w32codec)
(There're instructions on how to install these codecs in 5th post.)

---

### Post by Skara on 2005-10-02
.. Didn't work.  I see a place in the Totem preferences that says Add Proprietary Plugins..., but I can't figure out how it works.  It just opens nautilus. :/
I even tried 'ln -s /usr/lib/codecs/* ~/.gnome2/totem-addons/' to no effect.

Edit:  tried dpkg the the file from the last link on that page as well, to no effect. =_=

Edit2:  Got it to work!!  I had to go and find gstreamer0.8-mad.  ^_^  Thanks for the help anyway. ;)

---

