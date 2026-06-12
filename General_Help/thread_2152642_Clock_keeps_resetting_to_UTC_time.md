---
title: "Clock keeps resetting to UTC time"
date: 2013-06-08
forum: General Help
---

### Post by MichaelBKK on 2013-06-08
I recently traveled across several time zones and back with my notebook - something I do from time to time but this is the first time since installing 13.04. The clock seemed to work fine during the trip, but since returning, every time I wake up the computer or reboot it the clock resets to UTC time rather than my local time. I think I've tried every combination of settings for the digital clock and date/time but nothing seems to work. I've review all the documents I could find but haven't found anything to point at the problem or suggest settings I haven't already tried. It's amazing how annoying this is. Does anyone have any ideas on what the problem is?

---

### Post by Karlchen on 2013-06-08
Hello, MichaelBKK.

As I am not a KDE user, I cannot give a warranty that the steps will be exactly the same as on my system, yet there must be something on KDE which corresponds to "Date and Time" (configuration).
So here are my steps:
Go to [Menu] => Preferences => Date and Time. This will actually launch the commandline ```
gnome-control-center datetime
``` (Cannot tell what the equivalent command on KDE may be. Sorry)
Next I see a dialogue box like this (click thumbnail to enlarge):

[ATTACH=CONFIG]243658[/ATTACH]

In the dialogue box, I select my local region "Europe" and a city characterizing my timezone "Berlin".
Next I make sure that "network time synchronization" is switch [ON].
This is all.
By closing the dialogue the settings will be stored and used across reboots.
I have performed these steps only once. The system honours the settings and displays my local time, METDST.

Hope this helps a bit.
Karl

---

### Post by poitiers on 2013-06-24
Hi, I experience the same problem.

It may be related to something (the control module?) resetting /etc/localtime to point to, e.g. ../posix/Europe/Berlin

(while it should be pointing to /usr/share/zoneinfo/posix/Europe/Berlin)

---

### Post by poitiers on 2013-06-24
What I did to get out of this (and so far, it's working) was the following. (Let me stress: there is no advanced know-how in what I did, just guessing and wishful thinking, so some of these steps may seem funny to the experts here):

[LIST]
[*]purged ntp
[*]purged ntpdate (it looked to me like it installed differently with ntp present)
[*]installed ntpdate
[*]set UTC=yes in /etc/default/rcS
[*]rebooted
[*]sudo ln -f -s /usr/share/zoneinfo/Europe/Berlin /etc/localtime
[/LIST]

After the last step, the clock finally reset to my time zone. I will now keep away from the KDE system administration module for date&time, because I suspect that it may be responsible for the malformed /etc/localtime

HTH!

---

