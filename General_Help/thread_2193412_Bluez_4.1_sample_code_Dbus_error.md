---
title: "Bluez 4.1 sample code Dbus error"
date: 2013-12-12
forum: General Help
---

### Post by sprite728 on 2013-12-12
I'm trying the DBus API Bluez 4.1 provides, starting from the sample code. However, this error:
 "Sending ListAdapters failed: org.freedesktop.DBus.Error.UnknownMethod: Method "ListAdapters" with signature "" on interface "org.bluez.Manager" doesn't exist"
show up when I issue the command `sudo python apitest -i hci0 ListAdapters`.
 
I also try many other sample code but the same exception show up, it seems like that DBus can not recognize the interface/methods BlueZ support. However, I have no idea how to make it work. 

Thanks in advance!

---

### Post by steeldriver on 2013-12-12
I've played with dbus a bit, and the schema documentation often seems to be out of date unfortunately - the only reliable way I've found to deal with this is to use the dbus **introspection** capability - there are a few tutorials around that may help you including this one:

[http://cheesehead-techblog.blogspot.ca/2012/08/dbus-tutorial-introspection-figuring.html](http://cheesehead-techblog.blogspot.ca/2012/08/dbus-tutorial-introspection-figuring.html)

Good luck! it can be very frustrating, I know...

---

### Post by sprite728 on 2013-12-13
Thanks for sharing that blog posts, very helpful. 

I tried the command:
 $ sudo dbus-send --system --print-reply --dest=org.bluez /org/hci0 org.freedesktop.DBus.Introspectable.Introspect
However, the result is this:
   string "<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node>
</node>
"

It seems there is no interfaces.. 

I also introspect all the bluez api by this command:
$ sudo dbus-send --system --print-reply --dest=org.bluez /org/bluez org.freedesktop.DBus.Introspectable.Introspect


And the result is:
<node>
	<interface name="org.freedesktop.DBus.Introspectable">
		<method name="Introspect">
			<arg name="xml" type="s" direction="out"/>
		</method>
	</interface>
	<interface name="org.bluez.HealthManager">
		<method name="CreateApplication">
			<arg name="config" type="a{sv}" direction="in"/>
			<arg name="application" type="o" direction="out"/>
		</method>
		<method name="DestroyApplication">
			<arg name="application" type="o" direction="in"/>
		</method>
	</interface>
	<node name="597"/>
	<node name="test"/>
</node>

There is only one interface, org.bluez.HealthManager. I still don't know where I can get access to the org.bluez.Manager and org.bluez.Adatper interface.

---

