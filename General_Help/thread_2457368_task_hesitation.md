---
title: "task hesitation"
date: 2021-01-31
forum: General Help
---

### Post by jgw on 2021-01-31
I wrote another on this one some time ago.  My problem is, basically, that when I want to do something there is a wait.  In this particular case I went to the terminal and ran "sudo" three separate times (no command, no nuttin)  Running the 'sudo' things were the last things that I did.  Each line has a time stamp so you will see that the last thing is the first thing at the top of the file below. 

From the time I pressed the enter key, to the time the program came up with asking my password it took 10 seconds.  This probably doesn't sound like much but I get these hesitations anytime I try and do things.  I get one, for instance, when I click on a mail address which then comes up on my Broswer.  I did the plain sudo just to make sure that it wasn't a problem with my browser.   Then I ran 'logs' and put the result to a file.  I have included that file below (125 lines).  Hopefully somebody can tell me what is going one.

Thank you...............

```
 2:26:45 PM dbus-daemon: [session uid=1000 pid=1382] Successfully activated service 'org.gnome.Logs'
 2:25:56 PM systemd: gnome-launched-org.gnome.Terminal.desktop-47296.scope: Succeeded.
 2:25:56 PM dbus-daemon: [session uid=1000 pid=1382] Successfully activated service 'org.gnome.Terminal'
 2:25:55 PM systemd: Starting GNOME Terminal Server...
 2:25:55 PM dbus-daemon: [session uid=1000 pid=1382] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.173' (uid=1000 pid=47302 comm="/usr/bin/gnome-terminal.real --window " label="unconfined")
 2:25:55 PM systemd: Started Application launched by gnome-shell.
 2:25:19 PM dbus-daemon: [session uid=1000 pid=1382] Successfully activated service 'org.gnome.Logs'
 2:24:47 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:24:24 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:23:15 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:23:12 PM gnome-shell: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
 2:23:11 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:23:08 PM gnome-shell: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
 2:23:01 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:22:42 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:22:30 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:22:05 PM systemd: gnome-terminal-server.service: Succeeded.
 2:22:00 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:21:54 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:20:53 PM systemd: gnome-launched-org.gnome.Terminal.desktop-46275.scope: Succeeded.
 2:20:53 PM dbus-daemon: [session uid=1000 pid=1382] Successfully activated service 'org.gnome.Terminal'
 2:20:52 PM systemd: Starting GNOME Terminal Server...
 2:20:52 PM dbus-daemon: [session uid=1000 pid=1382] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.168' (uid=1000 pid=46278 comm="/usr/bin/gnome-terminal.real --window " label="unconfined")
 2:20:52 PM systemd: Started Application launched by gnome-shell.
 2:20:34 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:19:38 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:19:19 PM gnome-shell: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
 2:18:26 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:17:51 PM gnome-shell: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
 2:17:49 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:17:34 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:17:19 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:16:27 PM gnome-shell: ../clutter/clutter/clutter-actor.c:10558: The clutter_actor_set_allocation() function can only be called from within the implementation of the ClutterActor::allocate() virtual function.
 2:16:04 PM systemd: gnome-terminal-server.service: Succeeded.
 2:16:00 PM dbus-daemon: [session uid=1000 pid=1382] Successfully activated service 'org.gnome.Terminal'
 2:16:00 PM systemd: Starting GNOME Terminal Server...
 2:16:00 PM dbus-daemon: [session uid=1000 pid=1382] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.166' (uid=1000 pid=45605 comm="/usr/bin/gnome-terminal.real --window " label="unconfined")
 2:16:00 PM systemd: Started Application launched by gnome-shell.
 2:15:57 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:14:41 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:13:54 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:13:23 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:13:09 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:13:05 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:11:55 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:11:11 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:10:48 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

 2:10:26 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:10:06 PM gnome-shell: Window manager warning: WM_TRANSIENT_FOR window 0x380772b for 0x3807770 window override-redirect is an override-redirect window and this is not correct according to the standard, so we'll fallback to the first non-override-redirect window 0x3800010.
 2:09:59 PM gnote: gtk_tree_model_sort_set_sort_column_id: assertion 'header != NULL' failed
 2:09:49 PM gnome-shell: JS ERROR: Error: Source.notify() has been moved to Source.showNotification()this code will break in the future
notify@resource:///org/gnome/shell/ui/messageTray.js:865:23
_showNotification@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:610:27
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_processClipboardContent@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:483:26
wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27
_refreshIndicator/<@/home/greg/.local/share/gnome-shell/extensions/clipboard-indicator@tudmotu.com/extension.js:461:18

```

---

### Post by HermanAB on 2021-02-01
Run top or htop and kill the stuck consumers of CPU cycles.

---

### Post by Holger_Gehrke on 2021-02-01
Most of the messages in your log come from just two sources: gnote and what looks to me like a gnome shell extension named clipboard-indicator. Try closing those to see whether they are responsible. If that's not the problem I'd set up a new user and log in with that to see whether it's something in the user specific configuration or something system wide and go from there.

Holger

---

