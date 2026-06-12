---
title: "pavucontrol quit metering sound"
date: 2019-10-17
forum: General Help
---

### Post by Skaperen on 2019-10-17
earlier today it was working fine.  now, a few hours later, as i play the same music with same player (_mplayer_) those graphics in the _pavucontrol_ that meter the audio level are showing *nothing*.  but *everything else* still works.  i can hear the audio on every userid (_pulseaudio_ is in system mode).  i can adjust the levels in _pavucontrol_.  but the meter bars that earlier showed the activity of the audio with a fluctuating red bar now show nothing.  any idea what broke?

*edit*:

reboot ... now the metering works, again.  maybe pulseaudio needed a restart.

---

### Post by milesweb on 2019-10-18
I had tried [Sound troubleshooting procedure Step 6]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_6") when I faced an issue somewhat similar to this.

---

### Post by Skaperen on 2019-10-18
the playback device was not muted.  i could hear the audio just fine.  i could even set the levels in pavucontrol.  i just could see the meters doing anything.  they are working, now.

---

### Post by Artim on 2019-10-18
Don't forget to mark this [SOLVED] for the next user with the same issue.  PulseAudio was very troublesome at first, but it sure seems to have leveled off for the last few years.

---

### Post by Skaperen on 2019-10-18
there probably will never be a solution.  rebooting is, at best, a work-around for, what appears to be, a transient issue.

---

### Post by Artim on 2019-10-19
Yup.  I bet some future update will prob'ly fix it.  In the meantime you could make a bug report

---

### Post by Skaperen on 2019-10-20
i could, but i usually don't unless it is persistent in some way.  it's working fine tonight.

---

