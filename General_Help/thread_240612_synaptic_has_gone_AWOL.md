---
title: "synaptic has gone AWOL"
date: 2006-08-21
forum: General Help
---

### Post by matrooswolf on 2006-08-21
Hi, 
strange problem here, since yesterday Synaptic went AWOL. 

When I go to system/administration/synaptic does nothing, not even an error message.

Update manager and everything else works fine (system is up-to-date).

Anybody any ideas (why it went AWOL, and how to fix it?)

---

### Post by peabody on 2006-08-21
You know what?  I think mine's broken too!  I hadn't noticed since I usually use apt-get from a terminal.  Do you get the following when you type synaptic in a terminal?

```

synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

```

---

### Post by Nokia on 2006-08-21
> sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

Try Search next time ;)

---

### Post by Kobalt on 2006-08-21
The promblem comes from a buggy update of XGL/compiz repos... Once you've done "ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4" you can use Synpatic back. I recomment you to delete libtve.so.4 after that. 

Cheers !

---

### Post by matrooswolf on 2006-08-21
To Peabody:
Yes I get exactly the same error.

To Nokia:
Thanx!  That fixed it.
I tried search but didn't find anything relevant (just too much hits with synaptic and missing, mostly about programs missing in synaptic, but not about synaptic itself missing) (maybe I didn't try hard enough?)

To Kobalt:
Thanx!  
One more question.
Why should I delete libtve.so.4?
I have no idea what it is and how it is connected to synaptic or Xgl/Compiz ...
And isn't a Xgl/Compiz update going to fix that?  I suppose the Compiz guys/girls know about this bug, and the packages are updated regulary. (I have compiz0.0.13-0quinn32)
But I am in the dark here ...

Thanx again everybody!

---

