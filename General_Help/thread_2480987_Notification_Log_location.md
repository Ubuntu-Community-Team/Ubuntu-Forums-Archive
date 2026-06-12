---
title: "Notification Log location?"
date: 2022-11-15
forum: General Help
---

### Post by cedardoc on 2022-11-15
I want to monitor the notifications that happen on my computer to trigger a script when a certain app makes notifications.  

The only way I can think of to do that is to monitor a notification log.  I've read older posts that say there was this file: **$HOME/.cache/notify-osd.log **but that doesn't exist on my system (the post was 9 years old so I suppose there's a different system now)

I also found reference to putting LOG=1 in your bashrc file, but that didn't work either.

What's the "modern" way to do this?  I also read about a python script but I can't find out how to include glib so those scripts fail too.


There's got to be a text file somewhere in the system that reflects the system notifications...


Thanks, 
- Dave
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy

---

### Post by &amp;KyT$0P# on 2022-11-15
Can you use [FONT=Courier New]dbus-monitor[/FONT] or similar?

For example, watching the output of the following command -
```
dbus-monitor 'type=method_call,interface=org.freedesktop.Notifications'
```

---

### Post by cedardoc on 2022-11-16
Ok, thanks for that.  Here's what I've got working:

> dbus-monitor 'type=method_call,interface=org.freedesktop.Notifications'| grep --line-buffered "Skype" > notif.txt

So theoretically I could monitor the folder that was in with inotifywait and trigger skype to pop up from there with a `wmctrl -a Skype`

Can you think of any way to make it do that directly on the original dbus line?

---

### Post by cedardoc on 2022-11-16
Here's what I have as a solution:

> dbus-monitor 'type=method_call,interface=org.freedesktop.Notifications'| grep --line-buffered "Skype" > /home/david/skypeMonitor/notif.txt &




while inotifywait -e modify /home/david/skypeMonitor/;
do


wmctrl -a Skype


done


so as long as there's only one window open somewhere with the word "Skype" in the title I now get Skype popping up if I get a new message :)
(runs from a startup script)

Let me know if there are any obvious improvements though please

---

