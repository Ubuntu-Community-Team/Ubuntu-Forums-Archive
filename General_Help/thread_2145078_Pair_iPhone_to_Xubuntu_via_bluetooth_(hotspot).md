---
title: "Pair iPhone to Xubuntu via bluetooth (hotspot)"
date: 2013-05-14
forum: General Help
---

### Post by mgblake7 on 2013-05-14
Hi

I have paired my iphone with Xubuntu via bluetooth, however when I try to use it as a network access point I get the following:

Connection Failed: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in ServiceProxy
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/DBusService.py", line 121, in ServiceProxy
    self.Applet.Plugins.RunEx("service_connect_handler", cb, interface, object_path, _method, args, ok, err)
  File "/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py", line 231, in RunEx
    ret = getattr(inst, function)(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 333, in service_connect_handler
    conn = self.find_active_connection(d.Address, "panu")
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 290, in find_active_connection
    nma_connection = self.find_connection(address, type)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 278, in find_connection
    conns = self.nma.ListConnections()
AttributeError: 'NoneType' object has no attribute 'ListConnections'


Any help would be much appreciated!!

---

