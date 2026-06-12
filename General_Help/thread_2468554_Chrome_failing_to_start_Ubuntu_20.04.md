---
title: "Chrome failing to start Ubuntu 20.04"
date: 2021-11-03
forum: General Help
---

### Post by alanpatx on 2021-11-03
Hi, I'm reposting this from a Chrome forum as no reply there. Any suggestions welcome.

After a recent reboot I am unable to start Chrome.  (Trace/breakpoint trap (core dumped)). I have tried removing the  application with "apt-get purge google-chrome-stable" and deleting  ~/.config/google-chrome and ~/.cache/google-chrome. Then rebooting  and reinstalling chrome, but get the same result. I have also tried  starting with:


google-chrome --disable-gpu
[244628:244628:1025/084326.997976:ERROR:gpu_init.cc(453)] Passthrough is not supported, GL is swiftshader, ANGLE is 
Trace/breakpoint trap (core dumped)


Terminal hangs and no app window appears.


If  I log in as a different user, I can run Chrome normally, so I guess it  must be something in my home directory that is causing this. If I log in as another user on CLI, whilst logged into gnome as me "su  other-user" and run "google-chrome", I get the same core dumped error.  If I log out of gnome and log in as the other user, chrome works.

The following messages appear in syslog consistently when I try to start google-chrome:-

Nov  3 08:51:41 frigiliana dbus-daemon[1017]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.312' (uid=1000 pid=270301 comm="/opt/google/chrome/chrome --enable-crashpad " label="unconfined")
Nov  3 08:51:41 frigiliana systemd[1]: Condition check resulted in Bluetooth service being skipped.
Nov  3 08:51:42 frigiliana gnome-keyring-d[2646]: asked to register item /org/freedesktop/secrets/collection/login/4, but it's already registered
Nov  3 08:51:45 frigiliana pulseaudio-dlna[1049]: 11-03 08:51:45 pulseaudio_dlna.daemon                         INFO     Checking pulseaudio processes ...

Thanks, Alan

---

