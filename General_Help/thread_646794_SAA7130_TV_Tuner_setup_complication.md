---
title: "SAA7130 TV Tuner setup complication"
date: 2007-12-21
forum: General Help
---

### Post by lazertek on 2007-12-21
The OS detects the card but i cannot get any video to play. I would appreciate a step by step instruction on how to do this and what is the best application to use it with.. i found kde tv and tv time pretty impressive.

---

### Post by vbman11 on 2008-04-17
Try opening a Terminal(Applications->Accessories->Terminal) Then type:
```

sudo vim /etc/modprobe.d/saa7134

```

Then type your password, then press "a", then type:

```

options saa7134 card=98 tuner=69 video_nr=0 vbi_nr=0
alias snd-card-1 saa7134-alsa
options snd-card-1 index=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
remove saa7134-alsa { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/options -r --ignore-remove saa7134-alsa

```

Then press "Esc", Then "Shift+[Colon]", Then "W", Then Enter, Then "Shift+[Colon]", Then "Q", Then Enter

Restart then it should work. It did for me.

---

