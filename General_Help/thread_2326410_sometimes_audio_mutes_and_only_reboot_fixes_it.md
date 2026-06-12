---
title: "sometimes audio mutes and only reboot fixes it"
date: 2016-05-31
forum: General Help
---

### Post by a-you on 2016-05-31
Occasionally the audio just mutes, volume all the way down. There's no way (that I know of) to get it out of that state except for a reboot, which is not so nice. It seems to happen somewhat randomly. Possibly it's happening when an audio player (seemingly any of them) quits, but it's not really clear if this is the case. I tend to think so though.

If anybody has any idea why this is happening and what I can do about it, I'd much appreciate knowing. Many thanks in advance.

Or at least a workaround too would be appreciated---meaning for example some way to restart audio without having to reboot.

I'm using ubuntu studio xenial 64 bit. Thanks again.

---

### Post by QDR06VV9 on 2016-05-31
Have you tried running 
```
sudo alsa force-reload
```
Not the best solution but it beats restarting the system.
And sometimes I lose Pulseaudio with some very heavy chores i do.
and use these two commands to reinstate.
```
pulseaudio -k   ###kills pulseaudio

pulseaudio --start   ### To Restart it
```

Hope this helps.
Regards

---

### Post by a-you on 2016-05-31
Thanks @runrickus for those tips. As you say it beats restarting.

---

