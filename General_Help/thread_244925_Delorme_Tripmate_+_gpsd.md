---
title: "Delorme Tripmate + gpsd"
date: 2006-08-27
forum: General Help
---

### Post by amp_man on 2006-08-27
Can someone just tell me how to send a string, "ASTRAL" to be specific, to a serial port (/dev/ttyUSB0)? I need to use this to turn on my Delorme Tripmate so I can at least attempt to use it with gpsd, and sending strings to serial ports is something I've never dealt with before. I've tried "echo "ASTRAL" >> /dev/ttyUSB0", but that doesn't work (gpsdrive reports timeout recieving data). Thanks!


edit: The laws of forums strike again: I must have messed with this GPS for 2 months now, and it just happens to be that 30 seconds after posting I stumble accross the right combonation of settings. For anyone else with this GPS (HIGHLY doubtful, but there might be), use baud rate 4800 (gpsdrive defaults to 9600), and send the echo command above *after* loading gpsdrive. Also, don't use gpsd, use gpsdrive's built-in serial support, and don't use the garmin/earthmate settings.

another edit: correction: use a command like this:
$ echo "ASTRAL" >> /dev/ttyUSB0 && gpsdrive

The default action of the hardware in the Tripmate is to shut off after 10 seconds of inactivity, however, gpsdrive, if the tripmate isn't working when it starts or very shortly thereafter, won't attempt to probe it again. Why on earth did I never do this before? You can probably also make a small script and replace the simlink in /usr/bin for gpsdrive with it, I'll play with it more and maybe make a HOWTO, just in case anyone else ever gets one of these and wants to get it working under linux (if you have any doubts as to the usefulness of this, google "tripmate linux").

---

