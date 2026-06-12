---
title: "firefox mplayer and vlc plugin issues"
date: 2007-11-02
forum: General Help
---

### Post by Digitallysick on 2007-11-02
When i go to sites and try to play mpegs the video just flickers , i can see it but it flashes so much its impossible to watch, i would like vlc to play all formats inside of firefox, (can it play wmvs inside of firefox?) how can i make it default instead of mplayer

---

### Post by minus198 on 2007-11-02
sudo apt-get remove mozilla-mplayer

sudo apt-get install mozilla-plugin-vlc

---

### Post by Digitallysick on 2007-11-02
i tried that but i still have bad video quality when watching avis or mpegs , its as if its flashing every 3 secoonds

---

### Post by Maestro23 on 2007-11-02
> **Digitallysick said:**
> i tried that but i still have bad video quality when watching avis or mpegs , its as if its flashing every 3 secoonds

Are you running compiz?

---

### Post by minus198 on 2007-11-02
Weird.. Personally I think that totem plugin works best with firefox. So try:

sudo apt-get remove mozilla-plugin-vlc mozilla-mplayer

sudo apt-get install totem-mozilla

---

