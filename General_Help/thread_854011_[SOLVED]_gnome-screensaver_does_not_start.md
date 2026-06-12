---
title: "[SOLVED] gnome-screensaver does not start"
date: 2008-07-09
forum: General Help
---

### Post by unebaguettesvp on 2008-07-09
has anyone else had a problem with gnome-screensaver within the past month? it seems like a recent update (not sure what) screwed up my gnome-screensaver. i had it working fine under gutsy for a month or two.

when the screensaver kicks in, the screen turns black for a couple of milliseconds and then goes back to the previous view. when i lock my computer the screensaver works fine.

running gnome-screensaver from the command line:

```
philip@philip:~$ gnome-screensaver --debug
philip@philip:~$ Xlib: extension "XFree86-Misc" missing on display ":1.0".
Xlib: extension "XFree86-Misc" missing on display ":1.0".
Xlib: extension "XFree86-Misc" missing on display ":1.0".
```

when i run --no-daemon:

```
philip@philip:~$ gnome-screensaver --no-daemon --debug
[gs_debug_init] gs-debug.c:106 (00:47:38): Debugging enabled
[main] gnome-screensaver.c:87 (00:47:38): initializing gnome-screensaver 2.22.2
[init_session_id] gs-listener-dbus.c:2051 (00:47:38): Got session-id: /org/freedesktop/ConsoleKit/Session1
[gs_fade_init] gs-fade.c:683 (00:47:38): Fade type: 0
[initialize_server_extensions] gs-watcher-x11.c:903 (00:47:38): Not using server's MIT-SCREEN-SAVER extension.
[gs_watcher_set_active] gs-watcher-x11.c:731 (00:47:38): turning watcher: ON
[_gs_watcher_set_active_internal] gs-watcher-x11.c:718 (00:47:38): Starting idle watcher
[listener_dbus_handle_system_message] gs-listener-dbus.c:1481 (00:47:38): obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameAcquired destination=:1.46
[listener_dbus_handle_system_message] gs-listener-dbus.c:1481 (00:47:38): obj_path=(null) interface=(null) method=(null) destination=:1.46
[listener_dbus_handle_system_message] gs-listener-dbus.c:1481 (00:47:38): obj_path=(null) interface=(null) method=(null) destination=:1.46
[listener_dbus_handle_system_message] gs-listener-dbus.c:1481 (00:47:38): obj_path=(null) interface=(null) method=(null) destination=:1.46
[listener_dbus_handle_system_message] gs-listener-dbus.c:1481 (00:47:38): obj_path=(null) interface=(null) method=(null) destination=:1.46
[_gs_watcher_notice_window_created] gs-watcher-x11.c:568 (00:47:40): Window created: noticing activity on 0xC090F7
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1105 (00:48:08): Scheduling power notice in: 1
[power_timer] gs-watcher-x11.c:1080 (00:48:08): in power timer
[power_timer] gs-watcher-x11.c:1098 (00:48:08): Setting power notice elapsed: 30000
[watcher_power_notice_cb] gs-monitor.c:139 (00:48:08): Power notice signal detected: 1
[_gs_watcher_set_session_power_notice] gs-watcher-x11.c:478 (00:48:08): Changing power notice state: 1
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:28): in idle timer
[watcher_idle_notice_cb] gs-monitor.c:170 (00:48:28): Idle notice signal detected: 1
[gs_grab_grab_offscreen] gs-grab-x11.c:500 (00:48:28): Grabbing an offscreen window
[gs_grab_get_keyboard] gs-grab-x11.c:166 (00:48:28): Grabbing keyboard widget=2E00003
[gs_grab_get_mouse] gs-grab-x11.c:193 (00:48:28): Grabbing mouse widget=2E00003
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:501 (00:48:28): Changing idle notice state: 1
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[idle_timer] gs-watcher-x11.c:1115 (00:48:38): in idle timer
[watcher_idle_cb] gs-monitor.c:110 (00:48:38): Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:547 (00:48:38): Setting session idle: 1
[listener_check_activation] gs-listener-dbus.c:412 (00:48:38): Checking for activation
[listener_check_activation] gs-listener-dbus.c:427 (00:48:38): Trying to activate
[gs_grab_grab_root] gs-grab-x11.c:481 (00:48:38): Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:166 (00:48:38): Grabbing keyboard widget=52
[gs_grab_get_mouse] gs-grab-x11.c:193 (00:48:38): Grabbing mouse widget=52
[gs_manager_create_window] gs-manager.c:1375 (00:48:38): Creating 1 windows for screen 0
[gs_manager_activate] gs-manager.c:1495 (00:48:38): fading out
[fade_done_cb] gs-manager.c:1456 (00:48:38): fade completed, showing windows
[get_best_visual_for_screen] gs-window-x11.c:500 (00:48:38): Found best GL visual for screen 0: 0x2c
[window_map_cb] gs-manager.c:1214 (00:48:38): Handling window map event
[gs_window_clear] gs-window-x11.c:276 (00:48:38): Clearing window
[clear_all_children] gs-window-x11.c:251 (00:48:38): Clearing all child windows
[window_show_cb] gs-manager.c:1263 (00:48:38): Handling window show
[gs_job_set_command] gs-job.c:193 (00:48:38): Setting command for job: 'hufo_tunnel -r'
[gs_watcher_set_active] gs-watcher-x11.c:731 (00:48:38): turning watcher: OFF
[_gs_watcher_set_active_internal] gs-watcher-x11.c:714 (00:48:38): Stopping idle watcher
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:260 (00:48:38): Sending the ActiveChanged(TRUE) signal on the session bus
[gs_listener_update_console_kit_idle] gs-listener-dbus.c:296 (00:48:38): Updating ConsoleKit idle status: 1
[_gs_watcher_set_session_idle] gs-watcher-x11.c:524 (00:48:38): Changing idle state: 1
[listener_service_deleted] gs-listener-dbus.c:1043 (00:48:38): DBUS service deleted:
[gs_window_raise] gs-window-x11.c:627 (00:48:38): Raising screensaver window
[gs_window_raise] gs-window-x11.c:627 (00:48:38): Raising screensaver window
[gs_window_raise] gs-window-x11.c:627 (00:48:38): Raising screensaver window
[gs_window_xevent] gs-window-x11.c:679 (00:48:38): not raising our windows
[window_map_event_cb] gs-manager.c:1201 (00:48:38): Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1155 (00:48:38): Moving grab to 0x6502e0
[xorg_lock_smasher_set_active] gs-grab-x11.c:126 (00:48:38): Disabling the x.org grab smasher
Xlib: extension "XFree86-Misc" missing on display ":1.0".
[xorg_lock_smasher_set_active] gs-grab-x11.c:146 (00:48:38): XF86MiscSetGrabKeysState(off) returned MiscExtGrabStateSuccess

[gs_grab_move_keyboard] gs-grab-x11.c:331 (00:48:38): Moving keyboard grab from 52 to 2E0001C
[gs_grab_move_keyboard] gs-grab-x11.c:338 (00:48:38): *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:219 (00:48:38): Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:166 (00:48:38): Grabbing keyboard widget=2E0001C
[gs_grab_move_keyboard] gs-grab-x11.c:360 (00:48:38): *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:276 (00:48:38): Moving pointer grab from 52 to 2E0001C
[gs_grab_move_mouse] gs-grab-x11.c:283 (00:48:38): *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:237 (00:48:38): Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:193 (00:48:38): Grabbing mouse widget=2E0001C
[gs_grab_move_mouse] gs-grab-x11.c:306 (00:48:38): *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:206 (00:48:38): Starting job for window
[gs_job_start] gs-job.c:431 (00:48:38): starting job
[nice_process] gs-job.c:234 (00:48:38): Setting child process priority to: 10
[gs_window_xevent] gs-window-x11.c:679 (00:48:38): not raising our windows
[window_map_event_cb] gs-manager.c:1201 (00:48:38): Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1155 (00:48:39): Moving grab to 0x6502e0
[xorg_lock_smasher_set_active] gs-grab-x11.c:126 (00:48:39): Disabling the x.org grab smasher
Xlib: extension "XFree86-Misc" missing on display ":1.0".
[xorg_lock_smasher_set_active] gs-grab-x11.c:146 (00:48:39): XF86MiscSetGrabKeysState(off) returned MiscExtGrabStateSuccess

[gs_grab_move_keyboard] gs-grab-x11.c:324 (00:48:39): Window 2E0001C is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:264 (00:48:39): Window 2E0001C is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:212 (00:48:39): Not starting job because job is running
[gs_window_xevent] gs-window-x11.c:698 (00:48:39): not raising our windows
[gs_window_xevent] gs-window-x11.c:698 (00:48:39): not raising our windows
[window_obscured_cb] gs-manager.c:1287 (00:48:39): Handling window obscured: obscured
[gs_job_stop] gs-job.c:479 (00:48:39): stopping job
[gs_job_died] gs-job.c:128 (00:48:39): Waiting on process 16159
[gs_job_died] gs-job.c:142 (00:48:39): Job died
[window_obscured_cb] gs-manager.c:1287 (00:48:39): Handling window obscured: unobscured
[manager_maybe_start_job_for_window] gs-manager.c:206 (00:48:39): Starting job for window
[gs_job_start] gs-job.c:431 (00:48:39): starting job
[nice_process] gs-job.c:234 (00:48:39): Setting child process priority to: 10
[find_window_at_pointer] gs-manager.c:1131 (00:48:39): Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1473 (00:48:39): Requesting unlock
[gs_fade_reset] gs-fade.c:639 (00:48:39): Resetting fade
[gs_grab_release] gs-grab-x11.c:388 (00:48:39): Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:237 (00:48:39): Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:219 (00:48:39): Ungrabbing keyboard
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (00:48:39): Enabling the x.org grab smasher
Xlib: extension "XFree86-Misc" missing on display ":1.0".
[xorg_lock_smasher_set_active] gs-grab-x11.c:146 (00:48:39): XF86MiscSetGrabKeysState(on) returned MiscExtGrabStateSuccess

[gs_job_stop] gs-job.c:479 (00:48:39): stopping job
[gs_job_died] gs-job.c:128 (00:48:39): Waiting on process 16160
[gs_job_died] gs-job.c:142 (00:48:39): Job died
[window_unmap_cb] gs-manager.c:1221 (00:48:39): window unmapped!
[gs_window_dialog_finish] gs-window-x11.c:1249 (00:48:39): Dialog finished
[keyboard_command_finish] gs-window-x11.c:1125 (00:48:39): Keyboard finished
[gs_watcher_set_active] gs-watcher-x11.c:731 (00:48:39): turning watcher: ON
[_gs_watcher_set_active_internal] gs-watcher-x11.c:718 (00:48:39): Starting idle watcher
[gs_listener_update_console_kit_idle] gs-listener-dbus.c:296 (00:48:39): Updating ConsoleKit idle status: 0
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:260 (00:48:39): Sending the ActiveChanged(FALSE) signal on the session bus
```

any help would be appreciated. thanks!

---

### Post by unebaguettesvp on 2008-07-09
sorry for the bump. anyone had this problem?

---

### Post by InsektO on 2008-07-09
I'm having this same issue since yesterday (using 7.10). I thought the same about some update messing with the screensaver...

---

### Post by unebaguettesvp on 2008-07-10
I fixed the problem in Compiz. Go to the Settings Manager for Compiz. Go to General Options and uncheck "Unredirect Fullscreen Windows". That's it. Hope that helps. More information here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/159263)

---

### Post by InsektO on 2008-07-10
I don't have Compiz enabled, so I really don't see how that could make a difference. Anyways, I unchecked that option and the screensaver wouldn't work correctly, either.

Thanx anyways :D


---------------------------------------------------------------


Well, i solved it (at least for now) uninstalling and reinstalling gnome-screensaver.

---

