---
title: "Disable login screen on Lubuntu 18.04 LTS?"
date: 2018-10-26
forum: General Help
---

### Post by pandoragami on 2018-10-26
I know this thread has been asked millions of times but so far none of those threads have helped. What I do have are two machines, both with Lubuntu 18.04LTS and one of them was installed by default to pass through the password login to the desktop while the other was installed with the boot to login screen with the user name and password requirement (this second machine was actually an upgrade from 16.04 LTS). 

On the machine that has no login, I took all the files from the lightdm folder and passed them into the other machine but that still didn't work. I'm also unable to go into the "Users and Groups" app in the "System Tools" and change the setting for "ask user for password". Basically when I click on the checkbox for "Don't ask for password on Login" it saves the checkmark but then I get a popup error saying it wasn't saved in the configuration. I also wondered where is that file that it saves it to?

I also wondered if there might be other system files I should look at to change the login options.

---

### Post by #&amp;thj^% on 2018-10-26
without seeing the stuff you copied over to " the lightdm folder and passed them into the other machine "
Post back the content from:
```
cat /etc/lightdm/lightdm.conf
```
You may want to use [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for the output though, and leave the link here in your thread.

---

### Post by pandoragami on 2018-10-26
> **1fallen said:**
> without seeing the stuff you copied over to " the lightdm folder and passed them into the other machine "
Post back the content from:
```
cat /etc/lightdm/lightdm.conf
```
You may want to use [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for the output though, and leave the link here in your thread.

Here's the lightdm.conf

```

[Seat:*]
autologin-guest=false
autologin-user=pandoragami
autologin-user-timeout=0

```

Along with that there are several more files inside of /etc/lightdm

lightdm-gtk-greeter.conf

```

[greeter]
screensaver-timeout = 0

```

users.conf

```

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserList]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

inside of /etc/lightdm/lightdm-gtk-greeter.conf.d was 

30_lubuntu.conf

```

# LightDM GTK+ Configuration
# Available configuration options listed below.
#
# Appearance:
#  theme-name = GTK+ theme to use
#  icon-theme-name = Icon theme to use
#  background = Background file to use, either an image path or a color (e.g. #772953)
#  user-background = false|true ("true" by default)  Display user background (if available)
#  transition-duration = Length of time (in milliseconds) to transition between background images ("500" by default)
#  transition-type = ease-in-out|linear|none  ("ease-in-out" by default)
#
# Fonts:
#  font-name = Font to use
#  xft-antialias = false|true  Whether to antialias Xft fonts
#  xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
#  xft-hintstyle = none|slight|medium|hintfull  What degree of hinting to use
#  xft-rgba = none|rgb|bgr|vrgb|vbgr  Type of subpixel antialiasing
#
# Login window:
#  active-monitor = Monitor to display greeter window (name or number). Use #cursor value to display greeter at monitor with cursor. Can be a semicolon separated list
#  position = x y ("50% 50%" by default)  Login window position
#  default-user-image = Image used as default user icon, path or #icon-name
#  hide-user-image = false|true ("false" by default)
#
# Panel:
#  panel-position = top|bottom ("top" by default)
#  clock-format = strftime-format string, e.g. %H:%M
#  indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power", "~clock", "~host", "~spacer". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
#
# Accessibility:
#  a11y-states = states of accessibility features: "name" - save state on exit, "-name" - disabled at start (default value for unlisted), "+name" - enabled at start. Allowed names: contrast, font, keyboard, reader.
#  keyboard = command to launch on-screen keyboard (e.g. "onboard")
#  keyboard-position = x y[;width height] ("50%,center -0;50% 25%" by default)  Works only for "onboard"
#  reader = command to launch screen reader (e.g. "orca")
#
# Security:
#  allow-debugging = false|true ("false" by default)
#  screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
#
# Template for per-monitor configuration:
#  [monitor: name]
#  background = overrides default value
#  user-background = overrides default value
#  laptop = false|true ("false" by default) Marks monitor as laptop display
#  transition-duration = overrides default value
#
[greeter]
logo=/usr/share/icons/lubuntu/places/64/start-here.svg
background=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
theme-name=Lubuntu-default
icon-theme-name=lubuntu
font-name=Ubuntu
xft-antialias=true
#xft-dpi=
xft-hintstyle=full
xft-rgba=rgb
show-indicators=~host;~spacer;~clock;~spacer;~session;~language;~a11y;~power
#show-clock=
#clock-format=
#keyboard=



```

---

### Post by #&amp;thj^% on 2018-10-26
Try this, Paste the following lines
```

[Seat:*]
autologin-guest = false
autologin-user = pandoragami
autologin-user-timeout = 0

```
I use:
```
sudoedit /etc/lightdm/lightdm.conf
```
to make the edit>>>save and close this file.
Now try and reboot to see if any better.

---

### Post by pandoragami on 2018-10-26
> **1fallen said:**
> Try this, Paste the following lines
```

[Seat:*]
autologin-guest = false
autologin-user = pandoragami
autologin-user-timeout = 0

```
I use:
```
sudoedit /etc/lightdm/lightdm.conf
```
to make the edit>>>save and close this file.
Now try and reboot to see if any better.


Tried it to no avail. The login screen comes up as usual. Where are the "Users and groups" config stored in. I want to try and set the password on login feature, namely the checkbox that says "Don't ask for password on login". I can't change it from the gui because it always comes up with a configuration error when I click OK and then if I return to the same window it goes back to being unchecked.

---

### Post by #&amp;thj^% on 2018-10-26
One more try to that same file and add:
```
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter
```
And again reboot.

---

### Post by pandoragami on 2018-10-26
> **1fallen said:**
> One more try to that same file and add:
```
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter
```
And again reboot.

Nope, no luck. Any other suggestions?

---

### Post by pandoragami on 2018-10-27
What I've managed to do thus far is disable lightdm permanently with 

sudo systemctl disable lightdm.service

and now it boots into the command line. Next I wanted the command line to boot into my user account so I added a file  [COLOR=#444444][FONT=monospace]/etc/init/tty1.conf

and in that file I added 

[/FONT][/COLOR]exec /bin/login -f pandoragami < /dev/tty1 > /dev/tty1 2>&1

The problem is when I boot, I now get to the login command line and I still have to enter my username and password and then I get some errors saying

[ 714.733718] Could not find key with description: [ long number]
[ 714.735242] Could not find valid key in user session keyring for sig specified in mount option: [same long number]
[ 714.751740] Error parsing options; rc = [-2] 

any ideas.

I'm assuming I need to add my username to some group but I could be wrong. Not sure if the whole installation is corrupt and would be better for a reinstall.

---

### Post by pandoragami on 2018-10-28
I managed to get it to work by removing the encryption from the home folder. The computer boots into desktop no problem. Getting it to boot into command line with autologin is a different problem now.

---

