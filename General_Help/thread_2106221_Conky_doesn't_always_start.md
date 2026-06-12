---
title: "Conky doesn't always start"
date: 2013-01-18
forum: General Help
---

### Post by Kopkins on 2013-01-18
So, no matter which conkyrc I use, if I try to start it from a startup script it usually doesn't run. If I just put the conky command into startup apps the desktop manager starts after and conky is behind it, so I have to killall conky && conky anyway. 

For whatever reason some of my startup apps don't do well in the default ubuntu startup apps. So, I wrote a very simple script hoping to solve my issue.

```
#!/bin/bash

gnome-terminal -e conky

gnome-terminal -e thunderbird

exit
```This script will run and thunderbird will open. A terminal window will flash for conky, but then closes before it completes. The only way I can start conky is by using ONLY the conky command. 

Also, I would rather not have open terminals for all the apps I start with this method. Is there another command I can use to run them in the background? Just as another system process, or have the terminal close after the program is open?

Any help is appreciated.

Thank you, 

Kopkins

---

### Post by dannyboy79 on 2013-01-18
most times you need to add a sleep command in your conky startup script. google conky start up script and you'll see them with a sleep 10 or what have you prior to conky launching

as far as thunderbird launching upon startup, use gnome session manager and have all the apps open that you want open upon a new session and click on save session and then the checkbox that says, remember session upon restart or something like that.

---

### Post by Kopkins on 2013-01-18
I know, even with the sleep sometimes conky just doesn't start. I had sleep 30; conky for the startup, but it seems like the command just sleeps forever. Conky rarely starts via startup apps.

I'll have to look at gnome session manager.

Thank you,
Kopkins

---

### Post by ajgreeny on 2013-01-18
You don't need a script to delay conky's startup; simply use ```
conky -p 10
``` as the command to pause it by 10 seconds, or change the figure for shorter or longer pause time.

For applications that do not have the helpful -p option (pause) you can use a compound command in the startup applications box, as an example I use
```
bash -c "sleep 10; gmail-notify"
```Note: you must use the quotation marks " " in the command or it will fail.

---

### Post by Petro Dawg on 2013-01-18
> **Kopkins said:**
> I know, even with the sleep sometimes conky just doesn't start. I had sleep 30; conky for the startup, but it seems like the command just sleeps forever. Conky rarely starts via startup apps.

I'll have to look at gnome session manager.

Thank you,
Kopkins


I found on my system I needed a 60 second sleep to ensure start up every time.

Create a seperate conky-startup.sh file, enable it to be executable, and use the "start up applications" program to have the .sh file run at start up.

My conky-startup.sh looks like this...
```
#!/bin/bash 
sleep 60 && conky
```and it works for me, and no terminal window opens.  Not 100% sure if it will work the same in the GNOME environment however.

---

