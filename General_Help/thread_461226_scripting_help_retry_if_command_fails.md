---
title: "scripting help: retry if command fails"
date: 2007-06-01
forum: General Help
---

### Post by dangling participle on 2007-06-01
hey y'all.

i've created a script to restart the mouse/keyboard sharing application "synergy".  i use cron to run this script every hour, because there is a known issue with the current version of synergy where the copy/paste function fails after a period of time, and the only known workaround is to restart the app.

the script works 50% of the time, other times, synergy does not start up.  running dmesg, i see this error message:

synergys[17128]: segfault at 0000000000000009 rip 00000000004424da rsp 00007fff305648b0 error 4

i wonder, first, does anyone know why this would be happening, and second, is there a way to make my script retry launching the application again if it fails to start? (kinda new to scripting).

here is the script i am using to restart synergy:

#!/bin/sh
/usr/bin/killall synergys
synergys --config synergy.conf

Thanks all!

---

