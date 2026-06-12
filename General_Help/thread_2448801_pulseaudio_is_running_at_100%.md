---
title: "pulseaudio is running at 100%"
date: 2020-08-13
forum: General Help
---

### Post by Skaperen on 2020-08-13
**pulseaudio** is running at 100%.  no audio is being played.  if i do play audio it plays fine and the 100% usage continues.  is this one of those "issues" it has with "system mode"?

---

### Post by TheFu on 2020-08-14
Someday, pulse audio will be stable. They've only had 10 yrs. It is much better now than it was 5 yrs ago, but still far from perfect.

Kill the pulseaudio process. It should automatically restart.  If it doesn't, then manually restart it. These processes are owned by your userid.

---

### Post by Skaperen on 2020-08-14
in _system mode_ there is a single central process owned by user **pulse** and that is the one that is running at 100% which is why i'm wondering about _system mode_.  when i play audio, this process, when it is not doing the 100% thing, jumps to about 8%.  no other processes run.  the individual userid process don't get started even for playing audio.

---

### Post by Skaperen on 2020-08-15
at this moment nothing is playing any audio at all.  only one process is running **pulseaufio**.  it is owned by user name **pulse**.  it is using 18.8% of CPU.  i have no ideas what it is doing.

*edit*:

i started playing a 16 minute audio file and CPU usage went up to 19.1%

---

### Post by Skaperen on 2020-08-15
is it mining bitcoin?

---

### Post by mc4man on 2020-08-16
Canned response
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/)

---

### Post by ActionParsnip on 2020-08-16
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Try that. Please give the output of step 3

---

### Post by Skaperen on 2020-08-16
> **mc4man said:**
> Canned response
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/WhatIsWrongWithSystemWide/)

i have read that before.  i do know it says increased CPU usage.  that makes sense as there is more to do to transfer audio to the central process in a secure way.

there is no other way to keep the music playing as i switch to other userids (typically about 18 userids logged in and typically about 6 in busy use).

what my initial post is asking about is why does it sometimes use so much CPU to do *nothing* (no audio is playing).

---

### Post by Skaperen on 2020-08-16
> **ActionParsnip said:**
> [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Try that. Please give the output of step 3

audio works fine all the time.  these steps are assuming one is *not* using system mode and will end system mode in step 1 making all further steps *unable* to diagnose any issue with system mode.  since a reboot is part of the steps i cannot do that for a few hours due to things i have running that don't have an ability to resume.  not that i would do them.

---

