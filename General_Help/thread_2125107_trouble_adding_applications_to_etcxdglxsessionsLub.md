---
title: "trouble adding applications to /etc/xdg/lxsessions/Lubuntu/autostart"
date: 2013-03-13
forum: General Help
---

### Post by sarar on 2013-03-13
When I add an application to autostart and try to save the file it says it "can't open file to write" and won't save. What is happening?

---

### Post by ibjsb4 on 2013-03-13
```
gksudo leafpad /etc/xdg/lxsessions/Lubuntu/autostart
```

Is that the command your using?

---

### Post by sarar on 2013-03-13
Well. I used that command and was able to save a change. But when i rebooted, nothing autostarted. I opened up a terminal and opened the autostart file, and sure enough, nothing was there.

---

### Post by ibjsb4 on 2013-03-13
From what I am reading, thats not the way to do it in lubuntu.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=autostart+program+lubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=autostart+program+lubuntu&sa=Search&cof=FORID:9)

---

### Post by Gaygerbil on 2013-05-12
Goto

/etc/xdg/lxsession/Lubuntu

and find a text file named autostart, open it as root and add

```
@**APPLICATIONCOMMAND**
```

If you tell me the application you're trying to launch it would probably help I know a lot of times the application names aren't the same as the command, anything that doesn't work with autostart gets deleted I believe.

There is a second way of doing it as well, you could make the .desktop file for your application and place it in the /etc/xdg/autostart folder.

Like I said earlier though I think it's probably something up with the command you're writing.

---

