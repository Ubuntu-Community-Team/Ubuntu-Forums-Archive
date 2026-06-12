---
title: "detect when process of specific name newly starts"
date: 2014-12-30
forum: General Help
---

### Post by cedardoc on 2014-12-30
I have a script that opens a new google chrome tab, but because chrome is already running, my devilspie2 doesn't detect it as a new window to bring it forward above other windows.

I noticed when I run "top" in a terminal a new process comes up with the name "chrome" under the command column.

How can I detect when a new process of a certain name is created so I can instantly run something (xdotool or wmctrl) to bring that window forward?


thanks, 
Dave

---

### Post by cedardoc on 2015-01-06
anyone?

Is this not the right forum for this question maybe?

---

### Post by Holger_Gehrke on 2015-01-06
Why not go at it the other way around ? Check whether chrome is already running (pgrep chrome) in your script before it starts it. If it is, bring it to the front.

---

### Post by CantankRus on 2015-01-06
Maybe you could use wmctrl to focus chrome in your script.
wmctrl allows you to do various window manager actions from the command line. A useful feature is "wmctrl -a <str>", 
which will switch to a window containing the string <str> in the title.

List your windows to find an appropriate string.
eg I have **[COLOR="#FF0000"]google-chrome[/COLOR]** open with some other windows...
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] wmctrl -l**
0x0560001a  0 Trusty Unread - Opera
0x0280000a -1 Trusty Desktop
0x07000002  0 Trusty XdndCollectionWindowImp
0x07000005  0 Trusty unity-launcher
0x07000008  0 Trusty unity-panel
0x0700000b  0 Trusty unity-dash
0x0700000c  0 Trusty Hud
0x04600007  0 Trusty Home
[COLOR="#FF0000"]0x06600001  0 Trusty Ubuntu Forums - **Google Chrome**[/COLOR]
0x04e00001  0 Trusty [all variants] detect when process of specific name newly starts - Opera
```

So for google-chrome I could use the string "**Google Chrome**" to focus google-chrome.
eg to open an ubuntuforums tab and focus google-chrome...
```
google-chrome ubuntuforums.org && wmctrl -a "**Google Chrome**"
```

You would need to install wmctrl.

---

### Post by cedardoc on 2015-01-06
D'oh! Why didn't I think of that!  Thanks, both of you :)

---

