---
title: "Script won't run at login 15.10"
date: 2016-03-02
forum: General Help
---

### Post by musicboy on 2016-03-02
here's the script which is set as executable and also I have set dconf to allow scripts to execute which enables user to be able to click on a script to start it, rather than using terminal, other wise it will just open in gedit.

#!/bin/sh
xmodmap ~/.xmodmap
evrouter /dev/input/event5

in:

/home/*username*//scripts/xmodauto.sh

IF I log in and then click on this script, it runs and enables my .xmodmap and evrouter settings to set a Microsoft 7000 keyboard wheel in the middle of the split keyboard to zoom in and out and it DOES work if I do that. It also works if I get the commands in the script and run them from terminal so they ALL 100% work no issues, until I obviously restart then I have to do it again.

bash /home/*username*/scripts/xmodauto.sh
device  0: /dev/input/event5: Microsoft Microsoft® 2.4GHz Transceiver V1.0
Display name: :0
Parsed 2 rules, 144 bytes

SO that works fine.

My evrouterrc:

/home/*username*/.evrouterrc

"Microsoft Microsoft® 2.4GHz Transceiver V1.0" "/dev/input/event5" none key/418 "XKey/XF86ZoomIn"
"Microsoft Microsoft® 2.4GHz Transceiver V1.0" "/dev/input/event5" none key/419 "XKey/XF86ZoomOut"

My xmodmap

/home/*username*/.xmodmap

keycode 255 = XF86ZoomIn
keycode 254 = XF86ZoomOut

A file is created in /temp

.evrouter:0 

5625

this number changes every time I run it after restarting.

I tried to create a xmodauto.desktop file in /home/*username*/.config/autostart

[Desktop Entry]
Type=Application
Terminal=false
Exec="/home/skelm/scripts/xmodauto.sh"
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_IN]=starts xmod for evrouter - Microsoft 7000

I tried:

Terminal:true

Exec=/home/skelm/scripts/xmodauto.sh

Without the " " marks.
I also tried that with and without Terminal:false

I also tried:

Exec=bash /home/skelm/scripts/xmodauto.sh

and:

Exec=bash "/home/skelm/scripts/xmodauto.sh"

Nothing I do works I even tried upstart and also init.d etc that didn't work either.

Has anyone got any ideas they can point me towards as I am baffled why only this script would not start at login and other things will?

Thanks

---

### Post by ian-weisser on 2016-03-02
Did you try the script istelf (not the desktop file) in ~/.config/autostart?

---

### Post by musicboy on 2016-03-02
Yes this is what I am saying the script: xmodauto.sh I can click on that as I have set it by right clicking and allowing as executable. And that actually doesn't fully work in Ubuntu you have to THEN set scripts to be allowed to be executable in dconf editor.

And yes it does work I have to manually do it every time I boot. I have set a makelink to it and placed it on my desktop. But its very annoying having to do that every time if I have to reboot a few times in a row.

Thanks for any help.

---

### Post by Jacqes on 2016-03-20
Hello!

I was struggling with this some time ago. I'm on Ubuntu 14.04, so I don't know if this will work for sure but it's worth a try!

I found this script from somian: [https://gist.github.com/somian/f85bb1af2420627db848](https://gist.github.com/somian/f85bb1af2420627db848) which loads a .Xmodmap file in your ~/ directory.

So, all you have to do is, download the script and save it to ~/ folder. Then add a new startup application with this code:```
python LoadUserXmap.py
```

I hope this helps!

Edit:

There are also other workarounds that might work:
[URL="http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04/514277#514277"]
http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04/514277#514277[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2279616&p=13292432#post13292432"]
http://ubuntuforums.org/showthread.php?t=2279616&p=13292432#post13292432[/URL]

---

