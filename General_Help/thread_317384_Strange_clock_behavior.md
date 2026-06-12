---
title: "Strange clock behavior"
date: 2006-12-12
forum: General Help
---

### Post by gcampos on 2006-12-12
Hello

I have some problems with the clock moving slowly and backwards.

I have followed some of the threads regarding the clock were setting UTC to no in the /etc/default/rcS, restarting hwclock.sh, rebooting, enabling/disabling automatic clock sync.

Here is an example of the output, check the red timestamp compared with the previous line

Last login: Sun Dec 10 02:17:44 2006 from x.x.x.x
$ date
Sun Dec 10 03:32:25 CST 2006
$ date
[COLOR="Red"]Sun Dec 10 03:32:24 CST 2006[/COLOR]
$ date
Sun Dec 10 03:32:24 CST 2006
$ date
Sun Dec 10 03:32:26 CST 2006
$ date
Sun Dec 10 03:32:31 CST 2006
$ date
Sun Dec 10 03:32:35 CST 2006
$ date
Sun Dec 10 03:32:35 CST 2006
$ date
Sun Dec 10 03:32:38 CST 2006
$ date
[COLOR="red"]Sun Dec 10 03:32:35 CST 2006[/COLOR]

Thanks in advance for your reply that you may provide

---

### Post by ajgreeny on 2006-12-12
Are you now set to sync your clock to an ntp site?  If so that will explain why it sometimes jumps back a second or two.  Your computer clock may run slightly faster than real time.

---

### Post by gcampos on 2006-12-12
Thanks, currently the clock is not set to ntp.

Also, reading other posts  with other clock problems, this is not a single system and have 6.10 Edgy installed as a desktop

---

### Post by gcampos on 2006-12-14
OK, I have changed the Time Zone settings from  Americas/Mexico City to Americas/Chicago,  and now the clock seems to be behaving correctly.

Has anyone has experienced problems with some other exotic Time Zone settings?

---

