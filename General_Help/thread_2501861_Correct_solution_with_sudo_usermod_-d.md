---
title: "Correct solution with sudo usermod -d ?"
date: 2024-10-23
forum: General Help
---

### Post by meteoensevilla on 2024-10-23
Hello:
I am not an experienced user, what I achieve is through perseverance and consulting documentation)
I managed to launch a non-profit weather information page on a Ubuntu VPS server. Many hours of configuration of the Apache server, but I have a question:
I have several software programs that upload data frequently when connected to the weather station, almost all allow me to upload via ftp and specify the path to /var/www/html but one of them (weatherlink) does not seem to understand paths and uploads to the /home/user directory
To solve this, change the default user path with sudo usermod -d /var/www/html meteosan but I am not sure if I did the right thing. I would like to hear advice. Thank you very much

---

### Post by Frogs Hair on 2024-10-23
Support request , moved to General Help.

---

