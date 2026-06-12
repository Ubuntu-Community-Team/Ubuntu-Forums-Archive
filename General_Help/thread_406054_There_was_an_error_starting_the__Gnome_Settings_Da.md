---
title: "There was an error starting the  Gnome Settings Daemon"
date: 2007-04-10
forum: General Help
---

### Post by ranjan392b on 2007-04-10
Hi
A few hours back my Nautilus had crashed. I started my computer but couldn't log on to the default session. I tried to fix the problem and almost suceeded. This is the error message I am getting now : 
[COLOR="Red"]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

The name org.gnome.SettingsDaemon was not provided by any .service files

GNOME will still try to restart the Settings Daemon next time you log in.[/COLOR]

I have restarted the session a couple of times but the problem didn't get fixed. 
Please help me out. I am new to Linux and am completely at sea.
TIA

---

### Post by Rui Pais on 2007-04-10
hi,
try this:
Close any gnome session .
Go to a console (press Ctrl+Alt+F1 keys), login and at command line enter:
```
mv .gconf .gconf_TEMP
```
Then press  Ctrl+Alt+F7 to go back to your login manager and try again start a gnome session.

---

### Post by Italian mobster on 2007-04-10
nope this did not help me I get this 

mobster@mobster-desktop:/home/mobster# mv .gconf .gconf_TEMP
mv: cannot move `.gconf' to a subdirectory of itself, `.gconf_TEMP/.gconf'

and I also tryed    gnome-settings-daemon

I dont know how to fix this error

---

### Post by Italian mobster on 2007-04-10
hoo wate I just ran the  

gnome-settings-daemon

and it says this one is different

mobster@mobster-desktop:/home/mobster# gnome-settings-daemon

(gnome-settings-daemon:4996): GSwitchIt-WARNING **: Unable to connect to dbus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:4996): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:4996): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:4996): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

(bug-buddy:5004): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (bug-buddy:5004): WARNING **: Couldn't load icon for Open Folder

---

### Post by Rui Pais on 2007-04-11
> **Italian mobster said:**
> nope this did not help me I get this 

mobster@mobster-desktop:/home/mobster# mv .gconf .gconf_TEMP
mv: cannot move `.gconf' to a subdirectory of itself, `.gconf_TEMP/.gconf'

and I also tryed    gnome-settings-daemon

I dont know how to fix this error

you must have typed something wrong... the error output says you trying to move the folder to itself...

Do you have the same error message then ranjan392b?

you may need to mv all .gconf and .gnome... 
try **from a console (Ctrl+Alt+F1)**:
```
mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/
```
then login to a gnome session a see if it's ok.
If not move all from gnome_TEMP again to /home/mobster

You can try too:
```
sudo aptitude reinstall gnome-session capplets-data
```

---

### Post by Italian mobster on 2007-04-11
can you be more detailed I did what you said I did both I made the mkdir gnome_TEMP
but it will not let me move it I also reinstalled capplets-data what I think is strange because when I update it take's soo long to install capplets-data 
gnome is all messed up what is the problem thank you

---

### Post by Rui Pais on 2007-04-11
> **Italian mobster said:**
> can you be more detailed I did what you said I did both I made the mkdir gnome_TEMP
but it will not let me move it
Thats stange... what exactly was the error? 
You must do that from a console and with all gnome sessions closed.
You should be the owner of those files. 
btw whats the output of:
```
ls -l .ICEauthority
```

>  I also reinstalled capplets-data what I think is strange because when I update it take's soo long to install capplets-data 
gnome is all messed up what is the problem thank you

capplets will install the services that are mentioned as missing on ranjan392b first post. 
Thats why i suggest a reinstallation... if it take a long time maybe there is a deeper problem... 
My suggestion to move .gnome and .gonf folders is to check if you have problems with user config. 
If capplets have a problem thats at administrative/system level, and more difficult.


edit: i will need to leave now and only come back on a 5 or 6 hours. 
maybe somebody will help you in mean time, if not i will help you later

---

### Post by Italian mobster on 2007-04-11
the ls -l .ICEauthority out put is 
-rw------- 1 root root 0 2007-04-10 12:59 .ICEauthority

I just reinstalled because of this error  and Ctrl+Alt+F1) does not work did my computer get compromised or something this is the 2ed time with this error I'm thinking of useing a different distro I mean this stinks everytime I get it going good in the end this happends everytime and I cant fix it I learned so much with this distro I hate to go back to puppy

---

### Post by Rui Pais on 2007-04-11
> **Italian mobster said:**
> the ls -l .ICEauthority out put is 
-rw------- 1 root root 0 2007-04-10 12:59 .ICEauthority

I just reinstalled because of this error  and Ctrl+Alt+F1) does not work did my computer get compromised or something this is the 2ed time with this error I'm thinking of useing a different distro I mean this stinks everytime I get it going good in the end this happends everytime and I cant fix it I learned so much with this distro I hate to go back to puppy

damn i need to go out and it's falling ice (frozen rain)... 

You got a problem with ICE too... thats at least one thing that is wrong. 
do from a console:
```
chown *your_username_here* .ICEauthority
chgrp *your_username_here* .ICEauthority
```
replace *your_username_here* by your user name and try to login.

good luck

---

### Post by Italian mobster on 2007-04-11
it will not let me change my user name but it do something I'm going to repeat the posses in KDE 3.5  I installed it last night I'm haveing no problems in KDE 3.5 I feel like removing Gnome completely this stinks thanks for your help

---

### Post by Italian mobster on 2007-04-11
this sucks you people want to be azzholes when I asked for help a few months ago my computer got compromised buy some dum azz now I'm pissed off and its still happing WTF did I do you people want to be evil I will show you evil so my point is I dident do notheing in the first place I only wanted to be cool or something and I got azzholes and shited on I guess I have to go buy a new network card I been through so much in my life I'm full blooded Italian my family is from Aviano, Italy I been in the crazy house for trying to kill myself I realy wasent I just OD on coke and called the doctor a F#$ck'n Jap  then they put me in a shity rehab dirty place I about got throne out of the crazy house for picking on people because I was only their for 6 days I realy was not trying to OD I was just upset about  somethings so I got hooked on coke but I worked a killer job I made alot of money I'm not saying who I worked for but the rehab was a nightmare I did manage to get a bit of grily action but notheing real great I mean I dident get laide 
but if someone looked at me and saide you'll be useing Linux better then ever one year form now I would have punched them in the face I been CLEAN for 1 year now I feel great and I'm in great shape and I'm doing all the things I was doing better then ever please leave my PC alone
I dident do notheing to you  go away :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by Rui Pais on 2007-04-11
> **Italian mobster said:**
> this sucks you people want to be azzholes when I asked for help a few months ago my computer got compromised buy some dum azz now I'm pissed off and its still happing WTF did I do you people want to be evil I will show you evil so my point is I dident do notheing in the first place I only wanted to be cool or something and I got azzholes and shited on I guess I have to go buy a new network card I been through so much in my life I'm full blooded Italian my family is from Aviano, Italy I been in the crazy house for trying to kill myself I realy wasent I just OD on coke and called the doctor a F#$ck'n Jap  then they put me in a shity rehab dirty place I about got throne out of the crazy house for picking on people because I was only their for 6 days I realy was not trying to OD I was just upset about  somethings so I got hooked on coke but I worked a killer job I made alot of money I'm not saying who I worked for but the rehab was a nightmare I did manage to get a bit of grily action but notheing real great I mean I dident get laide 
but if someone looked at me and saide you'll be useing Linux better then ever one year form now I would have punched them in the face I been CLEAN for 1 year now I feel great and I'm in great shape and I'm doing all the things I was doing better then ever please leave my PC alone
I dident do notheing to you  go away :guitar: :guitar: :guitar: :guitar: :guitar:

?????
 
sorry?
don't get it. (Italian humor?)


In order to change permitions, since they belong to root you need to use chown and chgrp with sudo:
```
sudo chown your_username .ICEauthority
```
and do on.

---

### Post by guX on 2007-04-13
I'm getting this problem on a more or less fresh install of Feisty. I tried removing .gnome2 and .gconf*, but that didn't help. I even created a new user and tried logging in with that user, but I get the same problem.

---

### Post by Rui Pais on 2007-04-14
hi,
whats exactly is your error? 
It's like the one of ranjan392b (1st post), like the one of Italian mobster (4th post) or different?

---

### Post by slouck on 2007-04-21
Has anyone found a fix for this issue yet?  i too experience it from a fresh install of feisty but only when running the session through nxclient.  Any local logins without nx login just fine.  I have tested both on a lan and coming in through the internet.  Machine is an x40 IBM laptop.

---

### Post by matt91 on 2007-04-22
i had the same error about the Gnome settings daemon. i did this:

> mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/

which now gets rid of the error message but now gnome takes a long time to load with all my settings reset. when i start evolution it brings me to the setup assistent! so i spent hours yesterday setting up my desktop for it just to be messed up. the desktop was working faultless yesterday!

How can ubuntu release 7.04 when there are so many bugs to correct. i suggest this release should be called a beta.:(

this is my second installation of 7.04 where the first was keeping my home directory, i got the same error. i did a fresh fresh install and i thought it was ok.

---

### Post by macabro22 on 2007-04-27
I have got this same problem after a editing /etc/resolv.conf and later trying to configure my lan in network manager. When I start net work manager either I get a white window where my network setup-options should be or the system hands. I am thus forced to press the power button and the next time I log on I get the same problem: long start up time, white window on the upper right corner for half an hour, and then the bloddy message:

" ...blablabla, blabla bla.. will not be able to display themes and other ****... blablabla, bla bla bla...
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in. " 

I will try the above proposed solutions, but it seems it hasn't worked for anyone yet. Any ideas?

---

### Post by John Azelvandre on 2007-04-29
I'm having the same problem on a fresh install of Edgy.

The error message is:

[INDENT]"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."[/INDENT]

Certain things, like the "lock screen" button and the screensaver don't work.

Interestingly, it appears that opening up System/Preferences/Keyboard shortcuts may trigger the settings-daemon to start running.  

In any case, when I call that dialog, icons change to their updated appearance, lock screen works, screensaver works.  And gnome-settings-daemon is listed in the system monitor.

This error on login happens with any user account.

---

### Post by Liolikas on 2007-04-29
Same problem for me after update to 7 and after:

mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/

It works again. But it was my supadupa *conf* files and I had to drop them in junk folder. :(

---

### Post by Rui Pais on 2007-04-29
> **Liolikas said:**
> Same problem for me after update to 7 and after:

mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/

It works again. But it was my supadupa *conf* files and I had to drop them in junk folder. :(

hi, 
if it's working after you have done that you can then try to move from gnome_TEMP 1 by 1 the folders/files on it to your home again and see which one was the guilty one and that way you can have the issue solved and you configs not preserved.






@[matt91]("http://ubuntuforums.org/showpost.php?p=2506303&postcount=16")
the all point in move to a TEMP folder istead of simply delete them was got get back if the thing don't work or try to get back the personal confs, like above, it it works....

---

### Post by John Azelvandre on 2007-04-29
I'm afraid that

[INDENT]mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/
[/INDENT]

did NOT work for me.  The problem remains.  Anyone have any other ideas?

---

### Post by Rui Pais on 2007-04-29
> **John Azelvandre said:**
> I'm afraid that

[INDENT]mkdir gnome_TEMP
mv .gconf* .gnome* gnome_TEMP/
[/INDENT]

did NOT work for me.  The problem remains.  Anyone have any other ideas?

hi, you mention that the error happens with any user account.
That indicate a problem somewhere with gnome it self, not at users side (with configs inside users homes).

Can you post whats the output of:
```
cat .xsession-errors
```

---

### Post by John Azelvandre on 2007-04-29
Sure!

 Here it is, rather long, not sure how to format it properly for this board:

[INDENT]```
zizonus@lc2000:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "zizonus"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/lc2000:/tmp/.ICE-unix/11153
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Initializing nautilus-open-terminal extension
evolution-alarm-notify-Message: Setting timeout for 28118 1177891200 1177863082
evolution-alarm-notify-Message:  Sun Apr 29 20:00:00 2007

evolution-alarm-notify-Message:  Sun Apr 29 12:11:22 2007


(gnome-panel:11225): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 25

** (gnome-system-monitor:11329): WARNING **: SELinux was found but is not enabled.

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

CalDAV Eplugin starting up ...

(evolution-2.8:11815): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:11815): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.8:11815): Gtk-CRITICAL **: gtk_file_chooser_set_filename: assertion `GTK_IS_FILE_CHOOSER (chooser)' failed
** (evolution-2.8:11815): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:11815): DEBUG: mailto URL program: evolution
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x2e029ce (Reply to p); these messages lack timestamps and therefore suck.
** Message: <information>       Forcing device '/org/freedesktop/NetworkManager/Devices/eth0'


** Message: <information>       You are now connected to the wired network.

** Message: <information>       You are now connected to the wireless network 'linksys'.

gnome-screensaver-Message: Found best visual for GL: 0x21
alarm-notify.c:366 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:302 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:241 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1871 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Sun Apr 29 20:00:00 2007
 
alarm-notify.c:160 (list_changed_cb) - Adding Calendar file:///home/zizonus/.evolution/calendar/local/system
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80d02d0
alarm-notify.c:160 (list_changed_cb) - Adding Calendar contacts:///
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80d0c20
alarm-notify.c:160 (list_changed_cb) - Adding Calendar file:///home/zizonus/.evolution/memos/local/system
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80d0ca0
alarm-notify.c:160 (list_changed_cb) - Adding Calendar file:///home/zizonus/.evolution/tasks/local/system
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80e3c30
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80e1968: Received at thread b3edeba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80d02d0
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:16:03 2007
 to Sun Apr 29 12:16:03 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80e1968: Replied to GUI thread
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80e7708: Received at thread b3edeba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80d0ca0
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:16:03 2007
 to Sun Apr 29 12:16:03 2007

alarm-queue.c:497 (load_alarms) 
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80e7708: Replied to GUI thread
alarm-notify.c:347 (alarm_msg_received) - 0x80dfa18: Received at thread b3edeba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80e3c30
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:16:03 2007
 to Sun Apr 29 12:16:03 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80dfa18: Replied to GUI thread
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80e5aa0: Received at thread b3edeba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80d0c20
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:16:03 2007
 to Sun Apr 29 12:16:03 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:335 (alarm_msgport_replied) - 0x80e5aa0: Replied to GUI thread
alarm-queue.c:1833 (check_midnight_refresh)
alarm-queue.c:1852 (check_midnight_refresh) - Posting a task to refresh
alarm-notify.c:347 (alarm_msg_received) - 0x80e8bc8: Received at thread b3edeba0
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:41:23 2007
 to Sun Apr 29 12:41:23 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:41:23 2007
 to Sun Apr 29 12:41:23 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Sun Apr 29 12:41:23 2007
 to Sun evolution-alarm-notify-Message: Setting timeout for 40718 1177905600 1177864882
evolution-alarm-notify-Message:  Mon Apr 30 00:00:00 2007

evolution-alarm-notify-Message:  Sun Apr 29 12:41:22 2007

** Message: <information>       You are now connected to the wireless network 'linksys'.

** Message: <information>       Forcing device '/org/freedesktop/NetworkManager/Devices/eth0'


** Message: <information>       You are now connected to the wired network.

zizonus@lc2000:~$ 

```[/INDENT]

Ok, looks like I formatted it correctly.  Perhaps the earlier stuff in it will lead somewhere?  Thanks for helping!

---

### Post by Rui Pais on 2007-04-29
uhmm nothing wrong seems to be there...

can you login to a session with the issue and from a terminal start gnome-settings-daemon? It starts then? Did it outputs any warnings or errors messages?

check too if you got something on /var/log/messages related to gnome-settings-daemon (you can check with ```
tail -30 /var/log/messages
```, where -xx is the number of lines it prints... it's usually a huge file).
 
Have you tried to do:
```
sudo aptitude reinstall gnome-control-center capplets-data
``` 
? maybe it can correct something that failed or became broken.

---

### Post by John Azelvandre on 2007-04-29
Thank you for your suggestions.  I tried each in turn.  Here are the results.

When I start gnome-settings-daemon from the terminal this results:

```
zizonus@lc2000:~$ gnome-settings-daemon
uIyIxrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
~I

```

It then seems to run fine, until I Ctrl-Z it.  But then I can make it continue independently from the System Monitor.  Interestingly, another way to start it is to just call up System/Preferences/Keyboard Shortcuts, which triggers it to start and run thenceforth.

I looked at var/log/messages.  There didn't seem to be anything directly mentioning gnome-settings-daemon, but I'll share with you what is recorded for the 3 minutes (YES! three whole minutes and then some) that it takes to login a user, where the error is apparently happening:

```
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): starting (version 2.16.0), pid 11194 user 'zizonus'
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): Resolved address "xml:readwrite:/home/zizonus/.gconf" to a writable configuration source at position 1
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr 29 12:07:45 lc2000 gconfd (zizonus-11194): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr 29 12:11:21 lc2000 gconfd (zizonus-11194): Resolved address "xml:readwrite:/home/zizonus/.gconf" to a writable configuration source at position 0
```

Notice the long time lapse between the last two actions of gconfd.  It always happens like this.

Lastly, I tried reinstalling as you suggested.  It produced no change in behavior whatsoever.

What could possibly be going on?

---

### Post by John Azelvandre on 2007-04-29
Another little thing.  It says in the var/log/messages snippet I posted that it is starting 2.16.0.  But it appears that I am running Gnome 2.16.1.  Does this mean anything?

---

### Post by Rui Pais on 2007-04-29
the "xrdb:  "*xxx.xxxx" on line nnn overrides entry on line nnn" seems to be normal. 
It happens on a working installation, so no problem here...
> **John Azelvandre said:**
> Another little thing.  It says in the var/log/messages snippet I posted that it is starting 2.16.0.  But it appears that I am running Gnome 2.16.1.  Does this mean anything?
ahhh, now you may have found something. You should have 2.6.18.0.1. at feisty! 
Check with synaptic which version of gconf and other gnome components you have. 
Check if you have any edgy entry on /etc/apt/sources.list (**cat /etc/apt/sources.list|grep edgy** should gives nothing on a terminal)
Check if:
```
sudo aptitude reinstall ubuntu-desktop
```
produce anything. Try run this command with all gnome sessions closed froma console (logout gnome and press Ctrl+Alt+F1 keys)

---

### Post by John Azelvandre on 2007-04-29
Well, I am running edgy, not feisty.  But my edgy should be completely up to date.  I'll try reinstalling the ubuntu desktop and see what that does.

---

### Post by Rui Pais on 2007-04-29
> **John Azelvandre said:**
> Well, I am running edgy, not feisty.  But my edgy should be completely up to date.  I'll try reinstalling the ubuntu desktop and see what that does.

Oh, sorry. 
A lot of people had put questions about this on the festy upgrade context that  i assumed that was your case. :( In that case it's not a problem. 2.16.0 it's the correct version that gconf should said for gnome 2.16.1.

btw when reintalling the ubuntu-desktop make sure you use aptitude and not apt-get, for better management of dependencies. 
Good luck.

---

### Post by John Azelvandre on 2007-04-29
Alas, reinstalling the ubuntu-desktop package made no difference.  Still the 3+ minute delay in logging on, still the Gnome Settings Daemon error message.

A mystery.

---

### Post by msikka on 2007-05-05
I am getting the exact same error message as John Azelvandre but with Fiesty, and, only when I suspend, and then try to awaken the session. After a few minutes my wireless doesn't work, I have to reboot. Once I reboot everything works just fine.

Any ideas for me?

Thanks

---

### Post by John Azelvandre on 2007-05-05
In the end, a completely fresh install of Feisty cured my settings daemon problem and a host of other problems as well.  I guess I'll never know what the cause of the problem was.  See if any of the suggestions in this thread help your situation.  Good luck!

---

### Post by Rui Pais on 2007-05-05
> **John Azelvandre said:**
> In the end, a completely fresh install of Feisty cured my settings daemon problem and a host of other problems as well.  I guess I'll never know what the cause of the problem was.  See if any of the suggestions in this thread help your situation.  Good luck!

hi,
sorry, for some reason seems that i didn't received mail notification about your post before that... 
My suggestion wold be more or less a fresh reinstall (sometimes the only cure to obscure problems) or at least remove and purge any dependency of ubuntu-desktop (remove gnome completely) from a console and then a fresh install of ubuntu-dektop from zero (instead of reinstall only). 
Would have be lighter and easier, but maybe even then the problem wouldn't be solved so... glad you make work again :)



**@msikka**
yes, like John Azelvandre said try the suggestions on the thread and post on any doubt.

If it all fail you can do what i said above (i can give more details if needed) or you may go with a fresh install.

The basic here is use the move of gnome stuff and restart session to check if it's a user configuration problem or something deeper in the gnome installation.

Good luck

---

### Post by antonym on 2007-05-07
haha, never mind, I did a fresh install and it's working fine.

---

### Post by kevinsun on 2007-05-16
Hi,


Anyone tries disabling the ESD sound?  In my case, it works!

---

### Post by jEddy on 2007-05-17
Mine gives me that message if a networking card is plugged in which leads me to suspect it has something to do with networking.

Jeff

---

