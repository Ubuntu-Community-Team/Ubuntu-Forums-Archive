---
title: "How do I edit xorg.conf?"
date: 2007-07-12
forum: General Help
---

### Post by climbjm on 2007-07-12
I need to set "SHMConfig" to "true" in my xorg.conf but I have not the lightest clue how to do that or even where the file is located.

Can I open it with gedit?  I suck at VI.

---

### Post by merlinus on 2007-07-12
```

gksudo gedit /etc/X11/xorg.conf

```

Don't know about SHMConfig, though....

-merlin

---

### Post by Kodfish on 2007-07-12
```
gksu gedit /etc/X11/xorg.conf 
```

EDIT: beat me to it :3

---

### Post by aysiu on 2007-07-12
If you would prefer a GUI for configuring that file, look here:
[http://www.psychocats.net/ubuntu/xorg](http://www.psychocats.net/ubuntu/xorg)

---

### Post by climbjm on 2007-07-12
Awesome, that worked great.

One more quick question, 

The error I get says:
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.
```

So I opened xorg.conf and added the SHMConfig with the value of true, but it doesn't seem to have worked.  So I am looking for the XF86Config but search cannot find it.

Any ideas?

---

