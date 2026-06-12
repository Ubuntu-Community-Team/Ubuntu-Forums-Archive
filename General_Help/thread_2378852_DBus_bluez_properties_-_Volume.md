---
title: "DBus bluez properties - Volume"
date: 2017-11-28
forum: General Help
---

### Post by lukasz20 on 2017-11-28
I am trying to find commands to set and get volume of bluetooth headphones from the terminal. There are VolumeUp and VolumeDown methods available in org.bluez.MediaControl1 interface:
```
$ dbus-send --print-reply --system --dest=org.bluez /org/bluez/hci0/dev_XX_XX_XX_XX_XX_XX org.bluez.MediaControl1.VolumeUp
```
dev_XX_XX_XX_XX_XX_XX should be replaced with actual mac address and fdYY is regenerated everytime headphones are connected, there is d-feet software that helps with finding dbus properties

These methods work but according to [https://git.kernel.org/pub/scm/bluetooth/bluez.git/tree/doc/media-api.txt](https://git.kernel.org/pub/scm/bluetooth/bluez.git/tree/doc/media-api.txt) MediaControl interface is deprecated and MediaTransport should be used instead.
When use Introspect to list available properties:
```
$ dbus-send --print-reply --system --dest=org.bluez /org/bluez/hci0/dev_XX_XX_XX_XX_XX_XX/fdYY org.freedesktop.DBus.Introspectable.Introspect
```
I got [following response]("https://pastebin.com/EwUJic2N"), which contains:

[FONT=courier new]<interface name="org.bluez.MediaTransport1">[/FONT]
[FONT=courier new]  ...[/FONT]
[FONT=courier new]  <property name="Volume" type="q" access="readwrite" />[/FONT]
[FONT=courier new]</interface>[/FONT]

But when trying to list all the properties, Volume is not available:

```
$ dbus-send --print-reply --system --dest=org.bluez /org/bluez/hci0/dev_XX_XX_XX_XX_XX_XX/fdYY org.freedesktop.DBus.Properties.GetAll string:"org.bluez.MediaTransport1"


   array [
      dict entry(
         string "Device"
         variant             object path "/org/bluez/hci0/dev_XX_XX_XX_XX_XX_XX"
      )
      dict entry(
         string "UUID"
         variant             string "0000110..."
      )
      dict entry(
         string "Codec"
         variant             byte 0
      )
      dict entry(
         string "Configuration"
         variant             array of bytes [
               21 15 02 35
            ]
      )
      dict entry(
         string "State"
         variant             string "active"
      )
      dict entry(
         string "Delay"
         variant             uint16 1500
      )
   ]
```

I also cannot set the volume:
```
$ dbus-send --print-reply --system --dest=org.bluez /org/bluez/hci0/dev_2C_41_A1_02_E7_1C/fd29 org.freedesktop.DBus.Properties.Get string:"org.bluez.MediaTransport1" "string:Volume"
Error org.freedesktop.DBus.Error.InvalidArgs: No such property 'Volume'
```


What is the proper way of setting and reading bluetooth device volume?

---

