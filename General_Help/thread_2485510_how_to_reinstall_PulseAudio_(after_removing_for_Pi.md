---
title: "how to reinstall PulseAudio (after removing for Pipewire)??"
date: 2023-03-31
forum: General Help
---

### Post by 777funk on 2023-03-31
I did this:
[https://www.maketecheasier.com/install-configure-pipewire-linux/](https://www.maketecheasier.com/install-configure-pipewire-linux/)

and regretted it. Maybe it would work if it were setup by pros... but I didn't have the patience to get it working. Unfortunately, this removed (I removed) Pulse.

IS there a good way to get it back? Thanks for any hints!

---

### Post by MAFoElffen on 2023-03-31
I am thinking from your question, that you did not follow his recommendation about doing a good backup, in case you wanted to go back... Or something went wrong.

It seems logical to me that doing each step in reverse...
```

systemctl --user --now disable pipewire pipewire-pulse pipewire-media-session
systemctl --user mask pipewire pipewire-pulse pipewire-media-session
sudo apt remove pipewire pipewire-pulse pipewire-media-session wireplumber
sudo apt install --reinstall pulseaudio
systemctl --user unmask pulseaudio
systemctl --user --now enable pulseaudio.service pulseaudio.socket
systemctl --user --now start pulseaudio.service pulseaudio.socket

```

---

