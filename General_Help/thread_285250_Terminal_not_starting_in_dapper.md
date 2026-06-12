---
title: "Terminal not starting in dapper"
date: 2006-10-26
forum: General Help
---

### Post by metra on 2006-10-26
Basically what the title says.  I go to Applications>Accessories>Terminal

In the panel which shows which programs are open a box saying "Starting Terminal" shows up, the mouse changes to standby picture, then nothing. The mouse goes back to normal, the "Starting Terminal" disappears.

I tried re-installing using Synaptic, the re-install worked, but Terminal still not starting.  Also, tried re-starting the computer after that.

I used it a few days ago, and I haven't made any changes to my system since.


Thanks for any help.

Lynn

---

### Post by rumli on 2006-10-27
I had a similar issue in Edgy which turned out to be related to Xinerama and nvidia-glx, and I found a solution [here]("http://ubuntuforums.org/showthread.php?t=276354").

Adding:
```

Section "Extensions"
	Option "Composite" "false"
EndSection

```
to my /etc/X11/xorg.conf fixed it.

---

### Post by CatKiller on 2006-10-27
Does Nautilus work?

---

### Post by metra on 2006-10-29
rumil: thanks, I changed the code and rebooted and all is well.

CatKiller: I just looked up what Nautilus and I'm not entirely sure what it is or if I'm using it, I just read a review which compared it to konquerer , the article began by saying that most people who are happy using gnome won't ever have to choose. I thought I was using GNOME, but I'm still learning about all this...

As for if my shell was working or not...the only other odd thing going on was that when I went to shut-down, it took a very long time for the log-off screen came up.  But it did eventually came up and shut-down properly.

If I have Nautilus and isn't working, how would I know? What specifically wouldn't work?

---

### Post by CatKiller on 2006-10-29
> **metra said:**
> If I have Nautilus and isn't working, how would I know? What specifically wouldn't work?

Nautilus is the file browser thing. I'm glad you've got the terminal working now, though.

When I was first starting out, I'd managed to mess up the permissions on my Home folder, which meant that neither the Terminal or Nautilus would open, since they started in the Home folder, which I wasn't allowed to view. I thought it possible you'd done the same thing in some way.

---

