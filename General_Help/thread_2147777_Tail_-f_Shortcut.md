---
title: "Tail -f Shortcut"
date: 2013-05-23
forum: General Help
---

### Post by kjacobs on 2013-05-23
Hello all,

I have been a user of Xubuntu for a couple years now and lovin it. I have a custom launcher on my desktop that uses the command "tail -f /home/.........." to launch a logging txt file into a terminal, and it works great. However, when I switch over to Lubuntu, this launcher just generates an error....."Failed to change to directory '' (No such file or directory)". Why would this work in Xubuntu and not in Lubuntu. I have tried recreating the shortcut a dozen times with no luck. Yet, if I open LXTerminal and physically type the tail -f /home/......command, it works fine.

Any ideas as to why the shortcut works in X and not in L???

Thanks in advance............

---

### Post by MG&amp;TL on 2013-05-23
Can you post your launcher contents? You might need to tell it to open in a terminal or something.

---

### Post by kjacobs on 2013-05-23
Here is the launcher shortcut.....as setup in xubuntu. The contents are the same in the lubuntu shortcut....

BBS Monitor.desktop

[Desktop Entry]
Version=1.0
Type=Application
Name=BBS Monitor
Comment=
Exec=tail -f /home/kenneth/Linbpq/logLatest_BBS.txt
Icon=7767_BPQ32.0
Path=
Terminal=true
StartupNotify=false
GenericName=

I have tried adding terminal and lxterminal in front of the tail -f command, but if fails to launch that way as well. Thanks.

Ken

---

### Post by MG&amp;TL on 2013-05-23
> **kjacobs said:**
> 
Name=BBS Monitor
Comment=
Exec=tail -f /home/kenneth/Linbpq/logLatest_BBS.txt
Icon=7767_BPQ32.0
**Path=**
Terminal=true
StartupNotify=false
GenericName=


I'm not sure if this is supposed to happen, but I suspect LXDE just handles this differently to XFCE. According to [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html), the "Path" key tells the desktop environment what path to run the application in. I suspect that because you have given it a 'value' XFCE just ignored it (because it's just whitespace) but LXDE tried to changed directory to an empty path, creating an error. Try this instead:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=BBS Monitor
Exec=tail -f /home/kenneth/Linbpq/logLatest_BBS.txt
Icon=7767_BPQ32.0
Terminal=true
StartupNotify=false

```

(Note removed empty keys).

If that doesn't work either, try using

```
lxterminal **-e** tail -f /home/kenneth/....
```

Which will hopefully work. This is just guessing, but I'll be on my LXDE machine in a few hours anyway, so I'll test it then.

---

### Post by kjacobs on 2013-05-23
AHA! The second option worked....all because of one little -e....LOL.

lxterminal -e tail -f /home/kenneth/Linbpq/logLatest_BBS.txt

The first option above simply opened terminal, but did not begin the tail function. Anyway, it works like a champion. Many thanks.

---

### Post by MG&amp;TL on 2013-05-23
> **kjacobs said:**
> AHA! The second option worked....all because of one little -e....LOL.

lxterminal -e tail -f /home/kenneth/Linbpq/logLatest_BBS.txt

The first option above simply opened terminal, but did not begin the tail function. Anyway, it works like a champion. Many thanks.

Great. :D

Incidentally, all the '-e' option does is tell the terminal to start executing a script immediately. Just FYI.

---

