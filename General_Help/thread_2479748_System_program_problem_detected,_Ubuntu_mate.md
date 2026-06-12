---
title: "System program problem detected, Ubuntu mate"
date: 2022-10-05
forum: General Help
---

### Post by adrian-h on 2022-10-05
I am at a bit of a loss on where to start or what I may have done to cause this issue.

This is on an elderly HP thin client a T510 that I have pushed into service basically to leave on all day as the power requirements are very low.

It did have an issue with the display not recognising the monitor or giving me the correct resolution.  After searching for hours on the net, I managed to solve with :-
sudo apt install xserver-xorg-video-openchrome

This to install the chrome drivers to work with the VX900 integrated chip.

I also did a update and upgrade where a few files were updated zlib1g-dev:amd64 and zlib1g:amd64.   Not sure what these do, or if it matters.

I have had a look at the log files and here is a copy of the apport.log

ERROR: apport (pid 1584) Wed Oct  5 13:41:19 2022: called for pid 761, signal 11, core limit 0, dump mode 2
ERROR: apport (pid 1584) Wed Oct  5 13:41:19 2022: not creating core for pid with dump mode of 2
ERROR: apport (pid 1584) Wed Oct  5 13:41:19 2022: executable: /usr/sbin/lightdm (command line "lightdm --session-child 13 16")
ERROR: apport (pid 1584) Wed Oct  5 13:41:20 2022: wrote report /var/crash/_usr_sbin_lightdm.0.crash

I have clicked the report button, but would like to find out more on what the issue is and if something I have now got wrong?

Adrian

---

### Post by adrian-h on 2022-10-05
A bit of an update, as I said I had clicked the report button so the errors should have been reported back, following another thread in the Ubuntu mate community I deleted the files in /var/crash and rebooted the PC.  The system error has not returned and the previous logs relate to a time of 13:41:1 and as it is now past 15:00 and the PC is no longer showing an error on reboot I am guessing I no longer have a system error?

Adrian

---

