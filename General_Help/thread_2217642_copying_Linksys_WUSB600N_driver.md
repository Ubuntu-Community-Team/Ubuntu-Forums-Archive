---
title: "copying Linksys WUSB600N driver"
date: 2014-04-18
forum: General Help
---

### Post by LdpmZ3xEfHPMV on 2014-04-18
Hi all,

Windows XP refugee, and a complete Linux newbie here.

I tried LXLE on my old laptop and was pleasantly surprised with how it recognized my Linksys WUSB600N Wireless-N USB Network Adapter right out of the box.

That's  something that I could not manage with any other Linux distro that I  tried. 
My question is, how can I copy this driver from LXLE to Lubuntu? (because I like Lubuntu's look and feel better, and the manual process of compiling the driver for Ubuntu is just way above my head).

Thanks

---

### Post by sdowney717 on 2014-04-18
[http://www.pcworld.com/article/2031825/have-an-older-pc-try-the-new-ubuntu-linux-based-lxle.html](http://www.pcworld.com/article/2031825/have-an-older-pc-try-the-new-ubuntu-linux-based-lxle.html)

I see it is ubuntu based.
Did you boot ubuntu and the wireless does not work?

---

### Post by stalkingwolf on 2014-04-18
have you tried using  the additional drivers feature?

---

### Post by ldpmz3xefhpmv2 on 2014-04-19
> **sdowney717 said:**
> [http://www.pcworld.com/article/2031825/have-an-older-pc-try-the-new-ubuntu-linux-based-lxle.html](http://www.pcworld.com/article/2031825/have-an-older-pc-try-the-new-ubuntu-linux-based-lxle.html)

I see it is ubuntu based.
Did you boot ubuntu and the wireless does not work?

Yes, there is nothing to configure the wireless network with.  In LXLE, using the same computer and USB adapter, I could scan for nearby networks and connect without configuring anything.


> **stalkingwolf said:**
> have you tried using  the additional drivers feature?

I went to Preferences > Additional Drivers, after a few seconds it said no propitiatory drivers are in use and there was nothing to enable.


I noticed the light on the USB adapter stays on, so it must have be recognized by Lubuntu. 

So I did some digging around and added the Network Applet next to the clock. [ATTACH=CONFIG]252233[/ATTACH]

from there I could click on the monitors icon and see nearby wireless networks, after clicking my wireless network and entering password, nothing happened.

I even reset my router, and disabled wireless password, but still it would not connect at all.  (I could connect with ethernet cable just fine).

any ideas how can I configure the wireless driver or something to make it work?
Thanks

---

### Post by ldpmz3xefhpmv2 on 2014-04-22
After searching some more I found out that if I type** nm-applet **then I would get a new icon at systray to configure the wifi! and it seems to be working fine. phewww....

but I do get a lot of warnings and failed messages at the terminal window, that I would appreciate if anyone could clarify:
> lubuntu@lubuntu:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon
nm-applet-Message: No keyring secrets found for MYWiFi/802-11-wireless-security; asking user.

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_new_with_path: assertion 'path_is_valid (path)' failed

(nm-applet:3301): GLib-GIO-CRITICAL **: g_settings_get_value: assertion 'G_IS_SETTINGS (settings)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_get_boolean: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_BOOLEAN)' failed

(nm-applet:3301): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed

(nm-applet:3301): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

(nm-applet:3301): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 3 char 81: '(((('' is not a valid name

(nm-applet:3301): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 3 char 81: '(((('' is not a valid name

(nm-applet:3301): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 3 char 81: '(((('' is not a valid name

(nm-applet:3301): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 3 char 81: '(((('' is not a valid name



also when I close the terminal the network manager icon goes away completely, how can I make it stay in the systray?

---

### Post by wieman01 on 2014-04-22
Just enter:
```
nm-applet &
```
It should stay now.

---

### Post by ldpmz3xefhpmv2 on 2014-04-23
> **wieman01 said:**
> Just enter:
```
nm-applet &
```
It should stay now.

That didn't do it. Had to manually add it to startup programs...

---

### Post by ldpmz3xefhpmv2 on 2014-04-26
This thread can be closed and marked as solved.

But clearly ** nm-applet **has a bug which prevents it from loading automatically in this case.

---

