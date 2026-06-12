---
title: "Ubuntu 16.04 Sound No Longer Working With Headphones"
date: 2017-04-16
forum: General Help
---

### Post by littlebobbytables2 on 2017-04-16
Hello,

So rather suddenly my sound stopped working with my headphones. It was working a few minutes ago, I put my computer to sleep and unplugged my headphones and now the sound won't work through my headphones at all. Sounds works with speakers with no problem, and when I plug in headphones Ubuntu recognizes that headphones are plugged in, sound just won't work with them. I've restarted pulseaudio and alsa and I've completely reinstalled alsa. At this point I'm out of guesses. 

Any help would be greatly appreciated!

---

### Post by RobGoss on 2017-04-16
Hello and welcome to the forum, Have you checked the settings to see if anything is muted? 

Run the following command:
```
alsamixer
```

Alsamixer will let you set the levels, make sure all the levels are at the top then try your headset I'm not sure if this will help but it's worth a try

---

### Post by littlebobbytables2 on 2017-04-17
I had already tried that to no avail. That being said, the issue has rather mysteriously resolved itself. My laptop was suspended for a few hours, and when I turned it back on the headphones worked again! Thanks for the suggestion, though!

---

### Post by RobGoss on 2017-04-17
Your very welcome, if you continue to have this issue feel free to come back. If you feel your issue is resolved you can mark this thread as solved by using the **Thread tool **tab at the top of this post 

Have a great day

---

### Post by vanadium on 2017-04-17
IF it happens again (and it probably will), try the command "alsactl restore". This immediately "restores" the headphones for me. Must be a bug in Ubuntu 16.04.

---

