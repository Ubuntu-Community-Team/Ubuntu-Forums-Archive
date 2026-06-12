---
title: "Sending message to a user on another Ubuntu PC"
date: 2014-03-28
forum: General Help
---

### Post by hendry2 on 2014-03-28
Hi,

I want to be able to send message to a user on another Ubuntu PC. Does anyone know what command I can use to send message by which the message/activity is logged in system log. 
I found "notify-send" and "write" command but not sure if they are logged in the system log. Any clues about this ?

Thank you

---

### Post by GigabyteProduction on 2014-03-28
if by system log, you mean dmesg, well i just tested both of the commands, and neither of them write to dmesg, the notify-send command only does one of those bubbles in the ui's corner, and write does terminal only, and only 1 terminal at a time too, but i have figured out that you can write to dmesg on [http://serverfault.com/a/363042](http://serverfault.com/a/363042) so doing this will only write to dmesg: ```
sudo sh -c 'echo "message here" >> /dev/kmsg'
``` You will also need to be on the second machine through something like ssh, these commands aren't remote. Other than what i have given, i don't know what other commands to give.

---

