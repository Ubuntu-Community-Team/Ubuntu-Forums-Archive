---
title: "what am I doing wrong"
date: 2007-02-04
forum: General Help
---

### Post by fuzzyturtle on 2007-02-04
lets start with what i have.....
i have a T22 thinkpad 
I am running 6,1 edgy

My problem, 
Hal wont initialize dialog appears after logging in,
i have checked  my fstab file and also have tried using delayed login, i also have checked the  system logs to see if i could find any info on my problem, i also have reinstalled HAL and all associated library s
, i dont know if this is part of my problem but my device manager wont work, it looks like its starting then it just shuts down,

any help or insight would be appreciated

---

### Post by stalefries on 2007-02-04
Could you please post what the dialog box says exactly? Also, it'd be useful to see what the logs say.

---

### Post by fuzzyturtle on 2007-02-04
here is the screen shot of the error and the attached file is the log files for my system


[IMG]http://i9.tinypic.com/2niv4no.png[/IMG]

---

### Post by fuzzyturtle on 2007-02-07
since no one is giving me any help i'm gonna try to Remove hal completly 
wish me luck

---

### Post by fuzzyturtle on 2007-02-07
removing hal and reinstalling it cleared the "initialization error"  but it did not solve the problem with the device manager.....well back to the drawing board

---

### Post by llamakc on 2007-02-07
have you tried alternative kernels yet?

---

### Post by pay on 2007-02-07
Hal is dependent on Dbus, so make sure dbus is set up properly. Also  your device manager is dependent on hal so that's why it isn't working. I don't use Ubuntu so I can't really help you much with making hal and dbus work. Sorry.

---

### Post by fuzzyturtle on 2007-02-08
DBUS works fine and so does HAL after  i think i can do without the device manager for now

---

### Post by fuzzyturtle on 2007-02-09
is there a way to see the output of the device manager befor it closes? it might bring some insight to my problem

---

### Post by fuzzyturtle on 2007-02-09
> <gtk.Menu object (GtkMenu) at 0xb6829aa4>
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in ?
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 77, in __init__
    lambda *args: self.gdl_changed("DeviceAdded", *args))
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 291, in connect_to_signal
    self._obj.connect_to_signal(signal_name, handler_function, dbus_interface, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 151, in connect_to_signal
    path=self._object_path,
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 179, in add_signal_receiver
    named_service = bus_object.GetNameOwner(named_service, dbus_interface='org.freedesktop.DBus')
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Could not get owner of name 'org.freedesktop.Hal': no such name 
here is the output of the program 
can someone translate it into english

---

### Post by taloche on 2007-03-09
I think that you are getting this message because the service "hald" (hardware abstraction layer daemon) is not started. You can quickly check it by typing:

```
sudo /etc/init.d/hald start
```

and then retrying. If it works, you should add hald to the startup services list (System -> Administration).

Good luck.

---

