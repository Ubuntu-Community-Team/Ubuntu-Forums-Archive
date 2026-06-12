---
title: "A terminal that can open a new tab by command line?"
date: 2013-09-23
forum: General Help
---

### Post by sberla54 on 2013-09-23
[COLOR=#101010][FONT=Ubuntu]Hi guys,
for work purposes, me and my job mates are using bash script that use telnet to login into some different kind of devices. At every new login, a new tab is opened with the session of the new device.

We all use Ubuntu with Unity or Gnome 3 but we are forced to use Konsole (bringing with it a lot of KDE) because it's the only one that is able to open a new tab with a command [/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu] ("konsole --new-tab -p tabtitle=$1").
[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]It's even the only one that has a really powerful internal search engine, that can highlight the searched word and stuff like this.[/FONT][/COLOR]

Terminal has a command to open a new tab but is bugged and instead of opening a tab opens a windows. That bug is been there for a long time...

Is there any other terminal that has these 2 features? New tab by command line and search engine? 
It would be great if it was desktop enviroment independent.

We tried RoxTerm and ATerm but they haven't what we're searching for.

Thank you in advance.

Best regards.

---

### Post by Vaphell on 2013-09-24
[http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line](http://stackoverflow.com/questions/1188959/open-a-new-tab-in-gnome-terminal-using-command-line)

you might want to try hacking out a solution using xdotool to emulate ctrl+shift+t for new tab and to type the command to run
```
wid=$( xprop -root | awk '/_NET_ACTIVE_WINDOW\(WINDOW\)/{ print $5; }' )
xdotool windowfocus $wid
xdotool key ctrl+shift+t
sleep 2
xdotool type $'echo omgwtfbbq\n'

```

---

### Post by markbl on 2013-09-24
You should consider using screen or tmux (preferred) for this functionality instead. That's a better way to multiplex multiple terminal sessions rather than using tabs.

---

