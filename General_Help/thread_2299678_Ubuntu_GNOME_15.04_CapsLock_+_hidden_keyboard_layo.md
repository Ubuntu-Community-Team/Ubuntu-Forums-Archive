---
title: "Ubuntu GNOME 15.04 CapsLock + hidden keyboard layout"
date: 2015-10-20
forum: General Help
---

### Post by paxapy on 2015-10-20
I have a problem with switching between two keyboard layouts by CapsLock 
Most intresting, that there is no problem with switching by Super+Space
I have two layouts: English (Colemak) and Russian in keyboard settings
But when I use CapsLock, there third English (qwerty) layout comes out, and then it's toggling with russian with no colemak, like this (after each space capslock pressed):
```
qwfpgj qwerty &#1081;&#1094;&#1091;&#1082;&#1077;&#1085; qwerty &#1081;&#1094;&#1091;&#1082;&#1077;&#1085; qwerty
```

I feel, that there can be a mess with local configs from previous ubuntu installation (14.04), where I've suffered from another related bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1246272](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1246272)
I've tried all the suggested there methods with no luck
My keyboard settings:
[IMG]http://i.imgur.com/rjrc5Xd.png[/IMG]
[IMG]http://i.imgur.com/LhASdxM.png[/IMG]
[IMG]http://i.imgur.com/b8Ol0M7.png[/IMG]
```

paxapy@pahost:~$ cat /etc/default/keyboard XKBLAYOUT=us,ru
BACKSPACE=guess
XKBVARIANT=colemak,

paxapy@pahost:~$ cat /etc/default/im-config 
# Default im-config mode (see im-config(8))


# Always start best input method
IM_CONFIG_DEFAULT_MODE=auto
# Start best input method only if CJKV environment
#IM_CONFIG_DEFAULT_MODE=cjkv


# Set locale dependent preferred IM over standard auto mode
IM_CONFIG_PREFERRED_RULE="zh_CN,fcitx:zh_TW,fcitx:zh_HK,fcitx:zh_SG,fcitx"


# User and system wide configuration is normally done via im-config program.
# The above IM_CONFIG_PREFERRED_RULE sets locale dependent preferred IM
# override rule.  If you wish to use uim over ibus just for ja_JP,
# add :ja_JP,uim at the end of the above list.


# Trace commands for debug
# (This may cause problem configuration file generated under console mode)
#IM_CONFIG_SETMODE="-x"


# Verbose output for debug (uncomment following)
#IM_CONFIG_VERBOSE="true"

```

I think there is should be a way to fix it, but I can't find it by myself

---

