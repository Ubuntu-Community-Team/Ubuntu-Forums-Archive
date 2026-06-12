---
title: "Nitro Tasks just say loading."
date: 2013-08-26
forum: General Help
---

### Post by Daniel_Leite_de_Abreu on 2013-08-26
Hi Guys.


Trust you guys are all good.


I have a small problem here, I install Nitro task in my ubuntu 12.04 and i really like it, i use for a day and then i start to get this problem that every time I start it only say loading.

I attach a screen grab of how the problem look like and also some what happen when I start the software from the CLI i hope someone can help me.



Thanks


dabreu@lt-dabreu:~$ nitrotasks 
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `Window' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwds)
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `NitrotasksWindow' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwds)
** Message: console message: undefined @0: SyntaxError: JSON Parse error: Unexpected identifier "undefined"


** Message: console message: undefined @0: TypeError: 'undefined' is not an object[ATTACH=CONFIG]245721[/ATTACH]

---

### Post by Daniel_Leite_de_Abreu on 2013-08-28
Hi to all just to show how to fix this problem just have a look on this post.

[http://askubuntu.com/questions/234363/nitro-tasks-files-location](http://askubuntu.com/questions/234363/nitro-tasks-files-location)

As Consindo say is just delete this file and all work  ~/.local/webkit/databases/file__0.localstorage

Then need to restore for backup on Ubuntu1

Thanks

---

