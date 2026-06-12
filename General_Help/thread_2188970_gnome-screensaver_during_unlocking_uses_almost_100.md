---
title: "gnome-screensaver during unlocking uses almost 100% of CPU"
date: 2013-11-20
forum: General Help
---

### Post by wrzomar on 2013-11-20
Recently my desktop PC with lucid on-board freaked out (screen goes blank, no responding and hdd LED goes crazy) so I was forced to press restart button (first time since a very long time). Next was disc scanning during restart, login , etc. But when I lock screen and want to unlock, after clicking "Unlock" nothing happen. I was doing this over VNC and ssh, so I run top: gnome-screensaver process uses almost 100%, so i killed gnome-screensaver with "killall gnome-screensaver" (for now it's only 100%-proof way to unlock screen;)). Next I runned "DISPLAY=:0.0 gnome-screensaver --no-daemon --debug", locked the screen and was trying to unlock - third time (after disconnecting VNC and ssh tunnel) gnome-screensaver finally got stuck again and this is the end of its output:
```
[manager_maybe_grab_window] gs-manager.c:1218 (09:11:58):     Moving grab to 0x816a008
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:11:58):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:354 (09:11:58):     Window 220006A is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:294 (09:11:58):     Window 220006A is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:11:58):     Starting job for window
[gs_job_start] gs-job.c:435 (09:11:58):     starting job
[gs_job_start] gs-job.c:450 (09:11:58):     No command set for job.
[gs_window_xevent] gs-window-x11.c:801 (09:11:58):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:11:58):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:11:58):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:11:58):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[unfade_idle] gs-manager.c:1245 (09:11:58):     resetting fade
[gs_fade_reset] gs-fade.c:865 (09:11:58):     Resetting fade
[find_window_at_pointer] gs-manager.c:1177 (09:12:01):     Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1724 (09:12:01):     Requesting unlock
[window_dialog_up_cb] gs-manager.c:1086 (09:12:01):     Handling dialog up
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:01):     Grabbing keyboard widget=220006A
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:01):     Grabbing mouse widget=220006A
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:01):     Ungrabbing pointer
[window_dialog_up_cb] gs-manager.c:1109 (09:12:01):     Suspending jobs
[gs_job_suspend] gs-job.c:512 (09:12:01):     suspending job
[popup_dialog_idle] gs-window-x11.c:1666 (09:12:01):     Popping up dialog
[gs_window_clear_to_background_pixmap] gs-window-x11.c:309 (09:12:02):     Clearing window to background pixmap
[update_geometry] gs-window-x11.c:430 (09:12:02):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:02):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:02):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[error_watch] gs-window-x11.c:1072 (09:12:02):     command error output: [gs_debug_init] gs-debug.c:106 (09:12:02):     Debugging enabled

[gs_manager_request_unlock] gs-manager.c:1845 (09:12:02):     Request unlock but dialog is already up

[listener_service_deleted] gs-listener-dbus.c:1043 (09:12:02):     DBUS service deleted:
[error_watch] gs-window-x11.c:1072 (09:12:02):     command error output: [auth_message_handler] gnome-screensaver-dialog.c:225 (09:12:02):     Got message style 1: 'Has&#322;o: '

[gs_window_raise] gs-window-x11.c:749 (09:12:03):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:820 (09:12:03):     not raising our windows
[gs_window_xevent] gs-window-x11.c:820 (09:12:03):     not raising our windows
[lock_command_watch] gs-window-x11.c:1561 (09:12:03):     command output: WINDOW ID=29360160

[error_watch] gs-window-x11.c:1072 (09:12:03):     command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:1193 (09:12:03):     Setting prompt to: Has&#322;o:

[gs_window_xevent] gs-window-x11.c:801 (09:12:03):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:12:03):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:03):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:03):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[gs_window_raise] gs-window-x11.c:749 (09:12:03):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:801 (09:12:03):     not raising our windows
[gs_window_xevent] gs-window-x11.c:801 (09:12:03):     not raising our windows
[error_watch] gs-window-x11.c:1072 (09:12:08):     command error output: [request_response] gnome-screensaver-dialog.c:153 (09:12:08):     got response: -2

[error_watch] gs-window-x11.c:1072 (09:12:08):     command error output: [do_auth_check] gnome-screensaver-dialog.c:299 (09:12:08):     Verify user returned: TRUE

[lock_command_watch] gs-window-x11.c:1561 (09:12:08):     command output: RESPONSE=OK

[lock_command_watch] gs-window-x11.c:1575 (09:12:08):     Got OK response
[gs_window_dialog_finish] gs-window-x11.c:1472 (09:12:08):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1347 (09:12:08):     Keyboard finished
[clear_widget] gs-window-x11.c:350 (09:12:08):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:08):     Clearing all child windows
[clear_widget] gs-window-x11.c:350 (09:12:08):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:08):     Clearing all child windows
[window_dialog_down_cb] gs-manager.c:1124 (09:12:08):     Handling dialog down
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:08):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:354 (09:12:08):     Window 220006A is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:309 (09:12:08):     Getting pointer grab on 220006A
[gs_grab_move_mouse] gs-grab-x11.c:313 (09:12:08):     *** doing X server grab
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:08):     Grabbing mouse widget=220006A
[gs_grab_move_mouse] gs-grab-x11.c:336 (09:12:08):     *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:09):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:09):     starting job
[gs_job_start] gs-job.c:450 (09:12:09):     No command set for job.
[gs_window_xevent] gs-window-x11.c:820 (09:12:09):     not raising our windows
[gs_window_xevent] gs-window-x11.c:801 (09:12:09):     not raising our windows

[listener_service_deleted] gs-listener-dbus.c:1043 (09:12:09):     DBUS service deleted: :1.143
[update_geometry] gs-window-x11.c:430 (09:12:09):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:09):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:09):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[gs_fade_reset] gs-fade.c:865 (09:12:09):     Resetting fade
[gs_grab_release] gs-grab-x11.c:418 (09:12:09):     Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:09):     Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:244 (09:12:09):     Ungrabbing keyboard
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:09):     No XFree86-Misc extension present
[gs_job_stop] gs-job.c:483 (09:12:09):     stopping job
[gs_job_stop] gs-job.c:486 (09:12:09):     Could not stop job: pid not defined
[window_unmap_cb] gs-manager.c:1284 (09:12:09):     window unmapped!
[gs_window_dialog_finish] gs-window-x11.c:1472 (09:12:09):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1347 (09:12:09):     Keyboard finished
[gs_watcher_set_active] gs-watcher-x11.c:275 (09:12:09):     turning watcher: ON
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:221 (09:12:09):     Sending the ActiveChanged(FALSE) signal on the session bus
[gs_manager_set_lock_active] gs-manager.c:424 (09:12:23):     Setting lock active: 1
[gs_grab_grab_root] gs-grab-x11.c:521 (09:12:23):     Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:23):     Grabbing keyboard widget=11F
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:23):     Grabbing mouse widget=11F
[gs_manager_create_windows_for_screen] gs-manager.c:1651 (09:12:23):     Creating 1 windows for screen 0
[gs_manager_create_window_for_monitor] gs-manager.c:1461 (09:12:23):     Creating window for monitor 0 [0,0] (1366x768)
[update_geometry] gs-window-x11.c:430 (09:12:23):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:23):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[get_best_visual_for_screen] gs-window-x11.c:622 (09:12:23):     Found best GL visual for screen 0: 0xef
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:23):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[window_map_cb] gs-manager.c:1277 (09:12:23):     Handling window map event
[clear_widget] gs-window-x11.c:350 (09:12:23):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:23):     Clearing all child windows
[clear_widget] gs-window-x11.c:350 (09:12:23):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:23):     Clearing all child windows
[window_show_cb] gs-manager.c:1355 (09:12:23):     Handling window show
[apply_background_to_window] gs-manager.c:1304 (09:12:23):     Creating pixmap background w:1366 h:768
[gs_job_set_command] gs-job.c:193 (09:12:23):     Setting command for job: 'NULL'
[gs_watcher_set_active] gs-watcher-x11.c:275 (09:12:23):     turning watcher: OFF
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:221 (09:12:23):     Sending the ActiveChanged(TRUE) signal on the session bus
[gs_manager_set_lock_active] gs-manager.c:424 (09:12:23):     Setting lock active: 1
[set_status] gs-watcher-x11.c:345 (09:12:23):     GSWatcher: not active, ignoring status changes
[gs_window_xevent] gs-window-x11.c:801 (09:12:23):     not raising our windows
[window_map_event_cb] gs-manager.c:1264 (09:12:23):     Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1218 (09:12:23):     Moving grab to 0x814cbd8
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:23):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:361 (09:12:23):     Moving keyboard grab from 11F to 22000AF
[gs_grab_move_keyboard] gs-grab-x11.c:368 (09:12:23):     *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:244 (09:12:23):     Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:23):     Grabbing keyboard widget=22000AF
[gs_grab_move_keyboard] gs-grab-x11.c:390 (09:12:23):     *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:306 (09:12:23):     Moving pointer grab from 11F to 22000AF
[gs_grab_move_mouse] gs-grab-x11.c:313 (09:12:23):     *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:23):     Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:23):     Grabbing mouse widget=22000AF
[gs_grab_move_mouse] gs-grab-x11.c:336 (09:12:23):     *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:23):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:23):     starting job
[gs_job_start] gs-job.c:450 (09:12:23):     No command set for job.
[gs_window_xevent] gs-window-x11.c:801 (09:12:23):     not raising our windows
[window_map_event_cb] gs-manager.c:1264 (09:12:23):     Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1218 (09:12:23):     Moving grab to 0x814cbd8
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:23):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:354 (09:12:23):     Window 22000AF is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:294 (09:12:23):     Window 22000AF is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:23):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:23):     starting job
[gs_job_start] gs-job.c:450 (09:12:23):     No command set for job.
[gs_window_xevent] gs-window-x11.c:801 (09:12:23):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:12:23):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:23):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:23):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[unfade_idle] gs-manager.c:1245 (09:12:24):     resetting fade
[gs_fade_reset] gs-fade.c:865 (09:12:24):     Resetting fade
[find_window_at_pointer] gs-manager.c:1177 (09:12:37):     Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1724 (09:12:37):     Requesting unlock
[window_dialog_up_cb] gs-manager.c:1086 (09:12:37):     Handling dialog up
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:37):     Grabbing keyboard widget=22000AF
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:37):     Grabbing mouse widget=22000AF
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:37):     Ungrabbing pointer
[window_dialog_up_cb] gs-manager.c:1109 (09:12:37):     Suspending jobs
[gs_job_suspend] gs-job.c:512 (09:12:37):     suspending job
[popup_dialog_idle] gs-window-x11.c:1666 (09:12:37):     Popping up dialog
[gs_window_clear_to_background_pixmap] gs-window-x11.c:309 (09:12:37):     Clearing window to background pixmap
[update_geometry] gs-window-x11.c:430 (09:12:37):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:37):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:37):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[error_watch] gs-window-x11.c:1072 (09:12:37):     command error output: [gs_debug_init] gs-debug.c:106 (09:12:37):     Debugging enabled

[gs_manager_request_unlock] gs-manager.c:1845 (09:12:37):     Request unlock but dialog is already up
[gs_manager_request_unlock] gs-manager.c:1845 (09:12:37):     Request unlock but dialog is already up

[listener_service_deleted] gs-listener-dbus.c:1043 (09:12:37):     DBUS service deleted:
[gs_manager_request_unlock] gs-manager.c:1845 (09:12:37):     Request unlock but dialog is already up
[error_watch] gs-window-x11.c:1072 (09:12:38):     command error output: [auth_message_handler] gnome-screensaver-dialog.c:225 (09:12:38):     Got message style 1: 'Has&#322;o: '

[gs_window_raise] gs-window-x11.c:749 (09:12:38):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:820 (09:12:38):     not raising our windows
[gs_window_xevent] gs-window-x11.c:820 (09:12:38):     not raising our windows
[lock_command_watch] gs-window-x11.c:1561 (09:12:38):     command output: WINDOW ID=29360160

[error_watch] gs-window-x11.c:1072 (09:12:38):     command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:1193 (09:12:38):     Setting prompt to: Has&#322;o:

[gs_window_xevent] gs-window-x11.c:801 (09:12:38):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:12:38):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:38):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:38):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[gs_window_raise] gs-window-x11.c:749 (09:12:38):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:801 (09:12:38):     not raising our windows
[gs_window_xevent] gs-window-x11.c:801 (09:12:38):     not raising our windows
[error_watch] gs-window-x11.c:1072 (09:12:48):     command error output: [request_response] gnome-screensaver-dialog.c:153 (09:12:48):     got response: -2

[error_watch] gs-window-x11.c:1072 (09:12:48):     command error output: [do_auth_check] gnome-screensaver-dialog.c:299 (09:12:48):     Verify user returned: TRUE

[lock_command_watch] gs-window-x11.c:1561 (09:12:48):     command output: RESPONSE=OK

[lock_command_watch] gs-window-x11.c:1575 (09:12:48):     Got OK response
[gs_window_dialog_finish] gs-window-x11.c:1472 (09:12:48):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1347 (09:12:48):     Keyboard finished
[clear_widget] gs-window-x11.c:350 (09:12:48):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:48):     Clearing all child windows
[clear_widget] gs-window-x11.c:350 (09:12:48):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:48):     Clearing all child windows
[window_dialog_down_cb] gs-manager.c:1124 (09:12:48):     Handling dialog down
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:48):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:354 (09:12:48):     Window 22000AF is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:309 (09:12:48):     Getting pointer grab on 22000AF
[gs_grab_move_mouse] gs-grab-x11.c:313 (09:12:48):     *** doing X server grab
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:48):     Grabbing mouse widget=22000AF
[gs_grab_move_mouse] gs-grab-x11.c:336 (09:12:48):     *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:48):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:48):     starting job
[gs_job_start] gs-job.c:450 (09:12:48):     No command set for job.
[gs_window_xevent] gs-window-x11.c:820 (09:12:48):     not raising our windows
[gs_window_xevent] gs-window-x11.c:801 (09:12:48):     not raising our windows

[listener_service_deleted] gs-listener-dbus.c:1043 (09:12:48):     DBUS service deleted: :1.144
[update_geometry] gs-window-x11.c:430 (09:12:48):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:48):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:48):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[gs_fade_reset] gs-fade.c:865 (09:12:48):     Resetting fade
[gs_grab_release] gs-grab-x11.c:418 (09:12:48):     Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:48):     Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:244 (09:12:48):     Ungrabbing keyboard
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:48):     No XFree86-Misc extension present
[gs_job_stop] gs-job.c:483 (09:12:48):     stopping job
[gs_job_stop] gs-job.c:486 (09:12:48):     Could not stop job: pid not defined
[window_unmap_cb] gs-manager.c:1284 (09:12:48):     window unmapped!
[gs_window_dialog_finish] gs-window-x11.c:1472 (09:12:48):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1347 (09:12:48):     Keyboard finished
[gs_watcher_set_active] gs-watcher-x11.c:275 (09:12:48):     turning watcher: ON
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:221 (09:12:48):     Sending the ActiveChanged(FALSE) signal on the session bus
[gs_manager_set_lock_active] gs-manager.c:424 (09:12:58):     Setting lock active: 1
[gs_grab_grab_root] gs-grab-x11.c:521 (09:12:58):     Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:58):     Grabbing keyboard widget=11F
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:58):     Grabbing mouse widget=11F
[gs_manager_create_windows_for_screen] gs-manager.c:1651 (09:12:58):     Creating 1 windows for screen 0
[gs_manager_create_window_for_monitor] gs-manager.c:1461 (09:12:58):     Creating window for monitor 0 [0,0] (1366x768)
[update_geometry] gs-window-x11.c:430 (09:12:58):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:58):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[get_best_visual_for_screen] gs-window-x11.c:622 (09:12:59):     Found best GL visual for screen 0: 0xef
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:59):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[window_map_cb] gs-manager.c:1277 (09:12:59):     Handling window map event
[clear_widget] gs-window-x11.c:350 (09:12:59):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:59):     Clearing all child windows
[clear_widget] gs-window-x11.c:350 (09:12:59):     Clearing widget
[widget_clear_all_children] gs-window-x11.c:262 (09:12:59):     Clearing all child windows
[window_show_cb] gs-manager.c:1355 (09:12:59):     Handling window show
[apply_background_to_window] gs-manager.c:1304 (09:12:59):     Creating pixmap background w:1366 h:768
[gs_job_set_command] gs-job.c:193 (09:12:59):     Setting command for job: 'NULL'
[gs_watcher_set_active] gs-watcher-x11.c:275 (09:12:59):     turning watcher: OFF
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:221 (09:12:59):     Sending the ActiveChanged(TRUE) signal on the session bus
[gs_manager_set_lock_active] gs-manager.c:424 (09:12:59):     Setting lock active: 1
[set_status] gs-watcher-x11.c:345 (09:12:59):     GSWatcher: not active, ignoring status changes
[gs_window_xevent] gs-window-x11.c:801 (09:12:59):     not raising our windows
[window_map_event_cb] gs-manager.c:1264 (09:12:59):     Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1218 (09:12:59):     Moving grab to 0x816a008
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:59):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:361 (09:12:59):     Moving keyboard grab from 11F to 22000F4
[gs_grab_move_keyboard] gs-grab-x11.c:368 (09:12:59):     *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:244 (09:12:59):     Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:12:59):     Grabbing keyboard widget=22000F4
[gs_grab_move_keyboard] gs-grab-x11.c:390 (09:12:59):     *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:306 (09:12:59):     Moving pointer grab from 11F to 22000F4
[gs_grab_move_mouse] gs-grab-x11.c:313 (09:12:59):     *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:12:59):     Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:12:59):     Grabbing mouse widget=22000F4
[gs_grab_move_mouse] gs-grab-x11.c:336 (09:12:59):     *** releasing X server grab
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:59):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:59):     starting job
[gs_job_start] gs-job.c:450 (09:12:59):     No command set for job.
[gs_window_xevent] gs-window-x11.c:801 (09:12:59):     not raising our windows
[window_map_event_cb] gs-manager.c:1264 (09:12:59):     Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:1218 (09:12:59):     Moving grab to 0x816a008
[xorg_lock_smasher_set_active] gs-grab-x11.c:124 (09:12:59):     No XFree86-Misc extension present
[gs_grab_move_keyboard] gs-grab-x11.c:354 (09:12:59):     Window 22000F4 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:294 (09:12:59):     Window 22000F4 is already grabbed, skipping
[manager_maybe_start_job_for_window] gs-manager.c:216 (09:12:59):     Starting job for window
[gs_job_start] gs-job.c:435 (09:12:59):     starting job
[gs_job_start] gs-job.c:450 (09:12:59):     No command set for job.
[gs_window_xevent] gs-window-x11.c:801 (09:12:59):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:12:59):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:12:59):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:12:59):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[unfade_idle] gs-manager.c:1245 (09:12:59):     resetting fade
[gs_fade_reset] gs-fade.c:865 (09:12:59):     Resetting fade

[listener_service_deleted] gs-listener-dbus.c:1043 (09:13:16):     DBUS service deleted: :1.138

[listener_service_deleted] gs-listener-dbus.c:1043 (09:13:16):     DBUS service deleted: :1.139
[find_window_at_pointer] gs-manager.c:1177 (09:13:30):     Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1724 (09:13:30):     Requesting unlock
[window_dialog_up_cb] gs-manager.c:1086 (09:13:30):     Handling dialog up
[gs_grab_get_keyboard] gs-grab-x11.c:171 (09:13:30):     Grabbing keyboard widget=22000F4
[gs_grab_get_mouse] gs-grab-x11.c:206 (09:13:30):     Grabbing mouse widget=22000F4
[gs_grab_release_mouse] gs-grab-x11.c:267 (09:13:30):     Ungrabbing pointer
[window_dialog_up_cb] gs-manager.c:1109 (09:13:30):     Suspending jobs
[gs_job_suspend] gs-job.c:512 (09:13:30):     suspending job
[popup_dialog_idle] gs-window-x11.c:1666 (09:13:30):     Popping up dialog
[gs_window_clear_to_background_pixmap] gs-window-x11.c:309 (09:13:30):     Clearing window to background pixmap
[update_geometry] gs-window-x11.c:430 (09:13:30):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:13:30):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:13:30):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[error_watch] gs-window-x11.c:1072 (09:13:30):     command error output: [gs_debug_init] gs-debug.c:106 (09:13:30):     Debugging enabled

[gs_manager_request_unlock] gs-manager.c:1845 (09:13:30):     Request unlock but dialog is already up
[gs_manager_request_unlock] gs-manager.c:1845 (09:13:30):     Request unlock but dialog is already up

[listener_service_deleted] gs-listener-dbus.c:1043 (09:13:30):     DBUS service deleted:
[error_watch] gs-window-x11.c:1072 (09:13:31):     command error output: [auth_message_handler] gnome-screensaver-dialog.c:225 (09:13:31):     Got message style 1: 'Has&#322;o: '

[gs_window_raise] gs-window-x11.c:749 (09:13:31):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:820 (09:13:31):     not raising our windows
[gs_window_xevent] gs-window-x11.c:820 (09:13:31):     not raising our windows
[lock_command_watch] gs-window-x11.c:1561 (09:13:31):     command output: WINDOW ID=29360160

[error_watch] gs-window-x11.c:1072 (09:13:31):     command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:1193 (09:13:31):     Setting prompt to: Has&#322;o:

[gs_window_xevent] gs-window-x11.c:801 (09:13:31):     not raising our windows
[update_geometry] gs-window-x11.c:430 (09:13:31):     got geometry for monitor 0: x=0 y=0 w=1366 h=768
[update_geometry] gs-window-x11.c:443 (09:13:31):     using geometry for monitor 0: x=0 y=0 w=1366 h=768
[gs_window_move_resize_window] gs-window-x11.c:476 (09:13:31):     Move and/or resize window on monitor 0: x=0 y=0 w=1366 h=768
[gs_window_raise] gs-window-x11.c:749 (09:13:31):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:801 (09:13:31):     not raising our windows
[gs_window_xevent] gs-window-x11.c:801 (09:13:31):     not raising our windows
[error_watch] gs-window-x11.c:1072 (09:13:57):     command error output: [request_response] gnome-screensaver-dialog.c:153 (09:13:57):     got response: -2
<-- this is when gnome-screensaver got stuck and I killed it with killall
Zako&#324;czony
```

Next I found this thread: [http://ubuntuforums.org/showthread.php?t=776685](http://ubuntuforums.org/showthread.php?t=776685) but it's closed and the only work-around was to kill gnome-screensaver process. Maybe someone, this time, will got a better idea, so thank you in advance.
PS. I know that lucid is not supported anymore but dist-upgrade is not an option. And sorry for my English, I'm not using it too often.

---

