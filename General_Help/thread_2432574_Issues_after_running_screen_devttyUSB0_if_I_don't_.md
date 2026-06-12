---
title: "Issues after running screen /dev/ttyUSB0 if I don't exit"
date: 2019-12-04
forum: General Help
---

### Post by jstickler on 2019-12-04
Hello,

I setup a new server (18.04.3 LTS) that is used as a serial console server for staging Cisco equipment.  Everything seems to work great, I added user accounts to the dialout group and I can ssh to the device and type "screen /dev/ttyUSB0" and gain access without issue.  If I exit my ssh window without doing a "ctrl-a & d" to exit screen I have to type "sudo screen /dev/ttyUSB0".  When I do this I get garbled output from the screen session:
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]SSwitch>
Switch>
Switch>
S
Swi>
Switch>
Switch>

I need to reboot in order to fix the issue.  However, if I exit screen properly doing ctrl-a & d there are no problems.

I am curious if there is a way to correct this, I can remember to log off, however others may not.

Thank you!
[/FONT]

---

