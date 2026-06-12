---
title: "I accidentally deleted /tmp, now multiple programs are having issues"
date: 2015-09-12
forum: General Help
---

### Post by Nicholas_Alaniz on 2015-09-12
As the title said, I accidentally deleted my /tmp folder. I *thought* this was harmless, and simply created a new /tmp folder, but it seems to have consequences.

The first issue I encountered after the deletion/creation of the /tmp folder was my web browser (opera) would not start. It would give me an error saying that attempting to run opera as root will create another instance of opera instead of creating a new tab, or something similar. I cannot remember the exact error. The same thing happened with nautilus. I was able to run opera as root and correct this by running ```
sudo rm ~/.Xauthority
sudo touch ~/.Xauthority
``` (I searched the error codes I got and this was the solution that worked) however, I am not sure exactly what error codes I was getting because my history was not being saved for some reason. 

The issue now is that when I launch opera, I get a dialog box saying:
```
Your preferences files cannot be read.

Some features may be unavailable and changes to settings won't be saved.
```

I have a few other issues such as qjackctl giving errors:
```
[COLOR=#999999]14:13:02.621 Patchbay deactivated.[/COLOR][COLOR=#999999]14:13:02.623 Statistics reset.[/COLOR]
[COLOR=#cccc99]14:13:02.632 ALSA connection change.[/COLOR]
[COLOR=#999999]14:13:02.637 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]14:13:02.651 ALSA connection graph change.[/COLOR]
[COLOR=#999999]14:14:18.091 JACK is starting...[/COLOR]
[COLOR=#990099]14:14:18.091 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
/usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: clock_source
[COLOR=#999999]14:14:18.102 JACK was started with PID=5190.[/COLOR]
[COLOR=#999999]14:14:18.105 JACK was stopped[/COLOR]
[COLOR=#ff0000]14:14:20.277 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

Both of these issues started at the exact same same time, so I am led to believe they may have been caused by the removal of the /tmp folder or the deletion and touch of ~/.Xauthority. I have absolutely no clue how to fix this. If I need to make a separate thread for the Jack Audio errors please let me know.

---

### Post by jawilljr2 on 2015-09-12
You said you recreated the /tmp folder. The /tmp folder has to have the right permissions to work.

Try the command below:

```
sudo chmod 1777 /tmp
```

I would also reboot after that.

---

### Post by Nicholas_Alaniz on 2015-09-12
Okay, repaired the permissions and rebooted. Still the same errors. The only thing that changed is the qjackctl output:
```
16:59:25.427 Patchbay deactivated.
16:59:25.429 Statistics reset.
16:59:25.437 ALSA connection change.
16:59:25.695 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
16:59:25.704 ALSA connection graph change.

```

---

