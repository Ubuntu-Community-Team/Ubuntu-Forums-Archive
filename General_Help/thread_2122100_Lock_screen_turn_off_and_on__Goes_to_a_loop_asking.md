---
title: "Lock screen turn off and on : Goes to a loop asking to enter password to unlock-"
date: 2013-03-04
forum: General Help
---

### Post by Vinyas on 2013-03-04
I recently updated my laptop from 12.04 to 12.10. And now,  whenever I lock screen with "CTRL+ALT+L", the screen locks, and monitor  turns off. But within 30 seconds, it turns on and asks for password.  After some time, it says 'Time expired' and turns off. This keeps  happening until my battery goes dead. :-1 


  Please assist me with this. 


  Also, I'm using Dell Inspiron 15R (5520) (no external graphics card).  Often the fan speed goes very high for sometime. If you have any  solution, please help me. Thanks.

---

### Post by carl4926 on 2013-03-04
This didn't happen with 12.04 at all?

When you lock the screen, do you want to monitor off?

Does the machine suspend OK?

---

### Post by Vinyas on 2013-03-04
I've used 12.04 for hardly 3 months and never had this problem. Yeah, I want my monitor off when I lock the screen. It does suspend.

---

### Post by carl4926 on 2013-03-04
> **Vinyas said:**
> I've used 12.04 for hardly 3 months and never had this problem. Yeah, I want my monitor off when I lock the screen. It does suspend.

See if .xsession-errors holds a clue

---

### Post by zero2xiii on 2013-03-04
Hay,

I have this issue with any media players. Totem and VLC has similar issues. Even if the video is paused (or audio for that matter), it keeps wanting to unlock the screen. Note that it also does not automatically lock the screen when one of the two players are open.

After doing the ctrl + alt + L, do a ctrl + alt + F1.

This should bring you to a tty log in prompt. Log in with the SAME user.

In this TTY session please run the following and post the outputs separately:
```
ps -ely
ps -ejH
ps -eLf | grep gnome
```

Assuming the problem is caused by a process, we should be able to see the culprit in the lists.

But for completeness please log out of the TTY (just type exit) and go back to your GUI, ctrl + alt +F7 normaly. (try 6 and 8 if 7 fails).
Unlock your screen lock and then open terminal (ctrl + alt + T) and run the following:
```

ps -e |grep gnome-screen
sudo kill *pid_of_process_above*
clear
gnome-screensaver --debug

```
Easy copy paste alternative:
 ```
pid=`ps -e | grep gnome-screen |cut -d' ' -f1`;sudo kill $pid; clear; gnome-screensaver --debug 
```

Now lock the screen as you do normaly (ctrl +alt + L) and leave the system alone.
Pay attention if the screen tries to unlock itself again.
If it does, unlock it manually but make sure to create your own dialogue (press esc twice and then type your password).
Please post the output of the above steps here aswell.

Example output from the above will look like this:
```
~/:~$ 
~/:~$ ps -e |grep gnome-screen
**16767** ?        00:00:00 gnome-screensav
~/:~$ sudo kill **16767**
[sudo] password for zeroburn: 
~/:~$ gnome-screensaver --debug
[gs_debug_init] gs-debug.c:106 (14:21:41):     Debugging enabled
[main] gnome-screensaver.c:86 (14:21:41):     initializing gnome-screensaver 3.4.1
[init_session_id] gs-listener-dbus.c:1473 (14:21:41):     Got session-id: /org/freedesktop/ConsoleKit/Session2
[gs_fade_init] gs-fade.c:920 (14:21:41):     Fade type: 2
[set_status] gs-watcher-x11.c:346 (14:21:41):     GSWatcher: not active, ignoring status changes
[gs_manager_set_lock_enabled] gs-manager.c:162 (14:21:41):     GSManager: lock-enabled=1
[gs_watcher_set_active] gs-watcher-x11.c:277 (14:21:41):     turning watcher: ON

[listener_dbus_handle_system_message] gs-listener-dbus.c:854 (14:21:41):     obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameAcquired destination=:1.127
[on_bg_changed] gs-manager.c:549 (14:21:41):     background changed
[gs_manager_set_lock_active] gs-manager.c:129 (14:21:48):     Setting lock active: 1
[gs_grab_grab_root] gs-grab-x11.c:536 (14:21:48):     Grabbing the root window
[gs_grab_get_keyboard] gs-grab-x11.c:153 (14:21:48):     Grabbing keyboard widget=15A
[gs_grab_get_mouse] gs-grab-x11.c:188 (14:21:48):     Grabbing mouse widget=15A
[gs_manager_create_windows_for_screen] gs-manager.c:1161 (14:21:48):     Creating 1 windows for screen 0
[gs_manager_create_window_for_monitor] gs-manager.c:984 (14:21:48):     Creating window for monitor 0 [0,0] (1600x900)
[update_geometry] gs-window-x11.c:325 (14:21:48):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:48):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:48):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:48):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:48):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[window_map_cb] gs-manager.c:766 (14:21:48):     Handling window map event
[window_show_cb] gs-manager.c:838 (14:21:48):     Handling window show
[apply_background_to_window] gs-manager.c:799 (14:21:48):     Creating background w:1600 h:900
[gs_watcher_set_active] gs-watcher-x11.c:277 (14:21:48):     turning watcher: OFF
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:184 (14:21:48):     Sending the ActiveChanged(TRUE) signal on the session bus
[gs_manager_set_lock_active] gs-manager.c:129 (14:21:48):     Setting lock active: 1
[set_status] gs-watcher-x11.c:346 (14:21:48):     GSWatcher: not active, ignoring status changes
[gs_window_xevent] gs-window-x11.c:576 (14:21:48):     not raising our windows
[window_map_event_cb] gs-manager.c:755 (14:21:48):     Handling window map_event event
[manager_maybe_grab_window] gs-manager.c:709 (14:21:48):     Moving grab to 0x1f660e0
[gs_grab_move_keyboard] gs-grab-x11.c:343 (14:21:48):     Moving keyboard grab from 15A to 3400007
[gs_grab_move_keyboard] gs-grab-x11.c:350 (14:21:48):     *** doing X server grab
[gs_grab_release_keyboard] gs-grab-x11.c:226 (14:21:48):     Ungrabbing keyboard
[gs_grab_get_keyboard] gs-grab-x11.c:153 (14:21:48):     Grabbing keyboard widget=3400007
[gs_grab_move_keyboard] gs-grab-x11.c:372 (14:21:48):     *** releasing X server grab
[gs_grab_move_mouse] gs-grab-x11.c:288 (14:21:48):     Moving pointer grab from 15A to 3400007
[gs_grab_move_mouse] gs-grab-x11.c:295 (14:21:48):     *** doing X server grab
[gs_grab_release_mouse] gs-grab-x11.c:249 (14:21:48):     Ungrabbing pointer
[gs_grab_get_mouse] gs-grab-x11.c:188 (14:21:48):     Grabbing mouse widget=3400007
[gs_grab_move_mouse] gs-grab-x11.c:318 (14:21:48):     *** releasing X server grab
[gs_window_xevent] gs-window-x11.c:588 (14:21:48):     not raising our windows
[update_geometry] gs-window-x11.c:325 (14:21:48):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:48):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:48):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:48):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:48):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:48):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[unfade_idle] gs-manager.c:736 (14:21:49):     resetting fade
[gs_fade_reset] gs-fade.c:861 (14:21:49):     Resetting fade
[find_window_at_pointer] gs-manager.c:668 (14:21:51):     Requesting unlock for screen 0
[gs_window_request_unlock] gs-window-x11.c:1522 (14:21:51):     Requesting unlock
[window_dialog_up_changed_cb] gs-manager.c:909 (14:21:51):     Handling window dialog up changed: up
[handle_window_dialog_up] gs-manager.c:851 (14:21:51):     Handling dialog up
[gs_grab_move_keyboard] gs-grab-x11.c:336 (14:21:51):     Window 3400007 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:276 (14:21:51):     Window 3400007 is already grabbed, skipping
[gs_grab_release_mouse] gs-grab-x11.c:249 (14:21:51):     Ungrabbing pointer
[popup_dialog] gs-window-x11.c:1458 (14:21:51):     Popping up dialog
[gs_window_clear_to_background_surface] gs-window-x11.c:260 (14:21:51):     Clearing window to background pixmap
[update_geometry] gs-window-x11.c:325 (14:21:51):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:51):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:51):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:51):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:51):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:51):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[error_watch] gs-window-x11.c:838 (14:21:51):     command error output: [gs_debug_init] gs-debug.c:106 (14:21:51):     Debugging enabled

[error_watch] gs-window-x11.c:838 (14:21:52):     command error output: [auth_message_handler] gnome-screensaver-dialog.c:229 (14:21:52):     Got message style 1: 'Password: '

[gs_manager_request_unlock] gs-manager.c:1337 (14:21:52):     Request unlock but dialog is already up
[gs_window_raise] gs-window-x11.c:524 (14:21:52):     Raising screensaver window
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[lock_command_watch] gs-window-x11.c:1363 (14:21:52):     command output: WINDOW ID=71303172

[error_watch] gs-window-x11.c:838 (14:21:52):     command error output: [gs_lock_plug_enable_prompt] gs-lock-plug.c:1272 (14:21:52):     Setting prompt to: Password:

[update_geometry] gs-window-x11.c:325 (14:21:52):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:52):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:52):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:52):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:52):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:52):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[gs_window_xevent] gs-window-x11.c:576 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:576 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:576 (14:21:52):     not raising our windows
[update_geometry] gs-window-x11.c:325 (14:21:52):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:52):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:52):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:52):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:52):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:52):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[gs_window_xevent] gs-window-x11.c:588 (14:21:52):     not raising our windows
[error_watch] gs-window-x11.c:838 (14:21:54):     command error output: 

[error_watch] gs-window-x11.c:838 (14:21:54):     command error output: (gnome-screensaver-dialog:16856): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.32.1/./gobject/gsignal.c:2572: instance `0x23d6010' has no handler with id `140'

[error_watch] gs-window-x11.c:838 (14:21:54):     command error output: [request_response] gnome-screensaver-dialog.c:157 (14:21:54):     got response: -2

[error_watch] gs-window-x11.c:838 (14:21:54):     command error output: [do_auth_check] gnome-screensaver-dialog.c:303 (14:21:54):     Verify user returned: TRUE

[lock_command_watch] gs-window-x11.c:1363 (14:21:54):     command output: RESPONSE=OK

[lock_command_watch] gs-window-x11.c:1377 (14:21:54):     Got OK response
[gs_window_dialog_finish] gs-window-x11.c:1239 (14:21:54):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1116 (14:21:54):     Keyboard finished
[window_dialog_up_changed_cb] gs-manager.c:909 (14:21:54):     Handling window dialog up changed: down
[handle_window_dialog_down] gs-manager.c:883 (14:21:54):     Handling dialog down
[gs_grab_move_keyboard] gs-grab-x11.c:336 (14:21:54):     Window 3400007 is already grabbed, skipping
[gs_grab_move_mouse] gs-grab-x11.c:291 (14:21:54):     Getting pointer grab on 3400007
[gs_grab_move_mouse] gs-grab-x11.c:295 (14:21:54):     *** doing X server grab
[gs_grab_get_mouse] gs-grab-x11.c:188 (14:21:54):     Grabbing mouse widget=3400007
[gs_grab_move_mouse] gs-grab-x11.c:318 (14:21:54):     *** releasing X server grab
[update_geometry] gs-window-x11.c:325 (14:21:54):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:54):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:54):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:325 (14:21:54):     got geometry for monitor 0: x=0 y=0 w=1600 h=900
[update_geometry] gs-window-x11.c:338 (14:21:54):     using geometry for monitor 0: x=0 y=0 w=1600 h=900
[gs_window_move_resize_window] gs-window-x11.c:371 (14:21:54):     Move and/or resize window on monitor 0: x=0 y=0 w=1600 h=900
[gs_fade_reset] gs-fade.c:861 (14:21:54):     Resetting fade
[gs_grab_release] gs-grab-x11.c:399 (14:21:54):     Releasing all grabs
[gs_grab_release_mouse] gs-grab-x11.c:249 (14:21:54):     Ungrabbing pointer
[gs_grab_release_keyboard] gs-grab-x11.c:226 (14:21:54):     Ungrabbing keyboard
[gs_window_dialog_finish] gs-window-x11.c:1239 (14:21:54):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1116 (14:21:54):     Keyboard finished
[window_unmap_cb] gs-manager.c:773 (14:21:54):     window unmapped!
[gs_watcher_set_active] gs-watcher-x11.c:277 (14:21:54):     turning watcher: ON
[gs_listener_send_signal_active_changed] gs-listener-dbus.c:184 (14:21:54):     Sending the ActiveChanged(FALSE) signal on the session bus
[gs_window_dialog_finish] gs-window-x11.c:1239 (14:21:54):     Dialog finished
[keyboard_command_finish] gs-window-x11.c:1116 (14:21:54):     Keyboard finished
^C
~/:~$ 

```
The ^C at the end means I "ctrl + C"ed out of the running process in shell.

Please also add the output of:
```
tail ./.xsession-errors
```

Post the output of the above and we will try and assist you. :)

Cherz and good luck.

---

### Post by varunendra on 2013-03-04
Welcome to the forums Vinyas! :)

I'm interested in any updates.
For reference : [http://askubuntu.com/questions/263800/lock-screen-turn-off-and-on-goes-to-a-loop-asking-to-enter-password-to-unlock](http://askubuntu.com/questions/263800/lock-screen-turn-off-and-on-goes-to-a-loop-asking-to-enter-password-to-unlock)

Let us know if that solves your problem permanently or if you need further assistance.

---

