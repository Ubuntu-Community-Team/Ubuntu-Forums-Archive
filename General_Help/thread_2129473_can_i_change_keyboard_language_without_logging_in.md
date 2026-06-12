---
title: "can i change keyboard language without logging in"
date: 2013-03-26
forum: General Help
---

### Post by Rohitwrites on 2013-03-26
I am using Ubuntu 12.04 . I accidentally deleted English from my keyboard languages and let Kannada stay. I then rebooted my system. 

 Now Kannada Keyboard is activated and i cannot login since my password is in English.

 Is there a solution to this problem. How can i restore my keyboard to English.

---

### Post by slickymaster on 2013-03-26
At login press Ctrl+Alt+F1 and you'll be prompted to a terminal window where you'll have to login. After that just change the value of XKBLAYOUT to **en** in your **/etc/default/keyboard **file:
```
sudo nano /etc/default/keyboard
```

It shoud be something like this:
```
# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
[COLOR=#ff0000]XKBLAYOUT="en"[/COLOR]
XKBVARIANT=""
XKBOPTIONS=""

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
```

---

### Post by Rohitwrites on 2013-03-27
I tried doing this and changed the xkblayout value from us to en. 

But the Keyboard language is still Kannada. 

What else can be done? I did dpkg-reconfigure keyboard-configuration , it also didnot work.

---

### Post by slickymaster on 2013-03-27
I have to apologize, the value of XKBLAYOUT in your **/etc/default/keyboard** file should be _**uk**_, and not 'en' like I posted before.

Please correct it to the appropriate value so it will be like this:
```
# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
[COLOR=#ff0000]XKBLAYOUT="uk"[/COLOR]
XKBVARIANT=""
XKBOPTIONS=""

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
```

After correcting it, run the following command:
```
sudo dpkg-reconfigure console-setup
```

---

### Post by Rohitwrites on 2013-03-27
I did change the xkblayout value to uk and ran sudo dpkg-reconfigure console-setup

But the problem still persists, English keyboard is not getting activated.

What can i do next?

---

### Post by slickymaster on 2013-03-27
Try to see if [this]("http://ubuntuforums.org/showthread.php?t=1192865&p=7490888#post7490888") can anyhow help you.

---

