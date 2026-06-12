---
title: "Password Incorrect Message at Login Screen - Have to Enter PW Twice"
date: 2013-08-05
forum: General Help
---

### Post by fortitude on 2013-08-05
Hi everyone. :) I'm hoping someone can help me diagnose this issue.

The problem is that when I log in I get a password incorrect error message when I know I have entered it correctly.

I'm on Ubuntu 12.04 LTS AMD64.

Processor: quad core AMD
Ram : 4 GB
Video card: Nvidia GT 545 GDDR5 with the recommended proprietary driver from System Settings/Additional Drivers (304.88).
Hard disks: Samsung SSD, Samsung 7200 RPM storage drive (not mounted), Seagate 7200 RPM storage drive (mounted with fstab at boot).
Network: static internal network IP assigned to system, other systems on network run Windows, one folder shared via Samba.
User accounts: Only one account.

Things I have tried: Fresh install of Ubuntu 13.04. Fresh install of 12.04 LTS again (current). Deleting .Xauthority, various versions of video card driver, various files removed, patched and installed as suggested in other threads.

The odd thing is it was working fine for so long on this same hardware.

Please help. :) Thank you.

---

### Post by carl4926 on 2013-08-06
It would seem unlikely to be hardware related.
Just out of interest, what happens if you set it to auto login?

---

### Post by Mal_Ellis on 2013-08-06
Hi Fortitude. This is the same thing that happens to me and I sometimes have to change the passowrd which is a pain. It seems to be something to do with the latest Kernel as it started to happen to me just after the Kernel was last upgraded. Sorry I can't be of more help.

---

### Post by fortitude on 2013-08-06
> **carl4926 said:**
> Just out of interest, what happens if you set it to auto login?

Thanks for your reply, Carl. I tested your suggestion, it just boots right up into the desktop environment.

I'd like to have the extra security of having to log in though (just once of course). :)

I did notice that when I went to change back the auto-login option that the password was rejected the first time to unlock the user accounts settings. This did not happen when auto-login was set to off, presumably because the double password hassle had already been taken care of at the login screen.

---

### Post by fortitude on 2013-08-06
> **Mal_Ellis said:**
> Hi Fortitude. This is the same thing that happens to me and I sometimes have to change the passowrd which is a pain. It seems to be something to do with the latest Kernel as it started to happen to me just after the Kernel was last upgraded. Sorry I can't be of more help.

Hi there. :)

I did notice there was recently an update to kernel 3.5.0-37 but I think the issue was seen before that (but I could be wrong).

I hope to learn about additional troubleshooting steps that I can take (this is a general comment to the thread, not to you specifically, Mal_Ellis.) :)

---

### Post by fortitude on 2013-08-06
I thought I'd add that login works the first try with the onscreen keyboard, in case that's a clue!

---

### Post by fortitude on 2013-08-06
Here is the output of /var/log/lightdm when the issue presents itself:

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1156
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1185: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.69s] DEBUG: Got signal 10 from process 1185
[+0.69s] DEBUG: Got signal from X server :0
[+0.69s] DEBUG: Stopping Plymouth, X server is ready
[+0.72s] DEBUG: Connecting to XServer :0
[+0.72s] DEBUG: Starting greeter
[+0.72s] DEBUG: Started session 1421 with service 'lightdm', username 'lightdm'
[+0.76s] DEBUG: Session 1421 authentication complete with return value 0: Success
[+0.76s] DEBUG: Greeter authorized
[+0.76s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+0.76s] DEBUG: Session 1421 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+0.87s] DEBUG: Greeter connected version=1.2.3
[+0.87s] DEBUG: Greeter connected, display is ready
[+0.87s] DEBUG: New display ready, switching to it
[+0.87s] DEBUG: Activating VT 7
[+1.55s] DEBUG: Greeter start authentication for [my user name]
[+1.55s] DEBUG: Started session 1734 with service 'lightdm', username '[my user name]'
[+1.56s] DEBUG: Session 1734 got 1 message(s) from PAM
[+1.56s] DEBUG: Prompt greeter with 1 message(s)
[+9.55s] DEBUG: Continue authentication
[+11.72s] DEBUG: Session 1734 authentication complete with return value 7: Authentication failure
[+11.72s] DEBUG: Authenticate result for user [my user name]: Authentication failure
[+11.72s] DEBUG: Session 1734 exited with return value 1
[+11.72s] DEBUG: Greeter start authentication for [my user name]
[+11.72s] DEBUG: Started session 1926 with service 'lightdm', username '[my user name]'
[+11.73s] DEBUG: Session 1926 got 1 message(s) from PAM
[+11.73s] DEBUG: Prompt greeter with 1 message(s)
[+14.84s] DEBUG: Continue authentication
[+14.89s] DEBUG: Session 1926 authentication complete with return value 0: Success
[+14.89s] DEBUG: Authenticate result for user [my user name]: Success
[+14.90s] DEBUG: User [my user name] authorized
[+14.90s] DEBUG: Greeter requests session ubuntu
[+14.90s] DEBUG: Using session ubuntu
[+14.90s] DEBUG: Stopping greeter
[+14.90s] DEBUG: Session 1421: Sending SIGTERM
[+14.93s] DEBUG: Greeter closed communication channel
[+14.93s] DEBUG: Session 1421 exited with return value 0
[+14.93s] DEBUG: Greeter quit
[+14.95s] DEBUG: Dropping privileges to uid 1000
[+14.95s] DEBUG: Restoring privileges
[+14.96s] DEBUG: Dropping privileges to uid 1000
[+14.96s] DEBUG: Writing /home/[my user name]/.dmrc
[+14.97s] DEBUG: Restoring privileges
[+14.97s] DEBUG: Starting session ubuntu as user [my user name]
[+14.97s] DEBUG: Session 1926 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+14.99s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
```

And here is the output of .xsession-errors:
```

Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
** Message: applet now removed from the notification area
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/home/[my user name]/.compiz/session/1096a1e35320278de113758175411134000000019730034"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2039): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed

(gnome-settings-daemon:2023): color-plugin-WARNING **: failed to reset xrandr-Acer Technologies-Acer H9500BD-JDG010085901 gamma tables: gamma size is zero
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:2462): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
```

I could try unplugging the Acer easily enough, but no idea about the I/O error.

---

### Post by fortitude on 2013-08-06
Log /var/log/lightdm/x-0-greeter.log

```
Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:895: Starting unity-greeter 0.2.9 UID=104 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:898: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:902: Creating background surface
[+0.00s] DEBUG: unity-greeter.vala:905: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:933: Setting GTK+ settings
Successfully activated service 'org.a11y.atspi.Registry'

**  (at-spi2-registryd:1531): WARNING **: Failed to register client:  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:1531): WARNING **: Unable to register client with session manager
[+0.03s] DEBUG: unity-greeter.vala:956: Creating Unity Greeter
[+0.03s] DEBUG: Connecting to display manager...
[+0.03s] DEBUG: Wrote 17 bytes to daemon
[+0.03s] DEBUG: Read 8 bytes from daemon
[+0.03s] DEBUG: Read 120 bytes from daemon
[+0.03s] DEBUG: Connected version=1.2.3 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.08s] DEBUG: menubar.vala:359: LANG=en_US.UTF-8 LANGUAGE=(null)

** (python:1555): WARNING **: (../../atk-adaptor/bridge.c:793):adaptor_init: runtime check failed: (root)
[+0.52s] CRITICAL: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
[+0.54s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.54s] DEBUG: get entries
[+0.54s] DEBUG: menubar.vala:541: Adding indicator object 0x2554078 at position 0
[+0.54s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.54s] DEBUG: Checking against 2 possible times
[+0.55s] DEBUG: Guessing max time width: 62
[+0.55s] DEBUG: get entries
[+0.55s] DEBUG: menubar.vala:541: Adding indicator object 0x25cc1b8 at position 1
[+0.55s] WARNING: IndicatorObject class does not have an accessible description.
[+0.56s] WARNING: IndicatorObject class does not have an accessible description.
[+0.56s] DEBUG: get entries
[+0.56s] DEBUG: get entries
[+0.56s] DEBUG: menubar.vala:541: Adding indicator object 0x26440a8 at position 2
[+0.56s] DEBUG: menubar.vala:365: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.56s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.56s] DEBUG: Ignoring session /usr/share/xsessions/gnome-shell.desktop
[+0.56s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.56s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.56s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.56s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.64s] DEBUG: Setting keyboard layout to 'us'
[+0.67s] DEBUG: main-window.vala:98: Screen is 1920x1080 pixels
[+0.67s] DEBUG: main-window.vala:104: Monitor 0 is 1920x1080 pixels at 0,0
[+0.68s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.68s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.70s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.70s] DEBUG: unity-greeter.vala:332: Adding/updating user [my user name] ([my full name])
[+0.70s] DEBUG: unity-greeter.vala:189: Adding guest account entry
[+0.71s] DEBUG: Starting authentication for user [my user name]...
[+0.71s] DEBUG: Wrote 19 bytes to daemon
[+0.71s] DEBUG: unity-greeter.vala:959: Showing greeter
[+0.71s] DEBUG: unity-greeter.vala:357: Showing main window
[+0.71s] DEBUG: New style for time label
[+0.71s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.71s] DEBUG: Checking against 2 possible times
[+0.71s] DEBUG: Guessing max time width: 62
[+0.72s] DEBUG: background.vala:315: Regenerating backgrounds
[+0.72s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1080
[+0.72s] DEBUG: New style for time label
[+0.72s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.72s] DEBUG: Checking against 2 possible times
[+0.72s] DEBUG: Guessing max time width: 62
[+0.73s] DEBUG: unity-greeter.vala:972: Starting main loop
[+0.73s] DEBUG: Read 8 bytes from daemon
[+0.73s] DEBUG: Read 33 bytes from daemon
[+0.73s] DEBUG: Prompt user with 1 message(s)
[+0.81s] DEBUG: Num devices: '1'

[+0.81s] DEBUG: get_primary_device: got data from object /org/freedesktop/UPower/devices/ups_hiddev1
[+0.81s] MESSAGE: Couldn't find primary device
[+0.81s] DEBUG: Num devices: '1'

[+0.81s] DEBUG: menu_add_device: got data from object /org/freedesktop/UPower/devices/ups_hiddev1
[+0.81s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+0.81s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+0.81s] DEBUG: should_be_visible: no
[+0.81s] DEBUG: menubar.vala:549: Removing indicator object 0x24925e8
[+0.81s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.81s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.81s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+0.81s] WARNING: menubar.vala:561: Indicator object 0x24925e8 not in menubar
[+0.81s]  WARNING: Getting layout failed:  GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface  `com.canonical.dbusmenu' on object at path  /com/canonical/indicator/users/menu
[+0.81s] DEBUG: notify visible signal received
[+0.81s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+0.82s] DEBUG: New calendar item
[+0.82s] DEBUG: Connected to Application Indicator Service.
[+0.82s] DEBUG: unity-greeter.vala:315: starting system-ready sound
[+1.56s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+1.58s] DEBUG: Setting keyboard layout to 'us'
[+1.61s] DEBUG: Request current apps
[+1.61s] DEBUG: indicator-sound: new_volume_slider_widget
[+1.62s] DEBUG: indicator-sound: new_voip_slider_widget
[+8.70s] DEBUG: Providing response to display manager
[+8.70s] DEBUG: Wrote 23 bytes to daemon
[+10.87s] DEBUG: Read 8 bytes from daemon
[+10.87s] DEBUG: Read 15 bytes from daemon
[+10.87s] DEBUG: Authentication complete for user [my user name] with return code 7
[+10.87s] DEBUG: Starting authentication for user [my user name]...
[+10.87s] DEBUG: Wrote 19 bytes to daemon
[+10.89s] DEBUG: Read 8 bytes from daemon
[+10.89s] DEBUG: Read 33 bytes from daemon
[+10.89s] DEBUG: Prompt user with 1 message(s)
[+13.99s] DEBUG: Providing response to display manager
[+13.99s] DEBUG: Wrote 24 bytes to daemon
[+14.06s] DEBUG: Read 8 bytes from daemon
[+14.06s] DEBUG: Read 15 bytes from daemon
[+14.06s] DEBUG: Authentication complete for user [my user name] with return code 0
[+14.06s] DEBUG: Starting session ubuntu
[+14.06s] DEBUG: Wrote 18 bytes to daemon
[+14.06s] DEBUG: Read 8 bytes from daemon
[+14.06s] DEBUG: Read 4 bytes from daemon
```

---

### Post by fortitude on 2013-08-06
Aha! Upon rebooting several times and studying what happens closely, I see that the login prompt never registers the first keystroke of the password on the first attempt. Does not matter if I click the box to place focus there or not. I can get it to work by pressing any random key then the password. On the second attempt, all keystrokes are always registered. Looks like a bug to me.

---

### Post by carl4926 on 2013-08-06
> **fortitude said:**
> Aha! Upon rebooting several times and studying what happens closely, I see that the login prompt never registers the first keystroke of the password on the first attempt. Does not matter if I click the box to place focus there or not. I can get it to work by pressing any random key then the password. On the second attempt, all keystrokes are always registered. Looks like a bug to me.
This happened in openSUSE KDE 12.2 version (not sure if it was a KDE bug and affected other distros)
But I don't recall seeing it reported in any *buntu versions...

---

### Post by fortitude on 2013-08-06
> **carl4926 said:**
> This happened in openSUSE KDE 12.2 version (not sure if it was a KDE bug and affected other distros)
But I don't recall seeing it reported in any *buntu versions...

Do you happen to recall what the fix was in that instance? :)

---

### Post by carl4926 on 2013-08-07
> **fortitude said:**
> Do you happen to recall what the fix was in that instance? :)
No I don't
I'm fairly sure it didn't get sorted for some time. And I doubt it's related.

At the login > if you wait say 15 seconds before you type anything in the password field, does that help?

---

### Post by fortitude on 2013-08-07
> **carl4926 said:**
> At the login > if you wait say 15 seconds before you type anything in the password field, does that help?

I waited at least that long and no luck. Next I'll try uninstalling the nvidia proprietary driver again and see if that makes any difference and report back.

---

### Post by fortitude on 2013-08-07
> **fortitude said:**
> Next I'll try uninstalling the nvidia proprietary driver again and see if that makes any difference and report back.

No difference.

One idea, does the Ubuntu installer check files on the root drive to try to import anything into a fresh install? What I usually do is use the live cd and delete everything on the root drive except for the home folder, which I just rename to home_bak. Then when installation is finished I just copy over the personal files I need from home_bak into home. Is there any way some contamination from past installations could affect the new install with this method?

---

### Post by carl4926 on 2013-08-07
> **fortitude said:**
> No difference.

One idea, does the Ubuntu installer check files on the root drive to try to import anything into a fresh install? What I usually do is use the live cd and delete everything on the root drive except for the home folder, which I just rename to home_bak. Then when installation is finished I just copy over the personal files I need from home_bak into home. Is there any way some contamination from past installations could affect the new install with this method?

The preferred method is to format / (root)
And have a separate /home partition
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

---

### Post by fortitude on 2013-08-08
> **carl4926 said:**
> The preferred method is to format / (root)
And have a separate /home partition


Thanks Carl, I think I knew in the back of my mind that most people liked to do it that way but I've always been too lazy to set it up. I think I will later today with a fresh install of 13.04. I hope this finally solves the issue. :) I'll take it as slow as I can with making changes to the system (drivers, additional packages) and hopefully at least find out what package breaks things by trial and error.

Last time I tried 13.04 I had the login issue, plus suspend would not work, plus I was getting error messages popping up periodically about Ubuntu crashing or some such (sorry, I forgot the exact terminology). At least on 12.04 LTS I don't get the crashing messages.

---

### Post by carl4926 on 2013-08-08
> **fortitude said:**
> Thanks Carl, I think I knew in the back of my mind that most people liked to do it that way but I've always been too lazy to set it up. I think I will later today with a fresh install of 13.04. I hope this finally solves the issue. :) I'll take it as slow as I can with making changes to the system (drivers, additional packages) and hopefully at least find out what package breaks things by trial and error.

Last time I tried 13.04 I had the login issue, plus suspend would not work, plus I was getting error messages popping up periodically about Ubuntu crashing or some such (sorry, I forgot the exact terminology). At least on 12.04 LTS I don't get the crashing messages.

Hope we can help you on the other side... if necessary that is.
Hopefully, all will be well and no problems.

---

### Post by fortitude on 2013-08-08
> **carl4926 said:**
> Hope we can help you on the other side... if necessary that is.
Hopefully, all will be well and no problems.

Thanks Carl, you are a saint. I'll be sure to update this thread if I find out what package might be the culprit or if it starts doing this right away....

---

### Post by fortitude on 2013-08-09
Installed Ubuntu 13.04 AMD64 fresh by formatting and partitioning the hard disk before installation. Started it up for the first time and still have the issue -- first keypress on the login screen is not entered into the password field thus it won't accept the password the first try unless I press a random key before entering the password. Alas. Any other things I can try? I'm certainly willing to dig in and edit configuration files, I'll just need to be told which files and what to edit/add/remove!

---

### Post by QIII on 2013-08-09
Are you using a wireless keyboard, by chance?

---

### Post by carl4926 on 2013-08-09
Did you test the login with a new user account?

So you say format and partition, does that mean you started a clean /home too?

---

### Post by fortitude on 2013-08-09
> **QIII said:**
> Are you using a wireless keyboard, by chance?

Thanks for your question, but no, it is a wired PS/2 Keytronic, very reliable.

If you have any more ideas, please let me know. :)

---

### Post by fortitude on 2013-08-09
> **carl4926 said:**
> Did you test the login with a new user account?

So you say format and partition, does that mean you started a clean /home too?

Yes, everything fresh. New root partition (/), new home (/home) partition (there is a 4GiB swap partition as well).

I'll try making a new user and report back.

---

### Post by carl4926 on 2013-08-09
> **fortitude said:**
> Yes, everything fresh. New root partition (/), new home (/home) partition (there is a 4GiB swap partition as well).

I'll try making a new user and report back.

In that case it'll not matter testing a new user.

What about @[COLOR=#000000]QIII's comment about wireless keyboard?[/COLOR]

---

### Post by fortitude on 2013-08-09
I tested a new user with a different username and different password - same thing (first keypress does nothing).

I have a reliable wired PS/2 keyboard (Keytronic E06101P1).

Any other ideas? :)

---

### Post by carl4926 on 2013-08-09
No other ideas

But this phenomenon, only happens at the login?

---

### Post by fortitude on 2013-08-09
> **carl4926 said:**
> No other ideas

But this phenomenon, only happens at the login?

Hi Carl, It actually will happen the first time the password is entered in the GUI. So with auto login, it will happen for example when unlocking the user accounts settings for the first time if that's where I enter the password first.

I would guess that would tell us that it's not a problem with X or the graphics driver or the login screen specifically.

---

### Post by carl4926 on 2013-08-09
Any way you can try a different keyboard?

---

### Post by fortitude on 2013-08-09
> **carl4926 said:**
> Any way you can try a different keyboard?

Most of the keyboards I have are the same model but I will try to find a different model and report back. Might take a day or two. :)

---

### Post by fortitude on 2013-08-10
All right, I dug out a known-good IBM branded PS/2 keyboard and it has the same issue. I have discovered that the first password character will register if the key is held down for approximately 2 seconds until the bullet appears in the login box. A tap won't do it. A tap will suffice for all other characters after the first though.

I won't be testing a USB keyboard.

I'll leave this thread unsolved though as I believe this is a bug as the behavior will confuse most users. :)

I suppose it is possible it is just my motherboard and everyone else is fine and dandy though. Unlikely as that may be considering there is no issue typing or any delay of any kind in any other program or dialog. It is isolated to just the password entry mechanism.

Thanks again to all, especially Carl for their help. Time to move on to my other issue with the core functionality of Ubuntu, in another thread!

---

### Post by dj722000 on 2013-08-10
Coming from a sleep mode it does it to mine to. When I  input mine, it pops back up, I can do it several times in a row but it is picking up all of my keystrokes. If I log out and come back in, use the password it lets me in, if I have firefox running it wont let me open it back up and I have to do a restart before it lets me in. What a pain, all after a update about a week ago.

---

