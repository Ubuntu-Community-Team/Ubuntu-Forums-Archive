---
title: "]XFCE 4.12 no Shutdown and reboot buttons."
date: 2015-07-17
forum: General Help
---

### Post by gabriel50 on 2015-07-17
Hi there, beside i always read the forum and i've been using ubuntu and mint for a couple of years its the first time i post. English is not my native language so, excuse me if i don't write correctly.

The problem it's  simple. I can't shutdown or reboot the computer from xfce session. The buttons are disabled. So if i want to shutdown the computer, first i have to close session and use the option in the welcome screen. 

I've already added my user to groups, the plugdev, edit visudo, etc. and nothing its working. Here i post what i've done specifically. 

sudo gpasswd -a useri plugdev

exec ck-launch-session dbus-launch --sh-syntax --exit-with-session startxfce4

( By the way here is the udev working:

sudo service udev start
start: Job is already running: udev

sudo service udev
Usage: /etc/init.d/udev {start|stop|restart|reload|force-reload|status}   )

In visudo i added this line:

#user ALL=(root) NOPASSWD: /opt/xfce4/libexec/xfsm-shutdown-helper

and this are my permission, when i use the command : sudo gedit /etc/group 
```

root: x:0:
daemon: x:1:
bin: x:2:
sys: x:3:
adm: x:4:USER,syslog
tty: x:5:
disk: x:6:
lp: x:7:
mail: x:8:
news: x:9:
uucp: x:10:
man: x:12:
proxy: x:13:
kmem: x:15:
dialout: x:20:USER
fax: x:21:USER
voice: x:22:
cdrom: x:24:USER
floppy: x:25:USER
tape: x:26:USER
sudo: x:27:USER
audio: x:29: pulse,USER
dip: x:30:USER
www-data: x:33:
backup: x:34:
operator: x:37:
list: x:38:
irc: x:39:
src: x:40:
gnats: x:41:
shadow: x:42:
utmp: x:43:
video: x:44:USER
sasl: x:45:
plugdev: x:46:USER
staff: x:50:
games: x:60:
users: x:100:USER
nogroup: x:65534:
libuuid: x:101:
crontab: x:102:
syslog: x:103:
fuse: x:104:USER
messagebus: x:105:
ssl-cert: x:106:
netdev: x:107:
vboxsf: x:108:
mlocate: x:109:
ssh: x:110:
avahi-autoipd: x:111:
lpadmin: x:112:USER
rtkit: x:113:
bluetooth: x:114:
avahi: x:115:
pulse: x:116:
pulse-access: x:117:
sambashare: x:118:USER
scanner: x:119:saned,USER
colord: x:120:
saned: x:121:
mdm: x:122:
USER: x:1000:
nopasswdlogin: x:123:
utempter: x:124:
lightdm: x:125:
```
  
So why i cant shutdown or reboot from xfce session? 
 
you can see the plugdev service in groups and that i have permissions but when i enter the following command:

sudo service plugdev start
plugdev: unrecognized service


so? what should i do?. Thanks you to all.

---

### Post by QDR06VV9 on 2015-07-17
What is the output of
```
[FONT=consolas]xfce4-power-manager --no-daemon --debug[/FONT]
```
And you probably already know
```
[FONT=consolas]sudo shutdown -h now
[/FONT][COLOR=#111111][FONT=Consolas]sudo reboot[/FONT][/COLOR]
```

---

### Post by gabriel50 on 2015-07-17
> **runrickus said:**
> What is the output of
```
[FONT=consolas]xfce4-power-manager --no-daemon --debug[/FONT]
```

HI, thanks for your reply, first of all i made a mistake in the title, i just notice... y meant xfce 4.12:)

This is what returned 

[FONT=consolas]xfce4-power-manager --no-daemon --debug[/FONT]
Xfce Power Manager: Another power manager is already running

---

### Post by QDR06VV9 on 2015-07-17
Been awhile since I used XFCE This should still work
> [COLOR=#000000]If you right-click the Applications Menu and choose Properties and then click on the "Edit Menu" button, you will startup the menu editor.[/COLOR]

[COLOR=#000000]Click on "New Item" then add in the following info:[/COLOR]

_For Shutdown:_
[COLOR=#000000]Name = Shutdown[/COLOR]
[COLOR=#000000]Command = xfce4-session-logout --halt[/COLOR]
[COLOR=#000000]Icon = (select an icon)[/COLOR]

_For Restart_
[COLOR=#000000]Name = Restart[/COLOR]
[COLOR=#000000]Command = xfce4-session-logout --reboot[/COLOR]
[COLOR=#000000]Icon = (select an Icon)[/COLOR]

[COLOR=#000000]Click on "Create" to create the entry, then click-drag to move it to the proper location in the menu.[/COLOR]
Thanks to Toz post#10 [http://ubuntuforums.org/showthread.php?t=1993329](http://ubuntuforums.org/showthread.php?t=1993329)

---

### Post by gabriel50 on 2015-07-17
> **runrickus said:**
> Been awhile since I used XFCE This should still work

Thanks to Toz post#10 [http://ubuntuforums.org/showthread.php?t=1993329](http://ubuntuforums.org/showthread.php?t=1993329)

thanks again. i'll give it a try, i really wanted to shutdown and reboot like it should be. but we'll always have the terminal :)

---

### Post by monkeybrain20122 on 2015-07-17
xfce is kind of confusing that it has two logout/shutdown/reboot buttons (or sets of buttons) One on the upper right corner of the top panel, and the other will show if you open the whisker menu (the bottom right) and the behaviours of these are not the same. I don't use xfce so can't remember which does what but I have set it up for my roommate and remember he was quite confused. I think the whisker menu one always works (if I remember correctly)

---

### Post by ajgreeny on 2015-07-17
Add panel applet "Action buttons" to your panel, then right-click on it to move it and configure it as you want it to look.

You can choose which buttons to show (logout, shutdown, suspend, etc etc) and choose whether to show Action buttons or session menu; it sounds as if you want action buttons, but if you choose session menu, a click on that will then show you the same options of logout, shutdown, suspend, etc etc.

This is actually the same as that Toz link mentioned above, which I had not noticed.

---

### Post by monkeybrain20122 on 2015-07-17
> **ajgreeny said:**
> Add panel applet "Action buttons" to your panel, then right-click on it to move it and configure it as you want it to look.

You can choose which buttons to show (logout, shutdown, suspend, etc etc) and choose whether to show Action buttons or session menu; it sounds as if you want action buttons, but if you choose session menu, a click on that will then show you the same options of logout, shutdown, suspend, etc etc.

This is actually the same as that Toz link mentioned above, which I had not noticed.

I think for the reboot button on the panel, choosing reboot/shutdown actually log you out and you then have to reboot/shutdown from there, whereas the reboot/shutdown button in the whisker menu does what it advertises. Also I think session get restored if you restart from the panel.

---

### Post by gabriel50 on 2015-07-17
> **ajgreeny said:**
> Add panel applet "Action buttons" to your panel, then right-click on it to move it and configure it as you want it to look.

You can choose which buttons to show (logout, shutdown, suspend, etc etc) and choose whether to show Action buttons or session menu; it sounds as if you want action buttons, but if you choose session menu, a click on that will then show you the same options of logout, shutdown, suspend, etc etc.

This is actually the same as that Toz link mentioned above, which I had not noticed.



hi ajgreeny, thanks for your reply.... right, i understand what you say, but i cant shutdown, reboot or suspend my computer, the buttons are locked, i'm only able to close session, and i can't shutdown neither from the action buttons or from the applications menu. that's why i made this thread.

So, if i need to shutdown or reboot my system i have no other choice that doing it o from terminal o closing my session first.... any idea?

by the way, thank you for correcting the title :)

---

### Post by Toz on 2015-07-17
> **gabriel50 said:**
>  i cant shutdown, reboot or suspend my computer, the buttons are locked
Do you mean greyed out? "xfce4-power-manager --dump" will show what permissions Xfce says you have.
> exec ck-launch-session dbus-launch --sh-syntax --exit-with-session startxfce4
Are you running without a display manager and is this the command that you are using to start the Xfce session? If so, try with just "startx" to see if that sets the proper *kit permissions to grant you access to shutdown and reboot.

Also, what version of Ubuntu are you running?

---

### Post by gabriel50 on 2015-07-17
> **Toz said:**
> Do you mean greyed out? "xfce4-power-manager --dump" will show what permissions Xfce says you have.

Are you running without a display manager and is this the command that you are using to start the Xfce session? If so, try with just "startx" to see if that sets the proper *kit permissions to grant you access to shutdown and reboot.

Also, what version of Ubuntu are you running?

exactly yes!, the buttons are greyed out...

for:  xfce4-power-manager --dump

return: 

Xfce power manager version 1.4.3
With policykit support
With network manager support
---------------------------------------------------
Can suspend: True
Can hibernate: True
Authorized to suspend: True
Authorized to hibernate: False
Authorized to shutdown: True
Has battery: False
Has brightness panel: False
Has power button: True
Has hibernate button: True
Has sleep button: True
Has LID: False

--------------------------------------------------

and i have no issue to log in. i'm not using any code...

thanks for your reply :)

---

### Post by Toz on 2015-07-17
Xfce looks fine. Must be something else.
What version of Ubuntu are you running Xfce on?
```
cat /etc/lsb-release
```

---

### Post by gabriel50 on 2015-07-17
Sorry Toz, i forgot to tell you,  actually i'm in Linux mint 17.1.... but i think it really doesn't make much difference...
Thanks for your patience

---

### Post by gabriel50 on 2015-07-18
I have a clue, but i can't fix the problem. I create the buttons manually, to suspend, reboot, shutdown and hibernate. But, when i try to hibernate the system, shows up a windows saying: 



[ATTACH=CONFIG]263261[/ATTACH]


" 

Authentication is needed to run /user/local/lib/xfce4/session/xfsm-shutdown-helper 

this has anything to do with my problem?  

 this are the lines that i added to visudo

#user ALL=(root) NOPASSWD: /usr/local/lib/xfce4/session/xfsm-shutdown-helper

#user  ALL=(ALL)NOPASSWD: /sbin/shutdown -h now,/sbin/reboot

but still no luck....  any ideas ?

---

### Post by ajgreeny on 2015-07-18
If you have to manually add buttons, and I can't see why you should, but perhaps that is a Linux Mint difference from Ubuntu, the commands you need are
```
xfce4-session-logout --halt
xfce4-session-logout --suspend
xfce4-session-logout --reboot  # not sure about this one as I've never needed it as all my action buttons work
```
I have the first two of those as keyboard shortcuts which is very useful, particularly the suspend, for which I use the Pause/Break key, as it's not used these days for anything else of note.

I am using Xubuntu-14.04 but have the xfce-4-12 ppa enabled and have been using xfce-4.12 for several  months now, and very good it is too!

---

### Post by Toz on 2015-07-18
See if this help. With root privileges, create the following 2 files with the following content:

**_File 1:_  /etc/polkit-1/localauthority/50-local.d/org.freedesktop.upower.pkla**
```
[Local Users]
Identity=unix-group:power
Action=org.freedesktop.upower.*
ResultAny=yes
ResultInactive=no
ResultActive=yes
```

**_File 1:_  /etc/polkit-1/localauthority/50-local.d/org.freedesktop.consolekit.pkla**
```
[Local restart]
Identity=unix-group:power
Action=org.freedesktop.consolekit.system.restart
ResultAny=yes
ResultInactive=no
ResultActive=yes
 
[Local shutdown]
Identity=unix-group:power
Action=org.freedesktop.consolekit.system.stop
ResultAny=yes
ResultInactive=no
ResultActive=yes
 
[Local restart - multiple]
Identity=unix-group:power
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=yes
ResultInactive=no
ResultActive=yes
 
[Local shutdown - multiple]
Identity=unix-group:power
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=yes
ResultInactive=no
ResultActive=yes
```

Make sure your user is added to the power group and reboot for it to take effect.

---

### Post by Habitual on 2015-07-19
If you create a new user on the system and add the new user to the same  groups you are in now and log in as the new user, does the problem  remain?

For system info in terminal (for LinuxMint) run this:
```
inxi -Sxx | pastebin
``` 
and paste the link here.

Thank you.

---

### Post by gabriel50 on 2015-07-20
Hi sorry for my delay...   

Toz i made what you told me, but it didn't work.... something i notice is when a get into the tty and i put startx, it gets me into Cinnamon being in XFCE and thats odd, because i have as default shell xfce, I've configured it in the log in screen, and in the users configuration....  Maybe it could be a bug in linux mint 17.2, i don't know, i checked every group, every permission, everything and nothing's changed


Habitual, i created a new administrator user, because i only have one, and i added to the same groups, and the issue remains...

here's the link you asked me.... 

[http://paste.linuxmint.com/view/ttzb](http://paste.linuxmint.com/view/ttzb)

thank you to all.

---

