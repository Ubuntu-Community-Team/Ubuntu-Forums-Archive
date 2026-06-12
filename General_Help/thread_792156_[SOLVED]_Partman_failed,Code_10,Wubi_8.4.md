---
title: "[SOLVED] Partman failed,Code 10,Wubi 8.4"
date: 2008-05-12
forum: General Help
---

### Post by drifter2502 on 2008-05-12
Can someone kindly help me please. I tried to install the new Wubi 8.4 today as a straight download from the Wubi site. Everything went smoothly until I got to step 2 of the installation ie.. selecting the correct country and time zone. When I tried to move forward to the next stage I got the following message, `Partman failed with exit code 10. Info may be found in /var/log/syslog. ´ I went back to the previous screen to try again with the same result so I canceled the install. Ubuntu then loaded but with limited use. I was asked to send in a report but was unable to do so. My wireless configuration worked on a local basis and I was able to go back to Windows with no problems. I am using a laptop(notebook) with AMD sempron 64 bit, Vista Basic with bucket loads of space to accommodate Ubuntu. I am not tech minded but with some help can usually get round most problems. I really want to try Ubuntu and this hurdle is not,I hope going to put me off!

---

### Post by ago on 2008-05-14
Uninstall, reinstall, presse esc at boot after ubuntu and select verbose mode.

If that happens again, press ctrl+alt+f2 and run

sudo sh /custom-installation/hooks/failure-command.sh

That will generate logs in c:\ubuntu\installation-logs.zip

Attach them here.

---

### Post by drifter2502 on 2008-05-15
Thank you Ago. Did exactly what you advised. Wow!Loaded with no problems. Some reports say wubi is slow on a straight down but this is working faster than Vista on my laptop(notebook). Wireless connected quickly and automatically. All codex for the music player works! Lots to learn but thanks again.

---

