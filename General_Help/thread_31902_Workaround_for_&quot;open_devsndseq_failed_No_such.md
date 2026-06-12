---
title: "Workaround for &quot;open /dev/snd/seq failed: No such file ...&quot;"
date: 2005-05-05
forum: General Help
---

### Post by graggrag on 2005-05-05
Like others, I struck the problem of /dev/snd/seq *not* being set up by hotplug, udev et al. The missing /dev/snd/seq device does get set up by a 'modprobe snd_seq', but manually running the modprobe, or even putting it into /etc/modules wasn't acceptable.

From what I could see, the only snd_seq module to be installed by hotplug was 'snd_seq_device', so I tied the installation of the 'snd_seq' module to that with the following entry in /etc/modprobe.d/sound (or /etc/modprobe.conf):-

install snd_seq_device \
  /sbin/modprobe --ignore-install snd_seq_device; \
  /sbin/modprobe snd_seq

With that, /dev/snd/seq gets set up automatically.

cheers.

---

