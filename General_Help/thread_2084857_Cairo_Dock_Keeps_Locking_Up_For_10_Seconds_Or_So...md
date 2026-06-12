---
title: "Cairo Dock Keeps Locking Up For 10 Seconds Or So..."
date: 2012-11-16
forum: General Help
---

### Post by cbanakis on 2012-11-16
I have been using Cairo without issues for quite some time.

Running Ubuntu 12.04 32bit.

Starting today, Cairo has been locking up every time I use it.

After like 10 Seconds, it kicks back in, and works again, but only for a moment.

I install Ubuntu updates frequently including today, so I believe one of the most recent updates is the cause.  But not sure which one, or how to fix it.

I ran Cairo in terminal, and it looks like there are errors, but I don't know what to make of it.

```
chris@chris-ET2410:~$ cairo-dock
warning :  (/build/buildd/cairo-dock-3.1.1/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:208)  
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================
    Cairo-Dock version : 3.1.1
    Compiled date      : Nov  5 2012 17:44:13
    Built with GTK     : 3.4
    Running with OpenGL: 1
 ============================================================================

Unity-Bridge: registered as Unity: <dbus.service.BusName com.canonical.Unity on <dbus._dbus.SessionBus (session) at 0x88cb4ac> at 0x88c40ec>
connect...
-> connected to cairo-dock
Unity-Bridge: Update application://empathy.desktop
Unity-Bridge: set_count (0)
Unity-Bridge: set_progress (0.00)
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
g_string_free: assertion `string != NULL' failed
g_string_free: assertion `string != NULL' failed
g_string_free: assertion `string != NULL' failed
Unity-Bridge: set_urgent (0)
on_name_owner_changed: :1.149
Unity-Bridge: set_count_visible (0)
Unity-Bridge: set_progress_visible (0)
Unity-Bridge: Update application://nautilus.desktop
Unity-Bridge: set_count (0)
Unity-Bridge: set_progress (0.00)
Unity-Bridge: set_urgent (0)
Unity-Bridge: set_menu (/com/canonical/unity/launcherentry/706927342)
Unity-Bridge: set_count_visible (0)
Unity-Bridge: set_progress_visible (0)
Unity-Bridge: Update application://nautilus-home.desktop
Unity-Bridge: set_count (0)
Unity-Bridge: set_progress (0.00)
Unity-Bridge: set_urgent (0)
Unity-Bridge: set_menu (/com/canonical/unity/launcherentry/1543400804)
Unity-Bridge: set_count_visible (0)
Unity-Bridge: set_progress_visible (0)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 604, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "./Pidgin", line 104, in on_name_owner_changed
    self.update_nb_unread_msg()
  File "./Pidgin", line 130, in update_nb_unread_msg
    n = self.get_nb_unread_msg()
  File "./Pidgin", line 115, in get_nb_unread_msg
    count = self.purple.PurpleConversationGetData(conv, "unseen-count")
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "PurpleConversationGetData" with signature "is" on interface "im.pidgin.purple.PurpleInterface" doesn't exist

('new owner:', dbus.UTF8String(':1.269'))
Unity-Bridge: launcher bus name changed: :1.72
Unity-Bridge: launcher bus name changed: :1.26
Unity-Bridge: launcher bus name changed: :1.26
gtk_widget_realize: assertion `widget->priv->anchored || GTK_IS_INVISIBLE (widget)' failed
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./Pidgin", line 259, in on_conversation_updated
    self.update_nb_unread_msg()
  File "./Pidgin", line 130, in update_nb_unread_msg
    n = self.get_nb_unread_msg()
  File "./Pidgin", line 115, in get_nb_unread_msg
    count = self.purple.PurpleConversationGetData(conv, "unseen-count")
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "PurpleConversationGetData" with signature "is" on interface "im.pidgin.purple.PurpleInterface" doesn't exist

g_variant_get_string: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_STRING) || g_variant_is_of_type (value, G_VARIANT_TYPE_OBJECT_PATH) || g_variant_is_of_type (value, G_VARIANT_TYPE_SIGNATURE)' failed
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "./Pidgin", line 259, in on_conversation_updated
    self.update_nb_unread_msg()
  File "./Pidgin", line 130, in update_nb_unread_msg
    n = self.get_nb_unread_msg()
  File "./Pidgin", line 115, in get_nb_unread_msg
    count = self.purple.PurpleConversationGetData(conv, "unseen-count")
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "PurpleConversationGetData" with signature "is" on interface "im.pidgin.purple.PurpleInterface" doesn't exist
```Has anyone else experience any problems recently?

This pretty much renders the computer un-usable.

---

### Post by cbanakis on 2012-11-16
I figured out the problem.

Apparently, it was actually the entire computer locking up.
(It was just only noticeable in Cairo, because of all the fun animated icons I had going)

The cause of the problem is pretty strange though.

The file server at my work is ridiculously full.  (93%)

And I guess, simply having the network share mounted on my computer was causing the lockups.

I went on the server, and cleared out some files, and that fixed the issue on my desktop.

Very weird though.

And yes, I am aware of how bad it is for our server to be that full, and have been pestering my boss for over a year now about upgrading.

Looks like its gonna happen soon now though.

Sorry for wasting everyones time with a false issue.

And thanks for reading.

---

