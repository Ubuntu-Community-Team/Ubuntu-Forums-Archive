---
title: "AutoStart Transmission on a delay"
date: 2016-06-10
forum: General Help
---

### Post by ken55 on 2016-06-10
Complete Noob Linux User here, so please respond to me as such :)

-Most Current Version of Lubuntu-

I have Transmission set to autostart at boot, I would like to put it on a 30 second delay as to allow my VPN to connect before it starts. I have read many threads all around, but no matter what I try, I just can't seem to get this to work.

I'm not sure if I'm editing wrong files in wrong areas or what. 

Any help is appreciated.

Thanks much,
Ken

---

### Post by deadflowr on 2016-06-10
Post methods tried, so we don't post them and make you crazy.

---

### Post by ken55 on 2016-06-10
Hi deadflowr :)

I've tried creating .conf files as well as editing the "command" line from within transmission's properties (both from the startmenu and the autostart folder). Ex: Changing "transmission-gtk %U" to "sleep30; transmission-gtk %U".

---

### Post by papibe on 2016-06-10
Hi ken55.

In order to start a task, you have several options depending on when do you want it starts.

If it is right after you login, and no before, you can use 'Startup Applications'.

If you want it to start, when you turn on the computer, regardless of login, you can use either:
[LIST]
[*]/etc/rc.local, or
[*]crontab (using the special time keyword @reboot)
[/LIST]
In order to delay the process, you can use a script with a sleep command. For instance:
```
#!/bin/bash
/bin/sleep 30s
env DISPLAY=:0 /usr/bin/transmission-gtk

```
I recommend using crontab because interferes less with the booting process.

I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by ken55 on 2016-06-10
> **papibe said:**
> Hi ken55.

In order to start a task, you have several options depending on when do you want it starts.

If it is right after you login, and no before, you can use 'Startup Applications'.

If you want it to start, when you turn on the computer, regardless of login, you can use either:
[LIST]
[*]/etc/rc.local, or
[*]crontab (using the special time keyword @reboot)
[/LIST]
In order to delay the process, you can use a script with a sleep command. For instance:
```
#!/bin/bash
/bin/sleep 30s
env DISPLAY=:0 /usr/bin/transmission-gtk

```
I recommend using crontab because interferes less with the booting process.

I hope that points you in the right direction. Let us know how it goes.
Regards.

Thanks for the reply papibe!

I have transmission already auto-starting I just want to add the delay to it. As stated, I am new to linux. I think i would like to create that script, just not sure how to do that, or where to put it after I create it. Could you give me any tips on that?

Thanks again,
Ken

---

### Post by CantankRus on 2016-06-10
Copy your .desktop file to the autostart directory.
```
cp /usr/share/applications/transmission-gtk.desktop ~/.config/autostart/
```

Open using your text editor...
```
leafpad ~/.config/autostart/transmission-gtk.desktop
```

and change the line....
```
Exec=transmission-gtk %U
```

to...
```
Exec=sh -c "sleep [COLOR="#FF0000"]30[/COLOR] && transmission-gtk"
```

...where [COLOR="#FF0000"]30[/COLOR] is your delay time in seconds.

You may need to remove the other methods you have used to autostart transmission.

---

### Post by ken55 on 2016-06-11
> **CantankRus said:**
> Copy your .desktop file to the autostart directory.
```
cp /usr/share/applications/transmission-gtk.desktop ~/.config/autostart/
```

Open using your text editor...
```
leafpad ~/.config/autostart/transmission-gtk.desktop
```

and change the line....
```
Exec=transmission-gtk %U
```

to...
```
Exec=sh -c "sleep [COLOR=#FF0000]30[/COLOR] && transmission-gtk"
```

...where [COLOR=#FF0000]30[/COLOR] is your delay time in seconds.

You may need to remove the other methods you have used to autostart transmission.

PERFECT!! Thanks SO Much, CantankRus!

Ken

---

