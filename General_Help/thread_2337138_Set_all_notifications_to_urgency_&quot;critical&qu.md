---
title: "Set all notifications to urgency &quot;critical&quot;?"
date: 2016-09-15
forum: General Help
---

### Post by Roasted on 2016-09-15
Hi friends. Something that I only recently discovered was how the notifications truly work in Ubuntu. It seems as if they work pending no videos are running. If you are in YouTube, Vimeo, or playing a local video, notifications of the "normal" urgency simply don't show, while notifications of the "critical" urgency will. While I can see why there might be some logic here, it does get frustrating if you work with media playing on a 2nd monitor. I often let stand up comedy, a live concert, etc play on a second monitor while I work on the primary. This logic is anything but in those circumstances.

This can be tested by running these commands in terminal while playing a video to compare the results:
notify-send -u normal "test notification"
notify-send -u critical "test notification"

In an effort to combat that, I got to wondering if there was a way to simply set all notifications to a different urgency. Is that somehow possible to globally set all notifications to trigger as critical instead of normal? Or would that require a massive amount of voodoo to accomplish?

---

### Post by ian-weisser on 2016-09-15
I suspect it would require a rather large amount of voodoo to do safely.
Notification priorities come from the sending application, not the notification system. Overriding those priorities means second-guessing the notification's intent...which is generally unwise for several reasons.

Seems like an already-reported issue:
[https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/24070](https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/24070)
[https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/690845](https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/690845)
[https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/1081250](https://bugs.launchpad.net/ubuntu/+source/libnotify/+bug/1081250)

Strange little bugs like these are ideal for an affected user to move forward by Triaging. Developers don't usually fix un-triaged bugs.

---

### Post by CantankRus on 2016-09-15
Perhaps try the notification daemon for Xfce, xfce4-notifyd.
I use this in unity because notifications flagged as critical remain until clicked on.
Notifications seem to always be shown here critical or normal.

Just install **xfce4-notifyd** and it should take over from the default **notify-osd** after a logout.
If not remove **notify-osd**.

You can configure xfce4-notifyd with...
```
xfce4-notifyd-config
```

---

### Post by Roasted on 2016-09-15
> **CantankRus said:**
> Perhaps try the notification daemon for Xfce, xfce4-notifyd.
I use this in unity because notifications flagged as critical remain until clicked on.


They don't appear to remain there until clicked on -- at least from where I'm testing. If I run:

```
notify-send -u critical "testing"
```

in terminal, I get a notification popup. It remains there for 10 seconds and disappears without the need to click on it, much like when a "normal" notification pops up. The difference between the two is when they activate. Critical notifications will show during a video playing, whereas normal notifications won't.

Truth be told, I actually quite admire the way Ubuntu notifications are built, in that there are different levels and the different levels dictate when notifications appear based on current activities. As mentioned, the two-monitor-users-of-the-world such as myself (at least when I'm on my desktop) would likely agree that the behavior is frustrating. The frustration isn't so much "oh I missed a notification", but moreso "oh crap I have NO idea what notifications I missed in that time frame." I think Ubuntu could take a lesson from elementary Loki. Notifications show *all* the time without question, but with a quick toggle you can activate the "do not disturb" feature. Even with DND activated, it keeps a log in the notification history, so the notifications aren't ever "gone". On that note, a history of notifications would be incredible. It seems as if there's a PPA for that. 

[https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications](https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications)

Simple, does the job, and has been around for a long time. I've seen tech posts from 2011 with this linked, yet somehow I didn't think of it until someone linked to it in an AskUbuntu response. Maybe I'll give this a shot and cross my fingers it gets integrated by default someday. ;)

---

### Post by ian-weisser on 2016-09-15
By default is unlikely. Non-critical notification are, by definition, not critical for the user to miss (Oh, look, two unread e-mails).
The current notification system was the result of a *lot* of developer discussion (and argument). I doubt they want to re-open that can of worms anytime soon.
Happily, jconti continues to support his PPA for all current releases of Ubuntu.

Applications with non-critical notifications can also highlight themselves in the Shortcut Bar...or send you an e-mail, or notify you other ways.
And, of course, if you feel that an application's notifications should be upgraded or downgraded under certain specific conditions, please feel free to raise the issue with the project's through their forum or bug tracker.

---

### Post by Roasted on 2016-09-15
> **ian-weisser said:**
> By default is unlikely. Non-critical notification are, by definition, not critical for the user to miss (Oh, look, two unread e-mails).
The current notification system was the result of a *lot* of developer discussion (and argument). I doubt they want to re-open that can of worms anytime soon.
Happily, jconti continues to support his PPA for all current releases of Ubuntu.

Applications with non-critical notifications can also highlight themselves in the Shortcut Bar...or send you an e-mail, or notify you other ways.
And, of course, if you feel that an application's notifications should be upgraded or downgraded under certain specific conditions, please feel free to raise the issue with the project's through their forum or bug tracker.

I understand. It's a shame to hear about the "discussions", though. I may end up submitting something but if the discussion was as at-length as you mention I can see it going no where. It's a shame too, as the notification system feels like it's a 90% completed job. Almost there... little bit more and it'd be SO much better... but with those missing key points (do not disturb, a history of notifications, etc) really are, do I dare say, -u critical. ;) 

P.S. - one downside to the PPA I noticed is it logs each level of the sound change. For example, if I scroll over the volume icon to change the level, that may instigate 20, 30, 100 notifications in the list on the drop down. For kicks I scrolled up and down on my mouse wheel while hovering over the sound icon a few times. When I clicked, it had 1,800 notifications. Heh... Given there's no scrollability for those notifications, it can make it a bit cumbersome. I'll get a write-up submitted to Ubuntu, but in the mean time, I think it might be time to give Loki a serious test drive... 

Thanks for the insight everyone!

---

### Post by Roasted on 2016-09-15
For what it's worth, I submitted a "bug" (more of a feature request) regarding this issue. It can be found at:

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1624181](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/1624181)

---

