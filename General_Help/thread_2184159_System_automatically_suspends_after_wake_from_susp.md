---
title: "System automatically suspends after wake from suspend"
date: 2013-10-27
forum: General Help
---

### Post by marcinkowski on 2013-10-27
I posted this question here ([http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend](http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend)), but thought I'd post it to the forum as well.

After updating from 13.04 to 13.10, about 50% of the time on waking from suspend, the screen flashes black, then offers a login screen, then falls back into suspend. This cycle repeats on each subsequent resume, and seems to only be resolved by a reboot. The issue never occurs on boot. 

Please let me know if it would be helpful to post any other information. Thanks.

EDIT: This seems to be reported as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1243647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1243647)

---

### Post by Toz on 2013-10-27
How do you suspend? Lid closure? Do you get the same double-suspend if you run suspend from the menu or manually via:
```

sudo pm-suspend
```
...without closing the lid?

---

### Post by marcinkowski on 2013-10-27
Problem only occurs when closing lid to suspend and seems to only manifest on the second suspend-wake of the session. Both menu and manually seem to work fine. Though when running sudo pm-suspend system does not ask for login on wake, just waking to desktop.

---

### Post by Toz on 2013-10-28
I run Xubuntu 13.10 and noticed the same thing. I also run Arch linux on another laptop where I noticed the same double-suspend issue on lid closure. In Arch, they have fully transitioned to systemd and I found an inconsistency between the Xfce power manager and systemd. I was able to fix the issue in Arch by disabling the systemd functionality that monitors and acts upon lid closure. So I tried the same thing in Xubuntu and it worked. Looks like there is more of systemd in Xubuntu 13.10 than in previous versions. The fix that worked for me was to change, in the file **/etc/systemd/logind.conf** the line that reads:
> #HandleLidSwitch=suspend
...(the default action) to read:
```
HandleLidSwitch=ignore
```
...and reboot.

Perhaps you can give it a try on Ubuntu and see if it works?

---

### Post by marcinkowski on 2013-10-28
I made the change and rebooted, but now closing the lid does not suspend the system. It still wakes the system if it is suspended from the menu or manually. So the change eliminates the problem of the suspend loop :P , but avoids it by disabling the ability to suspend by shutting the lid :( .

It looks like the problem only occurs the second suspend after reboot. The first seems to go fine.

---

### Post by Toz on 2013-10-28
It looks like it might only work for Xubuntu (Xfce). When I disable the systemd lid handling, I can still enable lid handling with the Xfce power manager. I just put together a VM of Ubuntu 13.10 (Unity) and I see that there are no other options to handle lid events if you disable the systemd method. The other option, which _might_ work with the disabled systemd lid handling, is to create your own [lid handling events]("https://help.ubuntu.com/community/LaptopLidAndDockScripts"), but at some point, the workaround becomes so cumbersome that perhaps its better just to wait for a bug fix.

Another reason why you might be suspending twice, is that the system is receiving 2 lid closed events with every lid close. On my system, I have the file /proc/acpi/button/lid/LID/state which contains the current state of my lid. See if you have the same (or similar) file. If so, you could run, in a terminal window:
```
 while true; do cat /proc/acpi/button/lid/LID/state ; sleep 1; done
```
...and it will print out the state of the lid every second. Then close the lid, wait a few seconds and open it. See if you have any interrupted "state: closed" events. By interrupted, I mean:
> state:      open
state:      open
state:      closed
state:      closed
state:      closed
state:      closed
state:      open
state:      open
state:      open
state:      closed
state:      closed

...or something like that (note - two sets of closed events).

---

### Post by marcinkowski on 2013-10-28
Thanks for all your efforts in helping to resolve this, Toz.

Yes, creating custom lid handling events seems like it might work, though as you point out, it is a messy solution.

I was able to check the lid events, and everything appeared normal. When the lid was closed, it reported "closed," and when open it reported "open," with no stray events.

I tried setting the **/etc/systemd/logind.conf **line to 

[COLOR=#000000][I]HandleLidSwitch=suspend
[/I][/COLOR]
and the bad lid behavior returned, but when an external (svga) display is plugged in, shutting the lid still initiated suspend, and opening it still initiated resume, but on the second suspend after boot, instead of getting in a suspend loop, the screen just went black, and offered a lock screen on the external display (instead of on the laptop display as in the first boot). It did this twice (once after entering the password), but did not fall back into suspend. This cycle did, however, turn off networking that could be restored with:

sudo nmcli nm sleep false

(I had previously experienced the network-suspend trouble whose fix is described here [http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153) )

Additionally, each time this problem occurs (both in the single display and in the (less-severe) multiple display set ups), the Unity HUD menu command box (as when pressing alt) is displayed.

---

### Post by josephellengar2 on 2013-10-28
Toz- perhaps you could help me. I am trying to create a custom lid close event that calls pm-suspend instead of whatever it is calling right now. You can see more at this thread: [http://ubuntuforums.org/showthread.php?t=2184296](http://ubuntuforums.org/showthread.php?t=2184296) but briefly I have this in acpi/events:

```

# /etc/acpi/events/laptop-lid-close
# This is called when the user closes the laptop lid and calls
# pm-suspend so wireless will work

event=button/lid
action=/etc/acpi/lidclose.sh

```

And it calls this:

```

#!/bin/sh

pm-suspend &

```

You seem to know what you're talking about with acpi. Is there any reason why this wouldn't call the pm-suspend instead of the other version of suspend? One suspend works and the other needs to be restarted completely after resume.

---

### Post by Toz on 2013-10-29
> **josephellengar2 said:**
> Toz- perhaps you could help me. I am trying to create a custom lid close event that calls pm-suspend instead of whatever it is calling right now. You can see more at this thread: [http://ubuntuforums.org/showthread.php?t=2184296](http://ubuntuforums.org/showthread.php?t=2184296) but briefly I have this in acpi/events:

```

# /etc/acpi/events/laptop-lid-close
# This is called when the user closes the laptop lid and calls
# pm-suspend so wireless will work

event=button/lid
action=/etc/acpi/lidclose.sh

```

And it calls this:

```

#!/bin/sh

pm-suspend &

```

You seem to know what you're talking about with acpi. Is there any reason why this wouldn't call the pm-suspend instead of the other version of suspend? One suspend works and the other needs to be restarted completely after resume.
I've posted in your thread.

---

### Post by pimmesselink on 2013-11-12
Just a quick post to say I have the same issue of the suspend loop. Did you file a bug report?

---

