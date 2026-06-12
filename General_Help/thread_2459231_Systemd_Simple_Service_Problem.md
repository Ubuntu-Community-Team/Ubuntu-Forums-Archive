---
title: "Systemd Simple Service Problem"
date: 2021-03-13
forum: General Help
---

### Post by jb555 on 2021-03-13
See the pics. I have created a dead simple service to send a one liner notification to the screen. The service completes but i get no notification. I have tried all the environment variables that have been commented out. All 4 of the environment variables were verified to be present in the test3.sh file when executed from the service. The EnvironmentFile is a dump from my main user account using the command "env>>env.txt". I'm clueless at this point. What little info i found on the internet has not worked. Also, it may be of help to know that i can echo to the syslog at the end of the test notification bash file. This is further validation that the file makes it all the way through but the notify-send command still does not display. Also, echo $? right after the notify send command shows a zero so the command has returned not in error but i still get no notification. I dont know at this point. Any help would be appreciated. Thanks Also, the notify script runs just fine outside of a service. I get the notification.
[ATTACH=CONFIG]288106[/ATTACH]

---

### Post by ActionParsnip on 2021-03-14
Try using the absolute path to the binary. You may need to specify the DISPLAY variable too so it goes to your screen

---

