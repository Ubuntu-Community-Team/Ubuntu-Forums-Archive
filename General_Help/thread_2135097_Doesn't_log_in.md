---
title: "Doesn't log in"
date: 2013-04-13
forum: General Help
---

### Post by captainwithershins on 2013-04-13
I can't log in to ubuntu. When I typo un my password the screen flashes and returns me to the login screen. I tried removing .Xauthority and reinstalling the graphics driver but both didn't work.

---

### Post by Zukaro on 2013-04-13
I'm having the same issue too.  :V
Are you getting the error "mountall: unable to connect to plymouth"?

I don't however, know a fix, but I do know a workaround so you can at least use Ubuntu in the meantime.
Switch to another tty (ctrl+alt+F1 - 7 (F7 will be your login screen by default, so switch between 1 - 6)), type "startx" without quotes then press ctrl-c to stop xauth (not sure why but letting that run seems to prevent you from getting on; it'll still start x but you'll be presented with a black screen).  Then once you see your desktop Ubuntu will tell you the keyring is locked (something like that) so enter your password, then press ctrl+alt+t to open a terminal and type "unity" to start Unity.  This is just a workaround however and won't actually fix the issue; it'll allow you to get on for now though if you desperately need to do so.  As well, you'll have to redo this every time you login.

As for a fix, I don't know of one yet.

---

### Post by captainwithershins on 2013-04-13
I hope someone knows a fix.

---

### Post by captainwithershins on 2013-04-13
When I enter ''startx'' I get "Failed to load session "ubuntu"". I can't even get into guest.

---

### Post by captainwithershins on 2013-04-13
Bump!

---

### Post by steeldriver on 2013-04-13
I'm not familiar with Zukaro's fix, but afaik you can't start a Unity-based session via 'startx' anymore

In any case it sounds like the lightdm 'greeter' is working (i.e. you get a GUI login screen?)

You could try looking for errors in your ~/.xsession-errors file, and also maybe the lightdm logs

```
sudo tail /var/log/lightdm/lightdm.log

sudo tail /var/log/lightdm/x-0-greeter.log
```

Do you have any desktop customizations like custom wallpapers? Is your home dir encrypted? Have you checked the free space on /home (e.g. "df -h")? Is your home dir owned and writable by you?

```
ls -ld $HOME
```

---

### Post by captainwithershins on 2013-04-13
I do get a GUI screen. I have a custom wallpaper. The commands are in the attachments. I had Gnome before but I removed it.

---

### Post by steeldriver on 2013-04-13
So your lightdm.log seems to indicate failure during authentication - are you sure you successfully removed your ~/.Xauthority file? What about the .ICEauthority file?

```
ls -l ~/.{ICE,X}authority
```

---

### Post by captainwithershins on 2013-04-13
.Xauthority is gone, .ICEauthority too. Problem stays. Doesn't look like it made new ones.

---

### Post by steeldriver on 2013-04-13
Hmm well I don't know - at this point I would probably try

```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.bak

sudo dpkg-reconfigure lightdm

sudo dpkg-reconfigure unity-greeter
```

Did you have autologin enabled?

---

### Post by captainwithershins on 2013-04-14
:sad:  Still no luck. lightdm.conf:[SeatDefaults]
user-session=
greeter-session=unity-greeter

users.conf:#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

---

### Post by captainwithershins on 2013-04-14
UPDATE! Installed gnome-shell, reinstalled unity/compiz, removed gnome shell. Now in the login screen I can boot only into gnome classic(no unity option). I do that, it logs in, I open terminal enter unity, unity starts and all is good. Just no unity option in the login screen.

How do I add unity?

---

### Post by captainwithershins on 2013-04-14
Bump!

---

### Post by steeldriver on 2013-04-14
Do you have an ubuntu.desktop file in your /usr/share/xsessions? I *think* that's where it gets the list of sessions for the login greeter from e.g. mine has

```
$ ls /usr/share/xsessions/
gnome.desktop  gnome-shell.desktop  ubuntu-2d.desktop  **ubuntu.desktop**  xfce.desktop
$
$ cat /usr/share/xsessions/ubuntu.desktop 
[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
[B]Exec=gnome-session --session=ubuntu
TryExec=unity[/B]
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

It's provided by the gnome-session package apparently:

```
$ apt-file search /usr/share/xsessions/ubuntu.desktop 
gnome-session: /usr/share/xsessions/ubuntu.desktop
```

---

### Post by captainwithershins on 2013-04-14
Thanks!

What worked was:

```

[Desktop Entry] Name=Ubuntu 
Comment=This session logs you into Ubuntu [B]
Exec=unity[/B] 
Icon= 
Type=Application 
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

---

### Post by captainwithershins on 2013-04-14
Nevermind fixed it. Thanks to all.

---

