---
title: "Black screen at load up"
date: 2008-01-09
forum: General Help
---

### Post by grogger13 on 2008-01-09
I have an ati mobility x1400 video card and run compiz-fusion with xgl on Gutsy.  I have had unrelated problems with gutsy before and had to reinstall once.  On both fresh installs the gnome desktop has started up normally with the splash screen initially.  However after a couple start ups after the install i get an annoying bug at start up.

I get a black screen at the startup of the desktop environment that lingers around until after  the start up music goes off.  It usually continues to increase in time the longer the problem stays around.  It has gotten be as long as 30-60 seconds.

This problem drives me carzy and i have no idea what causes it.  When i went to linux i was  under the impression it wont slow down like windows, but this is not the case with this bug.

---

### Post by SeanTater on 2008-01-09
There are several logfiles in most linux systems which can help to clarify the source of problems like these. While I cannot immediately pinpoint the cause of this problem, you may want to look in a log named .xsession-errors (which is a hidden file in your home folder), or in the Xorg logs in /var/log.

Posting any interesting lines in these logs may help you or fellow posters to find a solution.

Alternatively, this could be the result of insufficient system specifications. Systems with low amounts of memory can suffer when the desktop loads. If this is the case, then Firefox and Openoffice should take an exceeding amount of time to load.

---

### Post by grogger13 on 2008-01-10
Haven't checked the log files, but the Mozilla does tend to load incredibly slowly and i dont open the oo.org programs as much but i always thought those loaded slowly from stuff i have read, maybe it was just my ram.

I have 1GB of ram in my laptop, i know thats not alot but i thought since im not running vista that 1 GB was more than enough, i might have to think about upgrading if i feel the load time is worth the price.



Here is the .xsession-errors file(not sure how to read it so im putting the whole thing up)
[HTML]
(process:6148): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6152): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/mikelaptop:/tmp/.ICE-unix/6145
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
Initializing gnome-mount extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
** Message: Not starting remote desktop server
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 3016 1199923200 1199920184
evolution-alarm-notify-Message:  Wed Jan  9 19:00:00 2008

evolution-alarm-notify-Message:  Wed Jan  9 18:09:44 2008

alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Wed Jan  9 19:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mike/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/mike/.evolution/calendar/local/system - Calendar Open Async... 0x80b7bb0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80cb860
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mike/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/mike/.evolution/tasks/local/system - Calendar Open Async... 0x80cd6d0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/mike/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/mike/.evolution/memos/local/system - Calendar Open Async... 0x80cd600
alarm-notify.c:393 (cal_opened_cb) file:///home/mike/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/mike/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/mike/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0xb4d00d38: Received at thread b4cffb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80b7bb0
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 18:09:45 2008
 to Wed Jan  9 18:09:45 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0xb4d00d38: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0xb4d06968: Received at thread b4cffb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80cd6d0
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 18:09:45 2008
 to Wed Jan  9 18:09:45 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0xb4d06968: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0xb4d01390: Received at thread b4cffb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80cd600
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 18:09:45 2008
 to Wed Jan  9 18:09:45 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0xb4d01390: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0xb4d013b0: R/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gnome-panel:6223): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -28 and height 24

(yelp:6399): Yelp-WARNING **: YelpDocument: Attempted to add an ID mapping from x-yelp-index to x-yelp-index, but x-yelp-index is already mapped.

(yelp:6399): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(yelp:6399): atk-bridge-WARNING **: IOR not set.

(yelp:6399): atk-bridge-WARNING **: Could not locate registry
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1199923200
eceived at thread b4cffb90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80cb860
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 18:09:45 2008
 to Wed Jan  9 18:09:45 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0xb4d013b0: Replied to GUI thread
alarm-queue.c:1832 (check_midnight_refresh)
alarm-queue.c:261 (midnight_refresh_cb) - Invoking task for midnight refresh
alarm-notify.c:349 (alarm_msg_received) - 0x80db880: Received at thread b4cffb90
alarm-queue.c:231 (midnight_refresh_async) 
alarm-queue.c:215 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 19:00:01 2008
 to Wed Jan  9 19:00:01 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:537 (load_alarms) - Disconnecting old queries 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-queue.c:215 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 19evolution-alarm-notify-Message: alarm.c:246: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1200009600 1199923200
evolution-alarm-notify-Message:  Thu Jan 10 19:00:00 2008

evolution-alarm-notify-Message:  Wed Jan  9 19:00:00 2008

:00:01 2008
 to Wed Jan  9 19:00:01 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:537 (load_alarms) - Disconnecting old queries 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-queue.c:215 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 19:00:01 2008
 to Wed Jan  9 19:00:01 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:537 (load_alarms) - Disconnecting old queries 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-queue.c:215 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan  9 19:00:01 2008
 to Wed Jan  9 19:00:01 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:537 (load_alarms) - Disconnecting old queries 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-queue.c:238 (midnight_refresh_async) - Reschedule the midnight update 
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Jan 10 19:00:00 2008
 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80db880: Re[/HTML]

---

