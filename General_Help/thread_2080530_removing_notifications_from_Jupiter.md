---
title: "removing notifications from Jupiter"
date: 2012-11-04
forum: General Help
---

### Post by thorbs on 2012-11-04
I have installed Jupiter on my xubuntu. It works flawlessly but every time I open my computer it gives notifications about the screen. I would like to deactivate these if possible. Does any one know a way to do this?

---

### Post by thorbs on 2012-11-05
found a thread in askubuntu about this subject but no solution there either. 
[http://askubuntu.com/questions/207739/xfce-some-notifications-not-disappearing](http://askubuntu.com/questions/207739/xfce-some-notifications-not-disappearing)

---

### Post by thorbs on 2012-11-05
Got the answer from xubuntugeek

After some digging on Jupiter's code I found out that the problem isn't in Jupiter itself. Jupiter sends desktop notifications using the "notify-send" command. notify-send has the "-t" parameter which sets the timeout, if you don't use it the notification vanishes after a few seconds, however, if you do use it the notification lasts forever; it's a bug I guess.

So it's easy to fix Jupiter; just remove the -t parameter from each call. This command does just that:

sudo sed -i 's/-t [0-9]\+//g' /usr/lib/jupiter/scripts/notify

---

