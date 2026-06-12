---
title: "Cursor Disappears After Waking"
date: 2019-01-02
forum: General Help
---

### Post by Daveski17 on 2019-01-02
Hello,

After the last update I noticed that the cursor will often disappear when my laptop (Lenovo G500) is brought out of sleep mode. 

I’ve been running Ubuntu 16.04 LTS since Boxing Day. I can fix this with a reboot but it is annoying.

Apparently this is a known bug, although I never experienced it on 14.04. Is there a fix?

Thanks.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]Daveski17[/COLOR]**]("https://ubuntuforums.org/member.php?u=789821"),

Can you please run the following commands in Terminal and advise if this has helped resolve your issue:

1. cd /lib/systemd/system-sleep
2. sudo nano mousefix
3. Insert the following then save the changes:
```
#!/bin/bash
if [ "$1" = "post" ]; then
    modprobe -r psmouse
    modprobe psmouse
fi;
exit 0
```
4. sudo chmod +x mousefix

---

### Post by Daveski17 on 2019-01-03
OK thanks for the info. Is this an official fix? Everything was fine until the last update. I haven't had an update since. I've also discovered that this behaviour is sporadic and doesn't happen every time I take the laptop out of sleep.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]Daveski17[/COLOR]**]("https://ubuntuforums.org/member.php?u=789821"),

This fix and its derivatives can be found on multiple pages over the Internet and it is possible that the issue was fixed in a newer revision of the Linux kernel (you could try updating it and see if this resolves your issue before applying the fix I provided above).

You can also see that this issue is not new, as per a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/980469") filed in April 2012.

---

### Post by Daveski17 on 2019-01-03
> **clementc said:**
> Hi [**[COLOR=#000000]Daveski17[/COLOR]**]("https://ubuntuforums.org/member.php?u=789821"),

This fix and its derivatives can be found on multiple pages over the Internet and it is possible that the issue was fixed in a newer revision of the Linux kernel (you could try updating it and see if this resolves your issue before applying the fix I provided above).

You can also see that this issue is not new, as per a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/980469") filed in April 2012.

OK thanks. I'm not getting the bug now, even though I've tried to replicate it. I still haven't had any updates.

---

### Post by Impavidus on 2019-01-03
That bug report says it's a bug in kernel 3.2 and it seems fixed in 3.4. According to OP the problem wasn't present in Ubuntu 14.04, using kernel 3.13, and shouldn't be present in Ubuntu 16.04, using kernel 4.4, either. However, this isn't the only bug with a disappearing cursor. There's one mentioned in the [release notes of Xubuntu 16.04](https://xubuntu.org/news/xubuntu-16-04-release/). But that one was fixed in 9-2016.

Is this an upgrade from 14.04 or a fresh install of 16.04? And in the latter case, have you installed all updates?

---

### Post by The Cog on 2019-01-03
If it reappears, you might have luck switching to console mode and back with Ctrl-Alt-F1 then Alt-F7. I vaguely remember that working for me some time ago.

---

### Post by Daveski17 on 2019-01-03
> **Impavidus said:**
> That bug report says it's a bug in kernel 3.2 and it seems fixed in 3.4. According to OP the problem wasn't present in Ubuntu 14.04, using kernel 3.13, and shouldn't be present in Ubuntu 16.04, using kernel 4.4, either. However, this isn't the only bug with a disappearing cursor. There's one mentioned in the [release notes of Xubuntu 16.04](https://xubuntu.org/news/xubuntu-16-04-release/). But that one was fixed in 9-2016.

Is this an upgrade from 14.04 or a fresh install of 16.04? And in the latter case, have you installed all updates?

It was an upgrade on Boxing Day (Dec 26th) from 14.04 LTS. According to the updater I'm up to date.

---

### Post by Daveski17 on 2019-01-03
> **The Cog said:**
> If it reappears, you might have luck switching to console mode and back with Ctrl-Alt-F1 then Alt-F7. I vaguely remember that working for me some time ago.

Yeah, I tried that thanks and it didn't work. Well, I may have done it right. I'm disabled and can only effectively use one hand to use a keyboard. Lenovo keyboards aren't always one hand user friendly lol. I also read one fix was just to tap the space bar. I have wanted to test this but now every time I put the computer into sleep mode it awakens with a visible cursor. :confused:

---

