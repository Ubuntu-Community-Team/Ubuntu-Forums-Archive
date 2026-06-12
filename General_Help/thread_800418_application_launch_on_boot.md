---
title: "application launch on boot"
date: 2008-05-19
forum: General Help
---

### Post by Wangberg on 2008-05-19
I asked this in another thread with several additional questions, and nobody was able to answer it.  I am posting it as it's own thread so more people can read and attempt to help on this specific issue.  

I would like to preface this issue by saying, this is the type of crap that linux should never do, as it's only emulating Windows in the sense that the developers of this OS are assuming i want this feature.  Not only is it annoying, but it slows my gnome boot 10 fold.  I want control, not assumed "features" that slow down my OS.

Here is the question:
How do i prevent applications from re-launching after i reboot via the main menu button restart or "sudo reboot" in terminal?  

I have this feature unchecked in the session manager but Ubuntu insists on displaying this behavior.  

Please help me disable this!!!!!

thanks,
wangberg

---

### Post by badfish591 on 2008-05-19
what is the name of the offending program?

---

### Post by drs305 on 2008-05-19
The sessions startup manager is where user gui input is usually made. 

The system startup programs are generally located in /etc/init.d  The order of startup is determined by runlevels and the links in the various /etc/rcX.d folders are run. These startup apps are probably not something you really want to mess with but if you have the experience or fortitude, you could play with the symnlinks in the rcX.d folders to prevent a process that particularly offends you.

---

### Post by Wangberg on 2008-05-19
evolution, pidgin, firefox, amarok, etc... anything and everything that is open pre-boot is relaunced upon a rebooted system and log in to gnome...

---

### Post by Wangberg on 2008-05-19
> **drs305 said:**
> The sessions startup manager is where user gui input is usually made. 

The system startup programs are generally located in /etc/init.d  The order of startup is determined by runlevels and the links in the various /etc/rcX.d folders are run. These startup apps are probably not something you really want to mess with but if you have the experience or fortitude, you could play with the symnlinks in the rcX.d folders to prevent a process that particularly offends you.

it's not a process...it's applications i launch like pidgin and amarok, and are relaunched upon a reboot....they are not startup processes...

---

### Post by drs305 on 2008-05-19
I misunderstood what you were looking for. There is an autostart folder in /home/username/.config but I believe it just holds the information that the Sessions manager contains. You could check it to make sure it's empty.

There is also a /usr/share/autostart folder.

---

### Post by vishnumrao on 2008-05-20
I too have the same problem.
Transmission, pidgin, skype, opera, screenlets(the one which i don't want starts up, while the one I would like to startup doesn't) etc, startup as soon as I login. Makes my login take forever. 

Both my autostart dirs are non empty. But they do not contain any info relating to the applications that startup. 

```
 vishnumrao@vishnumrao-desktop-2:/usr/share/autostart$ cd /home/vishnumrao/.config/autostart/
vishnumrao@vishnumrao-desktop-2:~/.config/autostart$ dir
bluetooth-applet.desktop        redhat-print-applet.desktop
compiz.desktop                  Screenlets\ Daemon.desktop
evolution-alarm-notify.desktop  SensorsScreenlet.desktop
gnome-at-session.desktop        SysmonitorScreenlet.desktop
vishnumrao@vishnumrao-desktop-2:~/.config/autostart$ cd /usr/share/autostart/
vishnumrao@vishnumrao-desktop-2:/usr/share/autostart$ dir
kab2kabc.desktop  khotkeys.desktop  trackerd.desktop
vishnumrao@vishnumrao-desktop-2:/usr/share/autostart$ 

```

I too have already tried what Wangberg has tried. Any suggestions?

---

### Post by N.N. on 2008-05-20
I believe this is non-standard behaviour. Please post the output of the following command (to be run in a terminal): ```
cat ~/.gnome2/session-manual
```

---

### Post by drs305 on 2008-05-20
I've done some research and may have found an answer. Try deleting the offending apps from System, Preferences, Sessions, CURRENT Session (i.e. not Startup Sessions). If the apps don't appear there because you have already terminated them after boot, do it the next time you start your computer. 

Yeah, I know, it doesn't seem to make much sense, but it has worked for some users.  Good luck.

---

### Post by Wangberg on 2008-05-20
> **N.N. said:**
> I believe this is non-standard behaviour. Please post the output of the following command (to be run in a terminal): ```
cat ~/.gnome2/session-manual
```

there was no "session-manual" file, but there was a "session" file:

```

wangberg@chewbacca:~/.gnome2$ cat session 

[Default]
0,id=117f000101000120985156800000055600000
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/wangberg
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ --sm-client-id 117f000101000120985156800000055600000 --screen 0 
1,id=117f000101000120991380000000055760012
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/wangberg
1,DiscardCommand=rm -f /home/wangberg/.metacity/sessions/117f000101000120991380000000055760012.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-client-id 117f000101000120991380000000055760012 
2,id=117f000101000120985156800000055600001
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/wangberg
2,CloneCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ --sm-client-id 117f000101000120985156800000055600001 --screen 0 
3,id=117f000101000120985157100000055600004
3,RestartStyleHint=1
3,Program=update-notifier
3,CurrentDirectory=/home/wangberg
3,CloneCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ 
3,RestartCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ --sm-client-id 117f000101000120985157100000055600004 --screen 0 
4,id=117f000101000120985157100000055600005
4,Program=gnome-power-manager
4,CurrentDirectory=/home/wangberg
4,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ 
4,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ --sm-client-id 117f000101000120985157100000055600005 --screen 0 
5,id=117f000101000121085261100000055750006
5,Program=firefox
5,CurrentDirectory=/home/wangberg
5,CloneCommand=firefox 
5,RestartCommand=firefox --sm-client-id 117f000101000121085261100000055750006 --screen 0 
6,id=117f000101000121089491600000055750009
6,RestartStyleHint=0
6,Program=amarokapp
6,RestartCommand=amarokapp -session 117f000101000121089491600000055750009_1210894923_739776 
7,id=117f000101000120986548500000055760006
7,RestartStyleHint=0
7,Program=pidgin
7,CurrentDirectory=/home/wangberg
7,DiscardCommand=/bin/true 
7,CloneCommand=pidgin --display :0.0 
7,RestartCommand=pidgin --session 117f000101000120986548500000055760006 --display :0.0 
8,id=117f000101000121090284800000055650001
8,RestartStyleHint=0
8,Program=evolution-alarm-notify
8,CurrentDirectory=/home/wangberg
8,CloneCommand=evolution-alarm-notify 
8,RestartCommand=evolution-alarm-notify --sm-client-id 117f000101000121090284800000055650001 --screen 0 
9,id=117f000101000121090286400000055650003
9,Program=fast-user-switch-applet
9,CurrentDirectory=/
9,CloneCommand=fast-user-switch-applet 
9,RestartCommand=fast-user-switch-applet --sm-client-id 117f000101000121090286400000055650003 --screen 0 
10,RestartCommand=bluetooth-applet --singleton 
11,RestartCommand=gnome-at-visual -s 
12,RestartCommand=jockey-gtk --check 60 
13,RestartCommand=/usr/lib/evolution/2.22/evolution-alarm-notify 
14,RestartCommand=tracker-applet 
15,RestartCommand=xdg-user-dirs-gtk-update 
16,RestartCommand=trackerd 
17,RestartCommand=pactl load-module module-x11-xsmp 
18,RestartCommand=/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable 
19,RestartCommand=/usr/bin/system-config-printer-applet 
20,RestartCommand=nm-applet --sm-disable 
num_clients=21

```

THANKS!

---

### Post by N.N. on 2008-05-20
> **Wangberg said:**
> there was no "session-manual" file, but there was a "session" file:

```

wangberg@chewbacca:~/.gnome2$ cat session 

[Default]
0,id=117f000101000120985156800000055600000
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/wangberg
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-hdCbYO/ --sm-client-id 117f000101000120985156800000055600000 --screen 0 
1,id=117f000101000120991380000000055760012
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/wangberg
1,DiscardCommand=rm -f /home/wangberg/.metacity/sessions/117f000101000120991380000000055760012.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-client-id 117f000101000120991380000000055760012 
2,id=117f000101000120985156800000055600001
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/wangberg
2,CloneCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-rTogIC/ --sm-client-id 117f000101000120985156800000055600001 --screen 0 
3,id=117f000101000120985157100000055600004
3,RestartStyleHint=1
3,Program=update-notifier
3,CurrentDirectory=/home/wangberg
3,CloneCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ 
3,RestartCommand=update-notifier --sm-config-prefix /update-notifier-Sb7dRL/ --sm-client-id 117f000101000120985157100000055600004 --screen 0 
4,id=117f000101000120985157100000055600005
4,Program=gnome-power-manager
4,CurrentDirectory=/home/wangberg
4,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ 
4,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-dvroqI/ --sm-client-id 117f000101000120985157100000055600005 --screen 0 
5,id=117f000101000121085261100000055750006
5,Program=firefox
5,CurrentDirectory=/home/wangberg
5,CloneCommand=firefox 
5,RestartCommand=firefox --sm-client-id 117f000101000121085261100000055750006 --screen 0 
6,id=117f000101000121089491600000055750009
6,RestartStyleHint=0
6,Program=amarokapp
6,RestartCommand=amarokapp -session 117f000101000121089491600000055750009_1210894923_739776 
7,id=117f000101000120986548500000055760006
7,RestartStyleHint=0
7,Program=pidgin
7,CurrentDirectory=/home/wangberg
7,DiscardCommand=/bin/true 
7,CloneCommand=pidgin --display :0.0 
7,RestartCommand=pidgin --session 117f000101000120986548500000055760006 --display :0.0 
8,id=117f000101000121090284800000055650001
8,RestartStyleHint=0
8,Program=evolution-alarm-notify
8,CurrentDirectory=/home/wangberg
8,CloneCommand=evolution-alarm-notify 
8,RestartCommand=evolution-alarm-notify --sm-client-id 117f000101000121090284800000055650001 --screen 0 
9,id=117f000101000121090286400000055650003
9,Program=fast-user-switch-applet
9,CurrentDirectory=/
9,CloneCommand=fast-user-switch-applet 
9,RestartCommand=fast-user-switch-applet --sm-client-id 117f000101000121090286400000055650003 --screen 0 
10,RestartCommand=bluetooth-applet --singleton 
11,RestartCommand=gnome-at-visual -s 
12,RestartCommand=jockey-gtk --check 60 
13,RestartCommand=/usr/lib/evolution/2.22/evolution-alarm-notify 
14,RestartCommand=tracker-applet 
15,RestartCommand=xdg-user-dirs-gtk-update 
16,RestartCommand=trackerd 
17,RestartCommand=pactl load-module module-x11-xsmp 
18,RestartCommand=/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable 
19,RestartCommand=/usr/bin/system-config-printer-applet 
20,RestartCommand=nm-applet --sm-disable 
num_clients=21

```

THANKS!

Remove the lines concerning the offending applications.

The default session that is launched if a user doesn't already have a session looks as follows: ```
[Default]
num_clients=4
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
```
Hence removing the lines that concern the offending applications should prevent them from being started upon next login.

---

### Post by Wangberg on 2008-05-20
> **N.N. said:**
> Remove the lines concerning the offending applications.

The default session that is launched if a user doesn't already have a session looks as follows: ```
[Default]
num_clients=4
0,id=default0
0,Priority=10
0,RestartCommand=gnome-wm --sm-client-id default0
1,id=default1
1,Priority=40
1,RestartCommand=gnome-panel --sm-client-id default1
2,id=default2
2,Priority=40
2,RestartCommand=nautilus --no-default-window --sm-client-id default2
3,id=default3
3,Priority=60
3,RestartCommand=gnome-cups-icon --sm-client-id default3
```
Hence removing the lines that concern the offending applications should prevent them from being started upon next login.

NN,

can i use the standard default you have posted?

---

### Post by issih on 2008-05-20
Doesn't sound quite like the behaviour you are describing, but nonetheless..

Go to System->Preferences->Sessions

and then on the session options tab, ensure that "remember currently running applications" is off

Not at all sure that is actually your problem, or indeed if you might actually like it to remember your current state, but generally I like my computer to come up clean on boot, I'll sleep or hibernate it if I want to save the current state of my programs.

---

### Post by N.N. on 2008-05-20
> **Wangberg said:**
> NN,

can i use the standard default you have posted?

Yes, that should work, too.

EDIT: Alternately just delete the session file in .gnome2, as that should have the same effect.

---

### Post by Wangberg on 2008-05-20
> **N.N. said:**
> Yes, that should work, too.

EDIT: Alternately just delete the session file in .gnome2, as that should have the same effect.

This did it, but also knocked out my network settings also.  I had to reconfigure them in network manager.

THANKS A TON!

---

### Post by N.N. on 2008-05-21
> **Wangberg said:**
> This did it, but also knocked out my network settings also.  I had to reconfigure them in network manager.

THANKS A TON!

You're welcome.

I wasn't aware that it would have any effect on your network settings, sorry about that.

---

### Post by vishnumrao on 2008-05-28
N.N,

Have been away from my Ubuntu machine for a few days. Tried out your suggestion to delete the session file and rebooted. Worked like a charm.

Thank you very much.
VMR

---

### Post by rimshot4 on 2010-01-30
Bump.

I'm having this problem in 9.10 but there's no session file in my .gnome2 folder. Anyone know how to fix this in 9.10?

---

### Post by drs305 on 2010-01-30
> **rimshot4 said:**
> Bump.

I'm having this problem in 9.10 but there's no session file in my .gnome2 folder. Anyone know how to fix this in 9.10?

You are having apps start that you don't want?

Try closing out all your apps. Then System, Preferences, StartUp-Applications, Options: Tick "Automatcially..." 
Reboot.
After rebooting, if the offending apps failed to start (which is what you wanted), untick the "Automatically..." selection.

---

### Post by rimshot4 on 2010-02-01
> **drs305 said:**
> You are having apps start that you don't want?

Try closing out all your apps. Then System, Preferences, StartUp-Applications, Options: Tick "Automatcially..." 
Reboot.
After rebooting, if the offending apps failed to start (which is what you wanted), untick the "Automatically..." selection.

That worked. Thanks!

---

