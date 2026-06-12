---
title: "automatic sound reload on restart"
date: 2022-02-05
forum: General Help
---

### Post by pjstock on 2022-02-05
for some reason, on reboot I have no audio.

I found a fix online:
"First Alternate method to fix no sound in Ubuntu
If the above problem did not fix it for you, try reinstalling Alsa and Pulse audio in the following manner:
**sudo apt-get install --reinstall alsa-base pulseaudio**

And force reload Alsa again:

**sudo alsa force-reload**"

and I now only have to run that final command: "**sudo alsa force-reload"** each time I reboot (along with my passoword). Which is fine. but I wish there was a way to have that command line execute automatcially (and ideally add my password) each time I restart. I am sure there is a way. I just don't know how to do it.

can anyone advise?

Peter

---

### Post by psychohermit on 2022-02-05
I found a way to make a script run at startup in Linux, by making a service and running it at startup.  One good thing about doing it this way is you won't need to use sudo. Good luck, --glenn  [https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop](https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop)

---

### Post by pjstock on 2022-12-22
just seeing this now.
thank you, but it seems more complicated than I can probably manage.
those first lines - After, Execstart, wantedby - those are commands executed in Terminal mode?
or what do I do with them?

---

