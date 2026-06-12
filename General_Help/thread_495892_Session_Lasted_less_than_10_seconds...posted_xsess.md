---
title: "Session Lasted less than 10 seconds...posted xsession error"
date: 2007-07-08
forum: General Help
---

### Post by mooter on 2007-07-08
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jasn"
/etc/gdm/Xsession: Beginning session setup...
/home/jasn/.profile: 1: [bench]: not found
/home/jasn/.profile: 2: as_____plugin_enabled: not found
/home/jasn/.profile: 3: cannot open Super: No such file
/home/jasn/.profile: 3: as_initiate: not found
/home/jasn/.profile: 4: as_disable_limiter: not found
/home/jasn/.profile: 5: as_output_screen: not found
/home/jasn/.profile: 6: as_position_x: not found
/home/jasn/.profile: 7: as_position_y: not found
/home/jasn/.profile: 8: as_output_console: not found
/home/jasn/.profile: 9: as_console_update_time: not found
/home/jasn/.profile: 11: [fs]: not found
/home/jasn/.profile: 12: as_____plugin_enabled: not found
/home/jasn/.profile: 13: as_mount_point: not found
/home/jasn/.profile: 15: [wall]: not found
/home/jasn/.profile: 16: as_____plugin_enabled: not found
/home/jasn/.profile: 17: as_show_switcher: not found
/home/jasn/.profile: 18: as_miniscreen: not found
/home/jasn/.profile: 19: as_allow_wraparound: not found
/home/jasn/.profile: 20: Syntax error: redirection unexpected

I searched for this problem but this ones different.
I'm hoping it isn't as bad as others might be.
I loaded up the game xmoto and I just got a blank white screen with the music and I couldn't get out of it so I hit Alt-F2.
I tried to find it in killall but wasn't sure which one it was, so I just tried "restartx"
then it said it was already loaded and to try something like
try "remove /tmp/ X0...."
I typed that but it said file not found.
I rebooted and got the session lasted less than ten seconds.
I have plenty of space left...
Any ideas?

---

