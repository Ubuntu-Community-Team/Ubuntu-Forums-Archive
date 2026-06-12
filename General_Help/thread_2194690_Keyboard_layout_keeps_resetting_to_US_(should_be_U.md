---
title: "Keyboard layout keeps resetting to US (should be UK)"
date: 2013-12-20
forum: General Help
---

### Post by WebDrake on 2013-12-20
Hello all,

I'm having a problem which seems to have hit various people on various occasions over the history of Ubuntu, but what I've read of previously-suggested solutions doesn't help me solve this.

The problem started while using 13.10 but has started to recur also with 14.04: on reboot and login, the keyboard layout will often be reset to US.

Going to System Settings > Text Entry shows only English (UK) in the list of input sources to use.  /etc/default/keyboard is as follows:
```
XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""

```

On the assumption it might be relevant, locale is as follows:
```

LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_GB.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME=en_GB.UTF-8
LC_ADDRESS=en_GB.UTF-8
LC_TELEPHONE=en_GB.UTF-8
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION=en_GB.UTF-8
LC_ALL=

```
I've tried using sudo dpkg-reconfigure keyboard-configuration and I've also tried sudo setxkbmap gb -- both of which seem to bring short-term relief, but the problem keeps recurring.

Can anyone suggest what might be the problem and how to fix it?

Thanks & best wishes,

    -- Joe

---

