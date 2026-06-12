---
title: "Screen Going With Sparks After Enabling Screen Recorder"
date: 2020-04-21
forum: General Help
---

### Post by th3c0wm1lk on 2020-04-21
Hello guys, I have some weird acting with my screen after trying to record my screen.

After some time while my laptop was in the repair shop for a spilled beer on it, I thought to do some programming content for my YouTube channel.

So since I knew Ubuntu had a built in screen recorder I thought to just try it once. I pressed the sequence keys to start it and I pressed the same sequance keys to stop it. But after I stopped it I noticed that my screen was flickering. I have searched on google for this issue but I couldn't find any post which could relate to me since others had different graphic card.

Here are some information which could help you guys:

cat /etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.4 LTS"

uname -a:
Linux root 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 vga:
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller [103c:17ab]
    Kernel driver in use: i915

env | grep DESK:
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

---

