---
title: "Background Music Box"
date: 2006-10-25
forum: General Help
---

### Post by Rick Henson on 2006-10-25
I am wanting to create a box that when booted up would activate a schedule so that at lets say 8 AM a music player would start then randomly play a list of mp3's from a direcroy. Then at let's say 8 PM the music player would shut down. This would repeat once a day. The purpose/use of this is for a business so that each morning the system would automatically start playing background music and then shut down at the close of business.

My questions are: 
Is this possible? and if so:
What scheduler software should I use?
What music player should I use?
Any other thoughts, tips or ideas welcome.

Thanks in advance for any help,

Rick

---

### Post by IYY on 2006-10-25
A simple script solution would be to use cron, and use XMMS as the player (because it can be controlled from the command line).

There are also graphical solutions, but I prefer cron.

---

