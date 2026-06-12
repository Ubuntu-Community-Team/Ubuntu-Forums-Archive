---
title: "bluetooth error message"
date: 2008-02-26
forum: General Help
---

### Post by tango_ninja on 2008-02-26
I'm trying to connect my Bluetooth headset (Motorolla H500) to my laptop but keep getting an error message. Here's what happens:

I plug in my dongle, the Bluetooth icon appears in my panel. so far so good. I turn on my h500 and send it into "discovery" mode. The laptop sees the h500 (Motorolla H500 appears in the browse list) but when I try to connect I receive the following error message:

```
"obex://[00:0c:55:52:f9:db]" is not a valid location. 
Please check your spelling and try again.
```

---

### Post by linuxwizard on 2008-02-26
Look at the bottom of this page for > Troubleshooting 
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by tango_ninja on 2008-02-26
thanks... however now I get:

"Couldn't display "obex://[xx:xx:xx:xx:xx:xx]"."

---

### Post by tango_ninja on 2008-03-19
any bluetooth experts? {bump}

---

### Post by alek01 on 2008-04-29
> **tango_ninja said:**
> I'm trying to connect my Bluetooth headset (Motorolla H500) to my laptop but keep getting an error message. Here's what happens:

I plug in my dongle, the Bluetooth icon appears in my panel. so far so good. I turn on my h500 and send it into "discovery" mode. The laptop sees the h500 (Motorolla H500 appears in the browse list) but when I try to connect I receive the following error message:

```
"obex://[00:0c:55:52:f9:db]" is not a valid location. 
Please check your spelling and try again.
```
***************

To connect use the following command:

sudo hidd --connect 00:07:61:6c:2f:94 where you replace these digits with the IP of your mouse.

If it is not on the mouse itself, type:

hidd --search

Unfortunately, I do not know how to make that command "default" in the config. I type it everytime I start Ubuntu.

---

### Post by damis648 on 2008-04-29
This is easy to fix. In the bluz config in the taskbar, right click it and click preferences. Click the Services tab. Check the box in the list that says "Input service" and then click "input service" and click "add" at the bottom. Just enable your mouse to be found and click on it and click connect. Easy as pie. And it is remembered upon restart.

EDIT: i mean bluez

EDIT 2: sorry i thought it was a mouse... for a headset do the same thing but with the audio service.

---

