---
title: "Ubuntu 10.04 add ssh service to autorun config"
date: 2014-06-18
forum: General Help
---

### Post by Ervin1989 on 2014-06-18
Hello everyone.

I have  a VPS with ubuntu 10.04 OS.
After reboot  VPS  i can't access  it via putty. I wrote an mail to VPS administrators with this problem, and they said the following:

"[COLOR=#333333]we have started SSH service for you. You must put SSH service into Autorun confi of your OS to start it at reboot. For this please take info of the developers pages or forums of your OS.[/COLOR]" 

I have no idea how can i put ssh service into autorun config.

---

### Post by 3v3rgr33n on 2014-06-18
There is no autorun in Ubuntu, that is a Windows feature as far as I understand.

If they've given you a "SSH service", it seems to me that you then need to to ssh in.
This thread: [http://ubuntuforums.org/showthread.php?t=1820405](http://ubuntuforums.org/showthread.php?t=1820405) might help.

---

### Post by steeldriver on 2014-06-18
What SSH server are you running? AFAIK even in 10.04, the default installation of openssh-server should start on boot automatically using upstart. Is there an /etc/init/ssh.conf file?

---

