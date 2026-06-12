---
title: "Get rid of yellow &quot;help&quot; pop-ups?"
date: 2007-05-26
forum: General Help
---

### Post by kalle314 on 2007-05-26
When I came back to Ubuntu yesterday, there were yellow pop-ups telling me that "you can update your applications by clicking here" and stuff. How do I get rid of these permanently?

---

### Post by smoker on 2007-05-26
hi, i am not sure if this is what you mean, but if you right click on the notification area, (three vertical dots), then choose remove from panel, i believe that will stop any pop-up warnings.

---

### Post by kalle314 on 2007-05-26
This is what I mean:
[IMG]http://pici.se/pictures/cEhUSvkfS.png[/IMG]

If I rightclick on the pop-up, the pop-up just disappears, without showing any menu, and then it pop ups again if I log out and log in.

If I click on the notification area, and choose "remove from panel" that would remove the notification area, which I don't want to do.

---

### Post by hikaricore on 2007-05-26
I don't use gnome anymore, but if I recall correctly you can remove/disable the update-notifier program from your startup applications, which should be under Preferences/Sessions.  ^_^

---

### Post by kalle314 on 2007-05-26
Thanks,
but I have nothing against the update notifier program, just the annoying yellow box!
I also got some other lightbulb-decorated yellow box which was not associated with the update notifier.

---

### Post by smoker on 2007-05-26
> **hikaricore said:**
> I don't use gnome anymore, but if I recall correctly you can remove/disable the update-notifier program from your startup applications, which should be under Preferences/Sessions.  ^_^

ah, excellent, hikaricore, i never had sessions as an option on that menu, but enabled it now, and simple...

thanks:p

---

### Post by kalle314 on 2007-05-28
The origin of the yellow bubbles apperently is notification-daemon (/usr/lib/notification-daemon/notification-daemon), so one way might be to simply remove the notification-daemon package, but then other packages that I prefer to keep would be removed to.
notification-deamon has process #1 (init) as parent process, and I guess it should be possible to find some file where you can tell init not to start notification-daemon.
For now, I just went with an ugly solution:
```
sudo chmod -x /usr/lib/notification-daemon/notification-daemon
```
(I don't recommend ugly solutions like this, but at least I got rid of the yellow bubbles without spending more time on this issue.)

---

### Post by drs305 on 2007-05-28
> **kalle314 said:**
> I guess it should be possible to find some file where you can tell init not to start notification-daemon.
For now, I just went with an ugly solution:
```
sudo chmod -x /usr/lib/notification-daemon/notification-daemon
```
(I don't recommend ugly solutions like this, but at least I got rid of the yellow bubbles without spending more time on this issue.)

System, Prefs, Sessions, uncheck Update Notifier.  That should do what you want.

---

### Post by mbeierl on 2007-05-28
Umm.  I think he said he wants the update notifier, just not the popup.  When the white star/orange background icon is showing, right click on it and uncheck "Show notifications."  That should do it without chmodding any files...

---

### Post by drs305 on 2007-05-28
I agree that is what he was originally seeking, but in the text I quoted it appeared he was saying that he didn't want to "start the notification daemon". I think that is what unchecking the box would do although it would certainly do more than eliminate the yellow boxes.

---

### Post by kalle314 on 2007-05-28
Yes, I want to keep the update-notifier which is useful to me, but I dislike the yellow bubbles that pops up from it, and sometimes pops up from the lower right corner with notifications unrelated to updates.
There are two different daemons here:
The update-notifier-daemon, which looks for updates and puts the orange star icon in the notification area when there is anything,
and the notification-daemon, which is responsible for the yellow bubbles (this daemon is used by the update-notifier as well as other processes). 

The best solution would be if I could find a configuration file with the daemons that init starts, and remove notification-daemon, but this ugly solution works fine.

---

