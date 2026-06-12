---
title: "indicator-bluetooth why oh why?"
date: 2015-05-28
forum: General Help
---

### Post by sami-mattila on 2015-05-28
I have no need for Bluetooth service so I disabled the service.
Still the "indicator-bluetooth-service" keeps automatically starting no matter what.
So I decided to remove the offending "indicator".
But ofcourse it won't go without a fight.
Can some1 smarter please explain why we need to check that the indicator won't stay killed and/or be removed?

Sam

```

root@sam:/media/ramdisk# **apt remove indicator-bluetooth**
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following packages will be REMOVED:
  indicator-bluetooth ubuntu-desktop unity-control-center
  unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 5.191 kB disk space will be freed.

Do you want to continue? [Y/n]

```

---

### Post by mc4man on 2015-05-28
Just open System Settings > Bluetooth & turn off there inc. not showing in menu bar & then forget about it..

---

### Post by sami-mattila on 2015-05-28
Please answer the question I asked. I did not ask how to disable Bluetooth service since as I mentioned previously I allready "turned it off" as you put it.

---

### Post by ian-weisser on 2015-05-28
> **sami-mattila said:**
> [...]please explain why [...] the indicator won't [...] be removed?

It seems like you are asking "Why can't I remove *only* indicator-bluetooth"
If you are asking a different question, please rephrase it more clearly. Or break the large question into several smaller questions. The grammar you chose makes the question difficult to understand.

The short, perhaps unsatisfying answer is 'package dependencies.'

The longer, perhaps unsatisfying answer is that Ubuntu expects to support all hardware on your system, including Bluetooth. The System Settings control panel assumes the system has bluetooth support, so it's coded to *require* bluetooth-indicator to be present.

If you feel that Unity's dependency on indicator-bluetooth is unwise, please suggest a coding solution to remove the dependency in a bug report, or at  the next Ubuntu Online Summit (3-5 NOV 2015) and provide your feedback to developers.


> **sami-mattila said:**
> [...]please explain why [...] the indicator won't stay killed[...]?
mc4man told you the right way to avoid the whole problem.

Look at your /usr/share/upstart/sessions/indicator-bluetooth.conf
```
description "Indicator Bluetooth Backend"

start on indicator-services-start
stop on desktop-end or indicator-services-end

[COLOR=#ff0000][B]respawn
respawn limit 2 10[/B][/COLOR]

exec /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
```

See the 'respawn' instruction? That's why it killing it doesn't work. It automatically respawns.
To prevent indicator-bluetooth from starting at login, simply comment out the start line and/or the exec line.

---

### Post by sami-mattila on 2015-05-29
Thank you. You answered my question which was why (something happens).
Now if only we could find out why someone decided this was a good idea?
Would it not make more sense if the Bluetooth indicator was dependent on Bluetooth?
I'm just wondering why I should have active indicator for Bluetooth if the service itself is disabled.
Maybe all that is needed is to rename the indicator (if infact it is indicating something elese other than Bluetooth?)

---

### Post by Mike_Walsh on 2015-05-29
As far as I'm aware, the Bluetooth indicator IS dependent on Bluetooth being present.

I run two elderly systems on various 'buntu-based distros, neither of which had Bluetooth in them when new. To get around this, I purchased a pair of cheap Bluetooth dongles for which I think I paid the grand total of £2.50 ($3.50?$3.75?)

When the dongles are plugged in, the Bluetooth indicators are present. When I remove them.....they are not.

I think if your system has Bluetooth integrated into the hardware, then mc4man's suggestion is the best way to get rid of the offending icon, as far as day-to-day use is concerned....**.if** it bothers you that much.


Regards,

Mike.

---

### Post by ian-weisser on 2015-05-29
> **sami-mattila said:**
> Now if only we could find out why someone decided this was a good idea?
That's not constructive.

> **sami-mattila said:**
> I'm just wondering why I should have active indicator for Bluetooth if the service itself is disabled.
Your shouldn't. If you do, that's a bug.
indicator-bluetooth bugs are at [https://bugs.launchpad.net/ubuntu/+source/indicator-bluetooth/](https://bugs.launchpad.net/ubuntu/+source/indicator-bluetooth/)

If somebody has reported the bug already, please click the 'affects me too' link on Launchpad, and help provide information and test solutions. 
If nobody has bothered to report the bug, then please report it with enough detail for a Triager to reproduce the problem. A bug that cannot be reproduced on the Triager's system will usually be ignored.

---

