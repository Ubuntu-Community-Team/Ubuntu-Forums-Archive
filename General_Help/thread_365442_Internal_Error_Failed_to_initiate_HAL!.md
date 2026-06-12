---
title: "Internal Error: Failed to initiate HAL!"
date: 2007-02-19
forum: General Help
---

### Post by cwmccabe on 2007-02-19
I recently installed Edgy Eft and have occasionally seen the following error after booting up:

[INDENT]**Internal Error: Failed to initiate HAL!**[/INDENT]

Each time, I have been able to just ignore it and keep on working with no problem.  However, I'm worried that this may be a symptom of something else.  Can someone tell me if this could indicate a larger problem and/or how to fix it?  Also, I can post more info if you let me know what output to provide.

Thanks!

---

### Post by dcstar on 2007-02-19
> **cwmccabe said:**
> I recently installed Edgy Eft and have occasionally seen the following error after booting up:

[INDENT]**Internal Error: Failed to initiate HAL!**[/INDENT]

Each time, I have been able to just ignore it and keep on working with no problem.  However, I'm worried that this may be a symptom of something else.  Can someone tell me if this could indicate a larger problem and/or how to fix it?  Also, I can post more info if you let me know what output to provide.

Thanks!

This is usually fixed by updates to various modules, is your system fully updated?

---

### Post by emarkay on 2007-02-19
I just couldn't resist this one...

"I'm sorry Dave, I'm afraid I just can't do that now"...  :)

---

### Post by wiesiek_h on 2007-02-21
I too started to see this error once I upgraded to 2.6.17-11 kernel.   Don't know how to diagnose.

---

### Post by Redeyes_Gambit on 2007-02-21
Does this, per chance, happen after your system does a scheduled disk scan? This happens after 30 boots or so and I noticed that HAL fails right after.

So long as HAL doesn't start singing about Daisy I think all should be well ;-)

---

### Post by drtvasudevan on 2007-02-22
> **Redeyes_Gambit said:**
> Does this, per chance, happen after your system does a scheduled disk scan? This happens after 30 boots or so and I noticed that HAL fails right after. ;-)

yes, it did just so. failed to intialise HAL after fs check
in my case i find the usb drive or cd is not mounted in /media
(dvd recorder)
and my system is updated regularly.
tv
added: curiously it is happening only in the 386 version and not in my 64bit version

---

### Post by Brandonson112 on 2007-08-01
Sorry to resurresct a dead thread but im getting this same error and it unables me to use my wireless card which upsets me.  Is there any solution to this problem?

---

### Post by GadgetsGuy on 2007-08-06
Bump for an answer please anybody?

I installed Nvidia drivers and Beryl (both working fine) and have had **HAL failed to initiate** ever since!

It seems my CDRW and my DVD ROM are not mounted ... 

Somebody told me to reinstall dbus ... same problem ... tried to uninstall dbus and reinstall, but half the damn computer is dependent on dbus, so I 86'ed that real fast! :(

I am loving the proper Nvidia drivers, and Beryl freakin ROKKS ... I just need to fix this **HAL failed to initiate** problem  :confused:

---

### Post by Raymond Clark on 2007-08-06
My Ubuntu just started to do this after installing some themes, however when i restarted, the HAL failed to initialize message appeared.  I fixed it by going into the synaptic package manager and reinstalling the following packages:

hal
hal-device-manager
hal-info

this seemed to work for me so its worth a try.

---

### Post by p388l3s on 2007-08-06
actually the quick fix would be to start dbus by going into a terminal:

Type

sudo /etc/init.d/dbus restart

then go into (System) -> (Administration) -> (Services)

Look thru the list of services and see if [Systems Communication Bus (dbus)] is checked to start if not then that is the problem, just check it and restart for effect, or lack thereof ;-)

I just had to fix this myself and was quite surprised at how easy it was.

:)

---

### Post by GadgetsGuy on 2007-08-06
> **p388l3s said:**
> actually the quick fix would be to start dbus by going into a terminal:

Type

sudo /etc/init.d/dbus restart

then go into (System) -> (Administration) -> (Services)

Look thru the list of services and see if [Systems Communication Bus (dbus)] is checked to start if not then that is the problem, just check it and restart for effect, or lack thereof ;-)

I just had to fix this myself and was quite surprised at how easy it was.

:)

I tried restarting dbus from a terminal, and I get exactly the same thing I get during the boot sequence:

* Stopping System Tools Backends system-tools-backends                  [ OK ] 

 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 

 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 

 * Stopping network connection manager NetworkManager                    [ OK ] 

 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 

 * Stopping Hardware abstraction layer hald                              [ OK ] 

 * Stopping system message bus dbus                                      [ OK ] 

 * Starting system message bus dbus                                      [ OK ] 

 * Starting Hardware abstraction layer hald                                     
**[color=red]run-parts: /etc/dbus-1/event.d/20hal exited with return code 1[/color]**

 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 

 * Starting network connection manager NetworkManager                    [ OK ] 

 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 

 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 

 * Starting System Tools Backends system-tools-backends                     [OK]


Any ideas?


BTW ... in System>>Admin>>Services  dbus is checked (System communication bus (dbus))

---

### Post by GadgetsGuy on 2007-08-06
> **Raymond Clark said:**
> My Ubuntu just started to do this after installing some themes, however when i restarted, the HAL failed to initialize message appeared.  I fixed it by going into the synaptic package manager and reinstalling the following packages:

hal
hal-device-manager
hal-info

this seemed to work for me so its worth a try.


I tried this too with no joy :(

---

### Post by GadgetsGuy on 2007-08-06
if it helps .... my network connection icon in the notifications area has a red X that says NO NETWORK CONNECTIONS when I mouse over it ... even though I do connect to the net      :confused:

---

### Post by GadgetsGuy on 2007-08-06
I am about to uninstall the whole thing and try again ... but I used WUBI and am not quite sure how to uninstall it.    :(

I am hoping I wont have to do this though, because that will mean that 1½ days setting this machine up was a waste of time ...

At this point, I would even be willing to **PAY SOMEBODY** to fix this for me!!! 

Reply here if interested ...

---

### Post by GadgetsGuy on 2007-08-07
well ... I gave up!

I have uninstalled WUBI and am now trying to install feisty with a live CD and manual partitioning ...

wish me luck ... first try ended with FATAL ERROR: could not write GRUB to (hd0)

it seems my hard drive is called sda, so I went into advanced options and told it to install GRUB in sda


We'll see what happens .... if this install goes to hell, that is all the time I have to play with  Linux for another few months ... days of ZERO PRODUCTIVITY wont pay my bills.  :(

---

### Post by GadgetsGuy on 2007-08-07
FOR @#$% SAKES !!!

at 94% Ubuntu gave me another FATAL ERROR!

Executing 'grub-install (sda)' failed.  This is a fatal error.


So screw this ... I am a windows guy for yet another few months


AS much as I love Linux, is it NOT ANYWHERE NEAR READY for mainstream use.

:mad:


UPDATE:

in trying to convert my XP Pro partition to FAT32, gparted erased my who @#$%ing disk ...... LOVELY!
I reinstalled a BRAND NEW FRESH Win XP .... and again treid to install Ubuntu 7.0.4

AGAIN it got to 94% and gave me a fatal error -- Could not write grub to (sda1) which is my (now FAT32 WinXP partition)

Anybody have any clue what the hell is going on??  How is Linux ever going to become more than an OS for geeks to mess around with, if nobody can install it ???  and I have 9 years of computer experience .... I am not a dummy!


I'm very pissed off and frustrated at the time I have spent (4 tries now) to install Ubuntu ...

WHAT AM I DOING WRONG ???????????????????????????????????

(I have set up Ubuntu successfully in the past on probably 5 machines)

---

### Post by GadgetsGuy on 2007-08-07
since I lost my entire WinXP drive, I cannot do any of my other work anyways .... I decided to give it another try .... 

I finally got ubuntu installed and working flawlessly ... but after installing codecs and fonts and the like with Automatix, the orange UPDATES AVAILABLE icon lit up in the notification area .... there were 9 updates, and one was Hardware Abstraction Layer .... 

Well you guessed it ....... the update broke my friggin HAL again, and I now cannot mount my CD nor my DVD ROM

Is there any way to reverse an update ????


:popcorn::popcorn::popcorn:

---

### Post by ashishgoel on 2007-08-08
yes GadgetsGuy, I'm also having exact similiar problems after updating the HAL-update  -. cannot mount the drives, Network shows all connection but network connection icon in the notifications area has a red X that says NO NETWORK CONNECTIONS when I mouse over it ... even though I do connect to the net.... though not able to use Wireless one...

I also tried solution to stop/restart/re-install HAL but all in vein.....  I'm also usin wubi for ubuntu, didn't had any probs before HAL-UPDATE....

Please, HELP us anybody....

---

### Post by ashishgoel on 2007-08-08
it gets solved... ---


Re: the infamous Failed to initialize hal error

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update via Ubuntus automatic update system (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes"

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

---

### Post by drtvasudevan on 2007-08-09
wow!
i did not know this force version feature existed.
thanks
btw perhaps you can use the lock version feature that is in the same menu too so that no accidental update occurs.

tv

---

### Post by Thiago Cesar Vieira on 2007-12-07
Good...

I had the same problem... I was trying to disable some **services** - Menu Administration - Services -, and clicked in **Systems Communication Bus (DBus)** - like p388l3s said to maintain checked.
Instantly I had a crash. Started with this window message "*Failed to initialize HAL*" and I couldn't connect to internet, neither reboot my machine and neither undo my stupid action! When I was trying to access some **Administration option**:
[I]The configuration could not be loaded
You are not allowed to access the system configuration.[/I]
The smart Ubuntu was locking the system!!

When I manually rebooted:
*starting avahi mDNS/DNS-SD Daemon avahi-daemon         [fail]*

I had to [run]("http://ubuntuforums.org/showthread.php?t=354877"):
[I]# update-rc.d -f dbus remove
# update-rc.d dbus defaults 12[/I]

At the end, I had to start **Dbus service before HAL**:
[I]$ ls -l /etc/rc2.d/
...
lrwxrwxrwx 1 root root  16 2007-11-28 00:17 S11dbus -> /etc/init.d/dbus
lrwxrwxrwx 1 root root  13 2007-11-25 11:47 S12hal -> ../init.d/hal
...[/I]

It works! I would like to suggest that a important service like Dbus is removed of that list.


Bye friends!

---

### Post by liquidcable on 2007-12-24
> **Thiago Cesar Vieira said:**
> 
# sudo update-rc.d -f dbus remove
# sudo update-rc.d dbus defaults 12
Bye friends!

This worked for me.  It seems to be "race condition" between the dbus and hal demon.  Don't know how my system got screwed up, but this seems to be something that the developers should have caught.

---

### Post by StGermain on 2007-12-29
I was so dumb to disable dbus in services as well. Reinstalling hal and dbus didn't work as dbus was in /etc/rc2.d as S50dbus and hal was as S12hal.

Doing a sudo mv S50dbus S11dbus fixed the problem.

---

### Post by BLTicklemonster on 2008-01-10
Wow, I show no services whatsoever. nada.

Rebooted, got the error again, ran sudo /etc/init.d/dbus restart again, and now I see services, but nothing in there having anything to do with communication or hal, dbus, de plane boss de plane, or anything like that.

---

### Post by BLTicklemonster on 2008-01-13
> **Thiago Cesar Vieira said:**
> Good...

I had the same problem... I was trying to disable some **services** - Menu Administration - Services -, and clicked in **Systems Communication Bus (DBus)** - like p388l3s said to maintain checked.
Instantly I had a crash. Started with this window message "*Failed to initialize HAL*" and I couldn't connect to internet, neither reboot my machine and neither undo my stupid action! When I was trying to access some **Administration option**:
[I]The configuration could not be loaded
You are not allowed to access the system configuration.[/I]
The smart Ubuntu was locking the system!!

When I manually rebooted:
*starting avahi mDNS/DNS-SD Daemon avahi-daemon         [fail]*

I had to [run]("http://ubuntuforums.org/showthread.php?t=354877"):
[I]# update-rc.d -f dbus remove
# update-rc.d dbus defaults 12[/I]

At the end, I had to start **Dbus service before HAL**:
[I]$ ls -l /etc/rc2.d/
...
lrwxrwxrwx 1 root root  16 2007-11-28 00:17 S11dbus -> /etc/init.d/dbus
lrwxrwxrwx 1 root root  13 2007-11-25 11:47 S12hal -> ../init.d/hal
...[/I]

It works! I would like to suggest that a important service like Dbus is removed of that list.


Bye friends!

I boot with the hal error message, but dbus already boots before hal:

lrwxrwxrwx 1 root root  14 2008-01-13 08:58 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2008-01-08 15:41 S12hal -> ../init.d/hal

I have to run 

 sudo /etc/init.d/dbus restart

every time I boot in order to have connectivity. I'm about to try a rollback.

Appears I'd have to remove hal and others, but they want to take everything and the kitchen sink with them, too, not sure about that.

I can't use the LAN with this hal error even after dbus restart.

is there an actual fix for this?

---

### Post by BLTicklemonster on 2008-01-23
I've still got nothing. Would my xsession errors help?

```

(process:5546): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
SESSION_MANAGER=local/bill-desktop:/tmp/.ICE-unix/5543
Window manager warning: Failed to read saved session file /home/bill/.metacity/sessions/default0.ms: Failed to open file '/home/bill/.metacity/sessions/default0.ms': No such file or directory
Conky: /home/bill/.conkyrc: 17: no such configuration: 'on_bottom'
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 23575 1201150800 1201127225
evolution-alarm-notify-Message:  Thu Jan 24 00:00:00 2008

evolution-alarm-notify-Message:  Wed Jan 23 17:27:05 2008

Initializing gnome-mount extension

** (nautilus:5604): WARNING **: Failed to initialize libhal context: (null) : (null)

** (nautilus:5604): WARNING **: Could not initialize hal context

Shutting down gnome-mount extension
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Thu Jan 24 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/bill/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/bill/.evolution/calendar/local/system - Calendar Open Async... 0x80bc980
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80cde80
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/bill/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/bill/.evolution/tasks/local/system - Calendar Open Async... 0x80d3800
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/bill/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/bill/.evolution/memos/local/system - Calendar Open Async... 0x80d5c20
alarm-notify.c:393 (cal_opened_cb) file:///home/bill/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/bill/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d92d0: Received at thread b4daab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80bc980
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan 23 17:27:11 2008
 to Wed Jan 23 17:27:11 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d92d0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x80d1058: Received at thread b4daab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d3800
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan 23 17:27:11 2008
 to Wed Jan 23 17:27:11 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d1058: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/bill/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80b6cc8: Received at thread b4daab90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80d5c20
alarm-queue.c:581 (load_alarms_for_today) - From Wed Jan 23 17:27:11 2008
 to Wed Jan 23 17:27:11 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80b6cc8: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80d30e0: Received
(gnome-panel:5603): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

** (update-notifier:5625): WARNING **: hal_initialize failed: (null)

Conky: forked to background, pid is 5763

Conky: desktop window (e000bd) is subwindow of root window (187)
Conky: window type - override
Conky: drawing to created window (1600002)
Conky: drawing to double buffer
sh: sensors: not found
X Error of failed request:  189
  Major opcode of failed request:  161 (DAMAGE)
  Minor opcode of failed request:  3 (XDamageSubtract)
  Serial number of failed request:  11800
  Current serial number in output stream:  11801

(nautilus:5981): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Initializing gnome-mount extension

** (nautilus:5981): WARNING **: Cannot connect to system bus: org.freedesktop.DBus.Error.FileNotFound : Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

** (nautilus:5981): WARNING **: Could not initialize hal context

Shutting down gnome-mount extension

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 0'

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 0'

(gecko:11139): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 0', text='English Hello'

(gecko:11139): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 0'

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Verdana 0'

(gecko:11139): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Verdana 0', text='English Hello'

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans Bold 0'

(gecko:11139): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Sans Bold 0'

(gecko:11139): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Sans Bold 0', text='English Hello'

(gecko:11139): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:11139): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gecko:11139): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gecko:11139): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gecko:11139): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:11139): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:11139): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:11139): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:11139): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:11139): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:11139): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:2180: invalid unclassed object pointer for value type `GdkScreen'

(gecko:11139): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:11139): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:11139): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:2180: invalid unclassed object pointer for value type `GdkScreen'

(gecko:11139): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

---

### Post by BLTicklemonster on 2008-01-26
Strangest danged thing just happened.

I was looking over this thread:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

when I noticed this:

> **Note**
For all of those that having HAL failure problem, try this:
1. change acpi-support from S to 2,3,4,5
2. change acpid from S to 2,3,4,5
3. change dbus from S to 2,3,4,5
4. Reboot. Go to the console and do

Guess what? Mine were all set to 2,3,4,5 already.

So being the nut I am, I set them to S.

Rebooted, and now have no problem with HAL.

Total shot in the dark. Wasn't looking for anything about HAL, just lucked up on it.

Weeeeee!!!!

---

### Post by kmepartaunrayo on 2008-01-31
> **BLTicklemonster said:**
> Strangest danged thing just happened.

I was looking over this thread:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

when I noticed this:



Guess what? Mine were all set to 2,3,4,5 already.

So being the nut I am, I set them to S.

Rebooted, and now have no problem with HAL.

Total shot in the dark. Wasn't looking for anything about HAL, just lucked up on it.

Weeeeee!!!!

  THAT SOLVED IT FOR ME!!!!! THANK YOU THANK YOU THANK YOU! :D!! and i thought i was goin to have to do a complete reinstall :(!!

---

### Post by BLTicklemonster on 2008-02-01
No problem. I was totally bumfuzzled when I found that it worked. I wonder if it's like "the fix" everyone with the hal error can use or not? Sure would be nice if it is this easy.

:guitar:

---

### Post by NorbertBroadsword on 2008-02-03
I also had the HAL issue and mine was down to fiddling about trying to speed up the boot process. Turned out in my case that a change I had made to the rc file in /etc/init.d had totally shafted everything. The change was meant to parallelise some of the services loading and thus make booting quicker.

in /etc/init.d/rc I had changed CONCURRENCY=none to CONCURRENCY=shell which obviously loaded the services in the wrong order for the system to bring itself up properly. Changing it back to CONCURRENCY=none fixed the problem for me

Incidentally, changing back has not actually made booting any quicker really!

---

### Post by rZeta on 2008-02-12
> **BLTicklemonster said:**
> Strangest danged thing just happened.

I was looking over this thread:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

when I noticed this:



Guess what? Mine were all set to 2,3,4,5 already.

So being the nut I am, I set them to S.

Rebooted, and now have no problem with HAL.

Total shot in the dark. Wasn't looking for anything about HAL, just lucked up on it.

Weeeeee!!!!

This worked for me too!!! :-D. That HAL problem was driving me crazy.
Thx man!

---

### Post by BLTicklemonster on 2008-02-12
:) Sweet!

---

### Post by Nickay on 2008-02-16
> **BLTicklemonster said:**
> Strangest danged thing just happened.

I was looking over this thread:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

when I noticed this:



Guess what? Mine were all set to 2,3,4,5 already.

So being the nut I am, I set them to S.

Rebooted, and now have no problem with HAL.

Total shot in the dark. Wasn't looking for anything about HAL, just lucked up on it.

Weeeeee!!!!

Thanks man. This worked for me too.

---

### Post by deadguy87 on 2008-03-11
> **Thiago Cesar Vieira said:**
> Good...

I had the same problem... I was trying to disable some **services** - Menu Administration - Services -, and clicked in **Systems Communication Bus (DBus)** - like p388l3s said to maintain checked.
Instantly I had a crash. Started with this window message "*Failed to initialize HAL*" and I couldn't connect to internet, neither reboot my machine and neither undo my stupid action! When I was trying to access some **Administration option**:
[I]The configuration could not be loaded
You are not allowed to access the system configuration.[/I]
The smart Ubuntu was locking the system!!

When I manually rebooted:
*starting avahi mDNS/DNS-SD Daemon avahi-daemon         [fail]*

I had to [run]("http://ubuntuforums.org/showthread.php?t=354877"):
[I]# update-rc.d -f dbus remove
# update-rc.d dbus defaults 12[/I]

At the end, I had to start **Dbus service before HAL**:
[I]$ ls -l /etc/rc2.d/
...
lrwxrwxrwx 1 root root  16 2007-11-28 00:17 S11dbus -> /etc/init.d/dbus
lrwxrwxrwx 1 root root  13 2007-11-25 11:47 S12hal -> ../init.d/hal
...[/I]

It works! I would like to suggest that a important service like Dbus is removed of that list.


Bye friends!

millions of thanks to you that fixed it for me also.

---

### Post by jwvans on 2008-05-09
i'm bit of a newbie so im not sure this will help any (senior) linux/ubuntu users. still...it's always worth a shot.

i got the same message whenever starting or rebooting my system. was also unable to mount my cd/dvd-drive.

i fiddled a bit around, more seriously after i got messages on screen that there was no final newline at the etc/fstab. this brought me to figure out what was the drive hardware-id and checking it against the etc/fstab file. i put in the systems hardware-ID for my r/rw cd/dvd-drive (which was 'scd0') instead of whatever was in the fstab. u can find this in the '/dev/cdrom' properties

worked for me!! \\:D/

cu, Jim

---

