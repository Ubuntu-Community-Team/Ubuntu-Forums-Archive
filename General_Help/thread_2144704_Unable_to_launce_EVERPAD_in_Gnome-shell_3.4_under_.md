---
title: "Unable to launce EVERPAD in Gnome-shell 3.4 under ubuntu 12.04"
date: 2013-05-13
forum: General Help
---

### Post by drofart on 2013-05-13
I guess the problem is in gnome cause everpad is working correctly in other users with unity. Some time it happens but automatically it was working but this time hardluck.

Here is the consol error :```

$ everpad %u           
Traceback (most recent call last): 
File "/usr/bin/everpad", line 9, in <module> load_entry_point('everpad==2.3dev', 'gui_scripts', 'everpad')() 
File "/usr/lib/pymodules/python2.7/everpad/pad/indicator.py", line 307, in main pad.create_wit_attach(args.attach) 
File "/usr/lib/pymodules/python2.7/everpad/tools.py", line 30, in wrapper return getattr(self.__interface, name)(*args, **kwargs) 
File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__ return self._proxy_method(*args, **keywords) 
File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__ **keywords) 
File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking message, timeout) dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last): 
File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb retval = candidate_method(self, *args, **keywords) 
File "/usr/lib/pymodules/python2.7/everpad/provider/service.py", line 187, in create_note btype.Note.from_tuple(data).give_to_obj(note) 
File "/usr/lib/pymodules/python2.7/everpad/basetypes.py", line 53, in give_to_obj setattr(obj, field[0] + '_dbus', val) 
File "/usr/lib/pymodules/python2.7/everpad/provider/models.py", line 75, in notebook_dbus self.notebook = self.session.query(Notebook).filter( AttributeError: 'Note' object has no attribute 'session'
```

---

### Post by dino99 on 2013-05-13
looks like an issue with python2.7; so report it
do you have installed package(s) from ppa(s) ? (that possibly conflict)

---

### Post by drofart on 2013-05-13
I am not sure if i have installed it from ppa. So i have to report a bug, any workaround?

---

