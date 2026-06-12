---
title: "Firefox 2.0 crashing on Edgy when a dialog box opens"
date: 2006-11-10
forum: General Help
---

### Post by amac777 on 2006-11-10
Hi all,

I am running Firefox on an Edgy system (clean install with latest updates installed). I have been getting many crashes in Firefox. I think it may be due to one of my plugins or something but need some help figuring out how to narrow this down. I used automatix to install flash and various other multi media drivers and plugins for firefox automatically.

I get two different crash situations in firefox. The first is just a random crash for no apparent reason. Here is the console output in that case:

```

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

Segmentation fault (core dumped)

```

The second only occurs when a javascript dialog box opens, but it doesn't happen all the time. Sometimes it works, sometimes is crashes. For example, a yes no dialog box confirming I want to delete an email in webmail. The dialog box outline pops up, but the buttons aren't there, and then about 1 second later firefox crashes with the following console output:

```
** Message: plugin_new_stream
** Message: plugin_new_stream type: audio/x-wav url: http://mywebmailsite.com/openwebmail/sounds/YouGotMail.English.wav
** Message: plugin_destroy
totemBasicPlugin dtor [0xb0e1f258]

(Gecko:21371): Gdk-CRITICAL **: gdk_colormap_get_screen: assertion `GDK_IS_COLORMAP (cmap)' failed

(Gecko:21371): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(Gecko:21371): Gdk-CRITICAL **: gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault (core dumped)

```

I have found the discussions in these forums about flash causing problem and I checked and my /etc/firefox/firefoxrc file already has export XLIB_SKIP_ARGB_VISUALS=1. Also my xorg file has color depth set to 24. 

Any suggestions of what I should do next?

---

