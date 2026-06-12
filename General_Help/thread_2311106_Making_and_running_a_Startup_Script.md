---
title: "Making and running a Startup Script"
date: 2016-01-24
forum: General Help
---

### Post by rigel4 on 2016-01-24
Hi all
I have bought my self a new keyboard CMStorm and it has back lighting..
To activate the keyboard lights you have to press scroll lock.  
This doesn't work in Ubuntu.. but someone has made a simple command line
to run in the terminal that makes the Scroll lock switch on the keyboard lights.

the problem is you have to do this every time the PC starts.. I was wondering if someone can help make 
a script that would run on startup .. so there is no need to run the command in the terminal every time.

sudo xmodmap -e 'add mod3 = Scroll_Lock'

Sorry about the title .. that’s what happens when the lights are off :)

Maybe there is a better way that i have not yet come across..
thanks in advance.

---

### Post by bytr on 2016-01-24
"/etc/rc.local" is a script that is automatically run at system startup. You can add your command to it.

---

### Post by ajgreeny on 2016-01-24
You can add the command to /etc/rc.local so it looks like this; note that you don't need the sudo prefix as it will be run as root at boot
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR="#FF0000"]xmodmap -e 'add mod3 = Scroll_Lock'[/COLOR]
exit 0
```
You will need to edit /etc/rc.local as root, so either use ```
sudo nano /etc/rc.local
``` or ```
sudo -H gedit /etc/rc.local
``` to do that.

---

### Post by rigel4 on 2016-01-24
Thank you I am going try it now :)

---

### Post by rigel4 on 2016-01-24
I tried copying the code line into rc.local
but after reboot .. the command hadn't run!

I'm a bit out of my depth here really..
maybe you could help me understand what&#8217;s wrong with it.

I'm wondering if i need to make a separate script and have
rc.local call it or something..

It not the end if i can t get it working as it does work manually.

---

### Post by matt_symes on 2016-01-24
Hi

You'll want the full path to xmodmap in the rc.local file.

```
/usr/bin/xmodmap .....
```

One question though, is X actually running at that point ?

I can't actually remember as it's been ages since I've looked.

You may want to add that command to the startup script of LightDm (if that's what you're using). That's what worked for me in the past.

Kind regards

---

### Post by maglin2 on 2016-01-24
Just a fairly uneducated thought - but might there be a systemd issue if this is 15.10? I don't know if it implements rc.local

---

### Post by matt_symes on 2016-01-24
Hi

> **maglin2 said:**
> Just a fairly uneducated thought - but might there be a systemd issue if this is 15.10? I don't know if it implements rc.local

I'm pretty sure that systemd has the ability to run rc.local using the systemd service rc-local.service.

Of course, rc.local needs to be executable but it should be by default.

I'll check to see if it does actually run because I've not used rc.local for a long while.

**EDIT:**

Looks to be started correctly.

```
matthew-xu-16-04:/home/matthew:0 % systemctl status rc-local.service 
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   **Active: active (exited) since Fri 2016-01-22 04:23:54 GMT; 2 days ago**
  Process: 888 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)
    Tasks: 0 (limit: 512)

**Jan 22 04:23:54** matthew-xu-16-04 systemd[1]: Starting /etc/rc.local Compatibility...
**Jan 22 04:23:54** matthew-xu-16-04 systemd[1]: Started /etc/rc.local Compatibility.
matthew-xu-16-04:/home/matthew:0 
```

It's the 24th Jan now, so it was last run when i started this laptop; on the 22nd Jan.

Kind regards

---

### Post by rigel4 on 2016-01-24
I feel bad to be still asking about this, especially in such educated company.

I still can't get it to work.. remember with scripts I'm a beginner!

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
[COLOR=#ff0000]/usr/bin/xmodmap -e 'add mod3 = Scroll_Lock'[/COLOR]

exit 0
```

---

### Post by matt_symes on 2016-01-24
Hi

There's nothing wrong with the script that i can see, so i don't think that's the problem.

Please post the output of this command

```
systemctl status rc-local.service
```

```
ls -l /etc/rc.local
```

```
echo $DESKTOP_SESSION
```

Run a sanity check. Run the xmodmap command in the terminal. Does it remap the key ?

The problem may be that X is not running when rc.local is run. As i said, it's been a long while since i looked. I'll look for you.

Kind regards

---

### Post by rigel4 on 2016-01-24
Thanks again for helping me!

yes the command works manually in the terminal.

Output from first command!


```
alex@alex-Z97P-D3:~$ systemctl status rc-local.service
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Sun 2016-01-24 22:18:40 GMT; 24min ago
  Process: 679 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)

Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Starting /etc/rc.local Compatibility...
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Control process e...1
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Failed to start /etc/rc.local Compa....
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Unit entered fail....
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Failed with resul....
Jan 24 22:18:40 alex-Z97P-D3 rc.local[679]: /usr/bin/xmodmap:  unable to ope...'
Hint: Some lines were ellipsized, use -l to show in full.
alex@alex-Z97P-D3:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 351 Jan 24 22:17 /etc/rc.local
alex@alex-Z97P-D3:~$ echo $DESKTOP_SESSION
ubuntu
alex@alex-Z97P-D3:~$ systemctl status-l rc-local.service
Unknown operation 'status-l'.
alex@alex-Z97P-D3:~$ systemctl status -l rc-local.service
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Sun 2016-01-24 22:18:40 GMT; 34min ago
  Process: 679 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)

Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Starting /etc/rc.local Compatibility...
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Control process exited, code=exited status=1
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Failed to start /etc/rc.local Compatibility.
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Unit entered failed state.
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Failed with result 'exit-code'.
Jan 24 22:18:40 alex-Z97P-D3 rc.local[679]: /usr/bin/xmodmap:  unable to open display ''

```

Second Command

```
alex@alex-Z97P-D3:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 351 Jan 24 22:17 /etc/rc.local
```


```
alex@alex-Z97P-D3:~$ echo $DESKTOP_SESSION
ubuntu

```

---

### Post by matt_symes on 2016-01-24
Hi

> **rigel4 said:**
> Thanks again for helping me!

No worries.

> ```
alex@alex-Z97P-D3:~$ systemctl status rc-local.service
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Sun 2016-01-24 22:18:40 GMT; 24min ago
  Process: 679 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)

Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Starting /etc/rc.local Compatibility...
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Control process e...1
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Failed to start /etc/rc.local Compa....
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Unit entered fail....
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Failed with resul....
**Jan 24 22:18:40 alex-Z97P-D3 rc.local[679]: /usr/bin/xmodmap:  unable to ope...'**
Hint: Some lines were ellipsized, use -l to show in full.
alex@alex-Z97P-D3:~$ 

```

rc-local.service is failing but the error message is being truncated :/

```
/usr/bin/xmodmap:  unable to ope...'
```

I suspect the above truncated message may be stating "unable to open X server" or something similar.

Please post the output of the command below so we can try to see the full message. I think the -l switch was still used in 15.10.

```
PAGER=cat journalctl -u rc-local.service -n 7 -l
```

Kind regards

---

### Post by rigel4 on 2016-01-24
```
alex@alex-Z97P-D3:~$ PAGER=cat journalctl -u rc-local.service -n 7 -l
-- Logs begin at Sun 2016-01-24 22:18:39 GMT, end at Sun 2016-01-24 22:41:11 GMT. --
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Starting /etc/rc.local Compatibility...
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Control process exited, code=exited status=1
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: Failed to start /etc/rc.local Compatibility.
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Unit entered failed state.
Jan 24 22:18:40 alex-Z97P-D3 systemd[1]: rc-local.service: Failed with result 'exit-code'.
Jan 24 22:18:40 alex-Z97P-D3 rc.local[679]: /usr/bin/xmodmap:  unable to open display ''
alex@alex-Z97P-D3:~$ 

```

---

### Post by mc4man on 2016-01-24
I'd try the command as a user, ie. no sudo. If it works (should), then just use  Startup Applications from menu or create a .desktop in ~/.config/autostart.

---

### Post by matt_symes on 2016-01-24
Hi

> **rigel4 said:**
> ```
**Jan 24 22:18:40 alex-Z97P-D3 rc.local[679]: /usr/bin/xmodmap:  unable to open display ''**
alex@alex-Z97P-D3:~$ 

```

That's the problem then. No display variable under root. 

I did just run a test using my username, in rc.local, and it also didn't work.
```

matthew-xu-16-04:/home/matthew:0 % grep sudo /etc/rc.local          
sudo -u matthew /usr/bin/xmodmap -e 'add mod3 = Scroll_Lock'
matthew-xu-16-04:/home/matthew:0 % systemctl status rc-local.service 
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Sun 2016-01-24 23:29:51 GMT; 7min ago
  Process: 886 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)

Jan 24 23:29:48 matthew-xu-16-04 systemd[1]: Starting /etc/rc.local Compatibility...
Jan 24 23:29:50 matthew-xu-16-04 sudo[889]:     root : TTY=unknown ; PWD=/ ; USER=matthew ; COMMAND=/usr/bin/xmodmap ...l_Lock
Jan 24 23:29:50 matthew-xu-16-04 sudo[889]: pam_unix(sudo:session): session opened for user matthew by (uid=0)
Jan 24 23:29:51 matthew-xu-16-04 rc.local[886]: /usr/bin/xmodmap:  unable to open display ''
Jan 24 23:29:51 matthew-xu-16-04 sudo[889]: pam_unix(sudo:session): session closed for user matthew
Jan 24 23:29:51 matthew-xu-16-04 systemd[1]: rc-local.service: Control process exited, code=exited status=1
Jan 24 23:29:51 matthew-xu-16-04 systemd[1]: Failed to start /etc/rc.local Compatibility.
Jan 24 23:29:51 matthew-xu-16-04 systemd[1]: rc-local.service: Unit entered failed state.
Jan 24 23:29:51 matthew-xu-16-04 systemd[1]: rc-local.service: Failed with result 'exit-code'.
Hint: Some lines were ellipsized,
```

> **mc4man said:**
> I'd try the command as a user, ie. no sudo. If it works (should), then just use  Startup Applications from menu or create a .desktop in ~/.config/autostart.

Therefore, this is your best bet i think and is the best suggestion.

It should run xmodmap after you've logged in but i don't suspect you'll need the key remapped on LightDM's screen.

Open a terminal and copy and paste this entire code block into it and then hit enter.

```
cat <<EOF>>~/.config/autostart/remap-keys.desktop
[Desktop Entry]
Name=Remap
Comment=Remap
Exec=/usr/bin/xmodmap -e 'add mod3 = Scroll_Lock'
EOF
```

Log out and then log back in.

Is the key remapped ?

Kind regards

---

### Post by ian-weisser on 2016-01-24
A lot of older advice won't work anymore. The plumbing of boot and login have changed in the past couple years.

Under systemd (15.04 and newer):
systemd handles the boot, and runs rc.local, and finally starts lightdm (the login screen).
After you login, lightdm launches Upstart, which in turn launches X and other user-level tasks. systemd handles only system-level tasks, and is not involved.

rc.local won't help because X is not running yet.
systemd tasks and targets won't help because xmodmap shouldn't be running as root.

The simplest way to run a user-level post-login script is to place the script in each user's /home/$USER/.config/autostart (matt_symes solution in Post #15)
Another way is to create an Upstart job in ~/.config/upstart
There are more ways, but they get arcane.

---

### Post by mc4man on 2016-01-25
If there are issues with proposed startup .desktop this would be a decent generic one
```
[Desktop Entry]
Name=Remap
Type=Application
Exec=/usr/bin/xmodmap -e 'add mod3 = Scroll_Lock'
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=
```

Note -
 X-GNOME-Autostart-enabled=true is usually needed so it actually runs
Name=  you can use whatever you want
X-GNOME-Autostart-Delay= is only used if it has a value after =, otherwise ignored.
 (- sometimes it's beneficial to slightly delay the running of the autostart .desktop, so for ex. a 2 sec delay would be - 
X-GNOME-Autostart-Delay=2

---

### Post by rigel4 on 2016-01-25
Thank you all for your generous help. 
I haven't got it working yet ..  but I&#8217;m sure I will
with the information and help you have all given me..

I'll post back later when I have some good news.
Thanks again 

Rigel4

---

### Post by Jacqes on 2016-03-20
Hi rigel4!

take a look at this:[ http://ubuntuforums.org/showthread.php?t=2315818&p=13458209#post13458209]("http://ubuntuforums.org/showthread.php?t=2315818&p=13458209#post13458209")

Maybe you can solve it with that, the script worked for me. The instructions are on the link.

---

