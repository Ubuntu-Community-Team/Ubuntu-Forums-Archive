---
title: "how to autorun scripts on boot/startup"
date: 2018-03-09
forum: General Help
---

### Post by delfiler on 2018-03-09
so i have this script for my firewall that uses iptables but i noticed after a reboot that the settings for the firewall didn't stick so now i need to know how to run the script, which i wrote, automatically on startup/boot the file it self is located in etc so the path would be like this; /etc/<firewall iptables script> so my question is how do i do this cause i have been searching for a little while

---

### Post by yancek on 2018-03-09
Have you tried the suggestions at the Ubuntu site below?

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

---

### Post by SeijiSensei on 2018-03-09
Edit the file /etc/rc.local as root with sudo and add a line to run the script there.  You don't need to prefix sudo to the command because rc.local is run with root privileges each time the machine is booted.

---

### Post by papibe on 2018-03-09
Hi delfiler.

I'd go with a more standard procedure for persistent iptables: [https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables)

Regards.

---

### Post by delfiler on 2018-03-12
thanks for all the replies and seijisensei's methode worked like a charm
[COLOR=#DD4814][COLOR=#DD4814][[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] se[/COLOR][COLOR=#000000][SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")[/COLOR][/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000][SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]

---

