---
title: "Every now and again nautalus jumps to 30% CPU usage, I found &quot;dumped to signal 11&quot;"
date: 2007-12-15
forum: General Help
---

### Post by Mysticle31 on 2007-12-15
I have an interesting problem with nautilus.

Every now and again, and I haven't been able to tell when or how it's going to happen, when I close a nautilus window CPU usage will jump to about 30% and the hard drive will be very active.  I didn't know what it was so I let it run overnight since I was going to bed.  I thought maybe it was indexing files or something. 

I come back in the morning and see it's still going.  So I killall nautilus and it stops.  There were a couple of zombied nautilus entries in the system monitor.  I find this log file in my home folder for nautilus that says.

"0x8177510 2007/12/15 00:42:33.1685 (USER): debug log dumped due to signal 11"

Over and over and over again throughout the whole time that I let nautilus run overnight.  And it would have just kept on, keepin on if I didn't stop it.

What? Where? Why? How to fix?  Was nautilus thrashing my hard drive over night creating this huge file?

I found another thread from someone else who had the problem.


[http://ubuntuforums.org/showthread.php?t=581541](http://ubuntuforums.org/showthread.php?t=581541)

---

### Post by Mysticle31 on 2007-12-16
I found something interesting. 

On this installation of Ubuntu, I did not upgrade (as I have had problems with it).  Nautilus went and did it's thing.  This time I saw it at the beginning, the first time it did it on this installation.

Then it starts to do the debug log dumped due to signal 11 part over and over again, until I stop it, about 1/4 of the way into the log.  

When I killed nautilus, tracker took over using my CPU and trashing the HD and went to 50% CPU usage.  So I killed it too.

Any insight?

Sorry for the long post with the log excerpt.

> 0x8177510 2007/12/16 03:06:20.5588 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5591 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5591 (GLog): nautilus_file_get_uri: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5591 (GLog): gnome_vfs_uri_new_private: assertion `text_uri != NULL' failed
0x8177510 2007/12/16 03:06:20.5592 (GLog): nautilus_file_is_mime_type: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5592 (GLog): nautilus_file_clear_cached_display_name: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5592 (GLog): invalid uninstantiatable type `(null)' in cast to `GObject'
0x8177510 2007/12/16 03:06:20.5593 (GLog): g_object_set_data_full: assertion `G_IS_OBJECT (object)' failed
0x8177510 2007/12/16 03:06:20.5593 (GLog): invalid uninstantiatable type `(null)' in cast to `GObject'
0x8177510 2007/12/16 03:06:20.5594 (GLog): g_object_set_data_full: assertion `G_IS_OBJECT (object)' failed
0x8177510 2007/12/16 03:06:20.5594 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5594 (GLog): nautilus_file_ref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5595 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5595 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5595 (GLog): nautilus_file_get_uri: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5596 (GLog): gnome_vfs_uri_new_private: assertion `text_uri != NULL' failed
0x8177510 2007/12/16 03:06:20.5596 (GLog): nautilus_file_is_mime_type: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5596 (GLog): nautilus_file_clear_cached_display_name: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5597 (GLog): invalid uninstantiatable type `(null)' in cast to `GObject'
0x8177510 2007/12/16 03:06:20.5597 (GLog): g_object_set_data_full: assertion `G_IS_OBJECT (object)' failed
0x8177510 2007/12/16 03:06:20.5597 (GLog): invalid uninstantiatable type `(null)' in cast to `GObject'
0x8177510 2007/12/16 03:06:20.5598 (GLog): g_object_set_data_full: assertion `G_IS_OBJECT (object)' failed
0x8177510 2007/12/16 03:06:20.5598 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5599 (GLog): nautilus_file_ref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5599 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5599 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5600 (GLog): nautilus_file_should_show_directory_item_count: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5600 (GLog): nautilus_file_should_get_top_left_text: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5600 (GLog): nautilus_file_should_get_top_left_text: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5601 (GLog): nautilus_file_ref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5601 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5601 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5602 (GLog): nautilus_file_should_show_directory_item_count: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5602 (GLog): nautilus_file_ref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5603 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5603 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5603 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5604 (GLog): invalid uninstantiatable type `(null)' in cast to `NautilusFile'
0x8177510 2007/12/16 03:06:20.5604 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5604 (GLog): instance of invalid non-instantiatable type `(null)'
0x8177510 2007/12/16 03:06:20.5605 (GLog): g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
0x8177510 2007/12/16 03:06:20.5605 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5605 (GLog): nautilus_file_monitor_remove: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5606 (GLog): instance of invalid non-instantiatable type `(null)'
0x8177510 2007/12/16 03:06:20.5606 (GLog): g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
0x8177510 2007/12/16 03:06:20.5606 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5607 (GLog): nautilus_file_monitor_remove: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5607 (GLog): instance of invalid non-instantiatable type `(null)'
0x8177510 2007/12/16 03:06:20.5607 (GLog): g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
0x8177510 2007/12/16 03:06:20.5608 (GLog): nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed
0x8177510 2007/12/16 03:06:20.5610 (GLog): "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
0x8177510 2007/12/16 03:06:20.5612 (USER): debug log dumped due to signal 11
0x8177510 2007/12/16 03:06:20.6860 (USER): debug log dumped due to signal 11
0x8177510 2007/12/16 03:06:20.2703 (USER): debug log dumped due to signal 11
Etc for about 10 minutes when I killall nautilus
Then tracker takes over using 50% CPU usage, which I have no log for, so I killed it too.

---

