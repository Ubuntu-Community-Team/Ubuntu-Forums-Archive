---
title: "Elisa won't run"
date: 2008-01-28
forum: General Help
---

### Post by ~LoKe on 2008-01-28
> $ elisa
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for coherence_plugin: coherence (elisa/core/plugin_registry.py:195)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for flickr_media: twill (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for bluetooth_input: bluetooth (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for lirc_input: pylirc (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for ipod_media: gpod (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for daap_media: daap (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for taglib_metadata: tagpy (elisa/core/plugin_registry.py:198)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Un-met dependency for stage6: BeautifulSoup (elisa/core/plugin_registry.py:195)
WARN  MainThread      comp_hal_service            Jan 28 18:18:31  Could not connect to the Gnome ScreenSaver: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files (elisa/plugins/good/hal/hal_service.py:107)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'coherence' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'coherence:coherence_service' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'gnome' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'gnome:gnome_screensaver_service' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'album_art' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'album_art:cover_in_dir' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'amazon' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'amazon:amazon_covers' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'album_art' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'album_art:cover_cache' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'gstreamer' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'gstreamer:gst_metadata_client' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component fspot_media failed to initialize: FSpot DB not found at '/home/loke/.gnome2/f-spot/photos.db' (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'flickr:flickr_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'stage6' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'stage6:stage_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'shoutcast' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'shoutcast:shoutcast_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'coherence' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'coherence:upnp_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'media_db' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'media_db:elisa_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'gvfs' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'gvfs:gnomevfs_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'ipod' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'ipod:ipod_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'daap' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'daap:daap_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'youtube' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Component 'youtube:youtube_media' not found (elisa/core/plugin_registry.py:618)
WARN  MainThread      plugin_registry             Jan 28 18:18:31  Plugin 'raval' not found (elisa/core/plugin_registry.py:455)
WARN  MainThread      interface_controller        Jan 28 18:18:31  Cannot create activity 'raval:elisa_activity' for backend 'backend1' (elisa/core/interface_controller.py:113)
WARN  MainThread      interface_controller        Jan 28 18:18:31  An error occured causing backend 'backend1' creation to fail (elisa/core/interface_controller.py:75)
A problem occurred in Elisa.
/tmp/elisa_dMJnRJ.txt contains the description of this error.
WARN  MainThread      interface_controller        Jan 28 18:18:31  Backend 'backend1' not existing for frontend 'frontend1' (elisa/core/interface_controller.py:165)
WARN  MainThread      interface_controller        Jan 28 18:18:31  An error occured causing frontend 'frontend1' creation to fail (elisa/core/interface_controller.py:90)
A problem occurred in Elisa.
/tmp/elisa_W85ZiS.txt contains the description of this error.

What am I doing wrong?

---

### Post by ~LoKe on 2008-01-28
Anyone?  How can I get these plugins?

---

### Post by loell on 2008-01-28
yes, it won't run :(, i've manage to get most of the plugins as these are just python modules available in the repo. but i was hitting the wall again with these error

```
loell@loell-desktop:~$ elisa
WARN  MainThread      service_manager             Jan 29 08:58:25  Component gnome_screensaver_service failed to initialize: DBus is not running. (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 29 08:58:25  Component daap_media failed to initialize: Couldn't initialize Avahi monitor: 'NoneType' object has no attribute 'DBUS_NAME' (elisa/core/manager.py:95)
WARN  MainThread      service_manager             Jan 29 08:58:25  Component hal_service failed to initialize: DBus is not running. (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 29 08:58:27  Component youtube_media failed to initialize: Can't initialize flvdemux CVS version of gst-plugins-bad (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 29 08:58:27  Component fspot_media failed to initialize: FSpot DB not found at '/home/loell/.gnome2/f-spot/photos.db' (elisa/core/manager.py:95)
elisa: could not connect to socket
elisa: No such file or directory
WARN  MainThread      interface_controller        Jan 29 08:58:30  Component lirc_input failed to initialize: Unable to initialize lirc! (elisa/core/interface_controller.py:324)
Segmentation fault (core dumped)

```

edit-- you can satisfy the plugin dependencies by querying **ie**

**apt-cache search python daap** you know, keyword error dependency then just add "python" to it . my bad, i forgot to list them.

---

### Post by ~LoKe on 2008-01-28
Ah, yeah, decided to hammer away and find out which ones I needed.  Now I get this:
> WARN  MainThread      media_manager               Jan 28 20:51:54  Component fspot_media failed to initialize: FSpot DB not found at '/home/loke/.gnome2/f-spot/photos.db' (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 28 20:51:54  Un-met dependency for flickr:flickr_media: twill (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 28 20:51:54  Component daap_media failed to initialize: Couldn't initialize Avahi monitor: 'NoneType' object has no attribute 'DBUS_NAME' (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jan 28 20:51:54  Component youtube_media failed to initialize: Can't initialize flvdemux CVS version of gst-plugins-bad (elisa/core/manager.py:95)
WARN  MainThread      comp_locations_builder      Jan 28 20:51:54  Location file:///home/loke/ given twice (elisa/plugins/good/xmlmenu/xmlmenu_components/locations_builder.py:294)
elisa: could not connect to socket
elisa: No such file or directory
WARN  MainThread      interface_controller        Jan 28 20:51:54  Component lirc_input failed to initialize: Unable to initialize lirc! (elisa/core/interface_controller.py:324)
WARN  MainThread      comp_pigment_context        Jan 28 20:51:54  Compiz detected, trying to hide all other windows. (elisa/plugins/good/pigment/pigment_context.py:217)

I can't get python-twill because it depends on a version of python-mechanize that's not in the Hardy repos.  I removed all compiz packages and it's still complaining about compiz.  And...all those other errors. =p

---

### Post by ~LoKe on 2008-01-28
Progress.

> WARN  MainThread      comp_locations_builder      Jan 28 21:15:21  Location file:///home/loke/ given twice (elisa/plugins/good/xmlmenu/xmlmenu_components/locations_builder.py:294)
elisa: could not connect to socket
elisa: No such file or directory
WARN  MainThread      interface_controller        Jan 28 21:15:21  Component lirc_input failed to initialize: Unable to initialize lirc! (elisa/core/interface_controller.py:324)
WARN  MainThread      comp_pigment_context        Jan 28 21:15:21  Compiz detected, trying to hide all other windows. (elisa/plugins/good/pigment/pigment_context.py:217)

---

### Post by DjBones on 2008-01-28
are you positive that you have:

gstreamer0.10-plugins-bad
or
python-imaging-dbg


.. its a suggested package for elisa
the meta package probably contains all the plugins you need, but if some aren't in the hardy repo's then i dont know
the python one is most likely not necessary.. but hell, its probably suggested for a reason lol
hope you get it working!

---

### Post by ~LoKe on 2008-01-28
Yup, I've got those.  I've trimmed the errors down to this:
> WARN  MainThread      comp_locations_builder      Jan 28 21:26:05  Location file:///home/loke/ given twice (elisa/plugins/good/xmlmenu/xmlmenu_components/locations_builder.py:294)
WARN  MainThread      comp_pigment_context        Jan 28 21:26:05  Compiz detected, trying to hide all other windows. (elisa/plugins/good/pigment/pigment_context.py:217)

The compiz issue should be sorted with a reboot.  But the first warning is what I might need to solve.

---

### Post by ~LoKe on 2008-01-28
Yep.  Only the first warning left.

---

### Post by loell on 2008-01-28
its good to know that it had less errors on hardy :)

in gutsy however, after triming down the services in **elisa.conf**

it still won't run, resulting segmenation fault and no warnings now,

going down further by debugging the core

```
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Core was generated by `/usr/bin/python /usr/bin/elisa'.
Program terminated with signal 11, Segmentation fault.
#0  0xb54e6936 in ?? ()

```

sigh :(

---

### Post by ~LoKe on 2008-01-28
I'm wondering how it made it into the repos.  I had to add the fluendo repositories to even get the dependencies.

---

### Post by wiscalico on 2008-01-31
Are you using 64-bit Ubuntu?

I tried with 64bit first and elisa just did a "Segmentation fault".

When using a 32 bit version on the same hardware I have no problem.

---

### Post by ~LoKe on 2008-01-31
32bit Ubuntu.

---

### Post by ~LoKe on 2008-01-31
Any ideas?  I'd really like to give this a shot...

---

### Post by wiscalico on 2008-02-01
I did a clean install yesterday and installed elisa from Ubuntu repos which worked. But shortly after I added Fluendos repos and installed Elisa 0.3.3:

[https://code.fluendo.com/elisa/trac/wiki/Packages](https://code.fluendo.com/elisa/trac/wiki/Packages)

They might have made some bugfixes which makes it work for you.

Apart from that I have no suggestions.

---

### Post by hyperair on 2008-02-01
When running elisa, it minimizes all my windows and then hangs. =\  Basically elisa doesn't seem to create any window whatsoever.

---

