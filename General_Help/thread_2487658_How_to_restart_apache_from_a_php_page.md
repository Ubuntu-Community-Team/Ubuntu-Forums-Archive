---
title: "How to restart apache from a php page?"
date: 2023-06-11
forum: General Help
---

### Post by josephchrzempiec on 2023-06-11
Hello, I have been searching online to restart apache through php. Only thing I can find is restarting apache from command line. Is  there a way to do that?

Joseph

---

### Post by aikoo7 on 2023-06-11
Apart from the terminal, the other solution I known is the apache switch, a guide here: [https://www.ubuntugeek.com/apache-switch-gui-application-to-startstop-and-restart-apache-server.html](https://www.ubuntugeek.com/apache-switch-gui-application-to-startstop-and-restart-apache-server.html)

Keep me updated if need anything more and welcome to the Ubuntu/the forum if you are new to any and be free to ask me anything.

Regards,
Aiko.

---

### Post by Holger_Gehrke on 2023-06-11
[Apache will restart]("https://httpd.apache.org/docs/current/en/stopping.html") when it receives a USR1 signal. So if you use the [posix_kill()]("https://www.php.net/manual/de/function.posix-kill.php") function to send a USR1 signal to the main apache process (you can get its pid from the pid file it creates) it should restart.

Holger

---

