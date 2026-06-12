---
title: "Shut down menu option not working"
date: 2013-06-17
forum: General Help
---

### Post by Arjunanda on 2013-06-17
We have three desktop computers on Dell hardware, installed some 4 years ago. These PC's are for our guest to get online.
Currently they are running ubuntu 12.04.

Recently I noticed two of them are having a problem: The Shut Down menu option in Unity does not work. When you select "Shut Down" from the upper right hand corner menu, you will get the pop up window to confirm. When you hit the "Shut down" button there, the pop-up disappears, but nothing happens.

I can shut down the PC nicely from commandline. But it would be useful to allow the users also to shut down the system when they finish.

It might be, that one temporary admin had made some changes with lock down editor (perhaps pessulus) as he mentioned planning something along this line, but now Pessulus is depreciated in 12.04 and it is not installed in the system. This person left, and he did not document the changes he made.

Does this sound like some change he might have made, or is this some strange Ubuntu bug?

---

### Post by matt_symes on 2013-06-17
Hi

> **Arjunanda said:**
> Does this sound like some change he might have made, or is this some strange Ubuntu bug?

Could be either.

Just to get a feel for what is going on, open a terminal and type these different shutdown commands.

Which ones work - if any ?

```
gnome-session-quit
```

```
/usr/lib/indicator-session/gtk-logout-helper --shutdown
```

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

What do these commands return ?

```
ls -l /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

```
cat /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
```

Kind regards

---

### Post by Arjunanda on 2013-06-17
Just noticed that it is not only shut down, but also reboot and log out for that user.
If I switch user from the upper right user switcher, and log in as guest, the log out works for guest account. But shut down from guest session does not, it just returns to login screen.

Rebooting now. Next will test your commands.

---

### Post by Arjunanda on 2013-06-17
Hahaa!!! :))))

Thanks - now it is clear.
> 
gnome-session-quit

** (gnome-session-quit:2757): WARNING **: Failed to call logout: Logout has been locked down


So now checking your other commands.

> /usr/lib/indicator-session/gtk-logout-helper --shutdown

Gives the log out confirmation pop-up, but hitting the button does nothing, nor any error message.

---

### Post by Arjunanda on 2013-06-17
And here is the output for the rest of the commands:

> $ ls -l /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
-rw-r--r-- 1 root root 1652 Feb 25  2012 /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy

> $ cat /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<!--
Policy definitions for ConsoleKit
-->

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

</policyconfig>

So it appears this temporary admin did try some lock down features, but did not document his work, did not communicate to me and perhaps also the tool he used was removed in upgrade to 12.04.

Now just need to find how to re-enable the logout.

Thanks, great to learn these things :)

---

### Post by matt_symes on 2013-06-17
Hi

Did you try this command ?

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

It will call console kit directly, bypassng the session manager and should, and i say should reservedly, shut it down as the polkiy file for console kit looks fine. 

It will not offer the option to save any open documents though, as that is the preserve of the session manager, but it will be a useful confirmation of exactly what has been locked down.

I'm not sure how it was locked down by that software but i think there are only a number of areas that it can be locked down.

I will be away until this evening though, so i cannot offer guidance until then.

In the meantime, if you do find a solution then please post it back here :)

EDIT:

As another check for console kit, can you post the output of

```
ls -l /usr/lib/ConsoleKit/scripts/ck-system-stop
```

and 

```
cat /usr/lib/ConsoleKit/scripts/ck-system-stop
```

Kind regards

---

### Post by Arjunanda on 2013-06-17
Yes I did, and it worked - it shut down the system cleanly.

I think the stuff is in the policy kit file > /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
Looking into that now. The syntax is not the most straight-forward.

---

### Post by matt_symes on 2013-06-17
Hi

> **Arjunanda said:**
> Yes I did, and it worked - it shut down the system cleanly.

I think the stuff is in the policy kit file 
Looking into that now. The syntax is not the most straight-forward.

If that shut it down cleanly then it has been locked down at the session manager level and that is where you'll need to look.

If you've had no luck by this evening, all look for you.

Kind regards

---

### Post by matt_symes on 2013-06-17
Hi

Try having a look under this key using gconf.

```
/desktop/gnome/lockdown
```

Anything useful under there in your version of Ubuntu ?

Maybe under this key (if it exists ?)

```
/org/gnome/desktop/lockdown/
```

If not check dconf settings as it may be stored there.

Kind regards

---

### Post by Arjunanda on 2013-06-17
Here is the output of these two commands:

> $ ls -l /usr/lib/ConsoleKit/scripts/ck-system-stop
-rwxr-xr-x 1 root root 191 Feb 25  2012 /usr/lib/ConsoleKit/scripts/ck-system-stop



> $ cat /usr/lib/ConsoleKit/scripts/ck-system-stop
#!/bin/sh

#Try for common tools
if [ -x "/sbin/shutdown" ] ; then
	/sbin/shutdown -h now
	exit $?
elif [ -x "/usr/sbin/shutdown" ] ; then
	/usr/sbin/shutdown -h now
	exit $?
else
	exit 1
fi


Now using gconf-editor, but so far not found there nothing that would help here.

> 
/desktop/gnome/lockdown

did not have anything related to shut down.

Now looking into dconf.

---

### Post by Arjunanda on 2013-06-17
Found!!!!

> $ gsettings list-recursively|grep lockdown
apps.onboard.lockdown disable-click-buttons false
apps.onboard.lockdown disable-hover-click false
apps.onboard.lockdown disable-preferences false
apps.onboard.lockdown disable-quit false
apps.onboard.lockdown disable-touch-handles false
org.gnome.gnome-panel.lockdown disable-force-quit false
org.gnome.gnome-panel.lockdown disabled-applets @as []
org.gnome.gnome-panel.lockdown locked-down false
org.gnome.desktop.lockdown disable-application-handlers false
org.gnome.desktop.lockdown disable-command-line false
org.gnome.desktop.lockdown disable-lock-screen true
[COLOR=#ff0000]**org.gnome.desktop.lockdown disable-log-out true**[/COLOR]
org.gnome.desktop.lockdown disable-print-setup false
org.gnome.desktop.lockdown disable-printing false
org.gnome.desktop.lockdown disable-save-to-disk false
org.gnome.desktop.lockdown disable-user-switching false


Now just have to learn how to change it. But really, I did not even know about the existance of gconf and dconf.

---

### Post by Arjunanda on 2013-06-17
Ok,

Did the following:
> gsettings set org.gnome.desktop.lockdown disable-lock-screen false
gsettings set org.gnome.desktop.lockdown disable-log-out false

And now it looks like this:
> $ gsettings list-recursively|grep lockdown
apps.onboard.lockdown disable-click-buttons false
apps.onboard.lockdown disable-hover-click false
apps.onboard.lockdown disable-preferences false
apps.onboard.lockdown disable-quit false
apps.onboard.lockdown disable-touch-handles false
org.gnome.gnome-panel.lockdown disable-force-quit false
org.gnome.gnome-panel.lockdown disabled-applets @as []
org.gnome.gnome-panel.lockdown locked-down false
org.gnome.desktop.lockdown disable-application-handlers false
org.gnome.desktop.lockdown disable-command-line false
org.gnome.desktop.lockdown disable-lock-screen false
org.gnome.desktop.lockdown disable-log-out false
org.gnome.desktop.lockdown disable-print-setup false
org.gnome.desktop.lockdown disable-printing false
org.gnome.desktop.lockdown disable-save-to-disk false
org.gnome.desktop.lockdown disable-user-switching false


Next I will test whether it works.

---

### Post by user_of_gnomes on 2013-06-17
Are you sure they're not shutting down? Sometimes the button doesn't seem to work for me either but it still shuts down after 60 seconds. Sometimes the menu disappears and it still shuts down. I have to look into why this is happening, using 13.04.

---

### Post by Arjunanda on 2013-06-17
Thanks matt_symes :)

The following solved the problem:

>  gsettings set org.gnome.desktop.lockdown disable-lock-screen false
gsettings set org.gnome.desktop.lockdown disable-log-out false 

And I learned tons in this process :) Ubuntu has changed a lot & Linux has evolved so much in these 15 years that I have been using it. I did not even know about dconf / gconf - perhaps heard about it but never used until now. And now I can see that it is very useful tool that can be used for so many things. Thanks a lot :)

---

