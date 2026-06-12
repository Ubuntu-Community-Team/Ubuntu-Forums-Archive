---
title: "Audio Problems FIrefox Rhythmbox"
date: 2008-05-28
forum: General Help
---

### Post by Mantorp on 2008-05-28
hi...
I have recently installed Hardy and I must say that I'm a little dissapointed. The main problem is the sound. It works perfect when I use one program only (example Rhythbox). But when I open Firefox in the browser there is no sound when I watch videos in youtube. So i have to close both programs and start firefox again to gain sound. And it's the same if i first open firefox and than Rhythmbox. The only  change is that now is rhythmbox who is not working....grrrrrrrr

please help me.....

---

### Post by Caseyjp on 2008-05-28
> **Mantorp said:**
> hi...
I have recently installed Hardy and I must say that I'm a little dissapointed. The main problem is the sound. It works perfect when I use one program only (example Rhythbox). But when I open Firefox in the browser there is no sound when I watch videos in youtube. So i have to close both programs and start firefox again to gain sound. And it's the same if i first open firefox and than Rhythmbox. The only  change is that now is rhythmbox who is not working....grrrrrrrr

please help me.....


Firefox at this point is "pulseaudio" deaf.  If firefox has first dibs on sound, it works, but borks everything else 'after' it.

If another application is running audio, then firefox will be messed.

For the fricking life of me I still am not completely sure WHY 
a. firefox was released in an LTS version as a beta and
b. why pulseaudio was selected for, yet, again, an LTS, when it is CLEARLY not ready for primetime at this point.

:confused:

--edit- YES I KNOW why firefox's beta was included.  but part B, well I'm a gamer and a/v oriented, and pulse audio while doing some cool stuff just hasn't impressed me from a stability or 'just works' category at this point.

---

### Post by tobycatlin on 2008-09-07
So anyone got a solution to this problem. I am having this issue and it's very irritating.

ta
t

---

### Post by Caseyjp on 2008-09-07
> **tobycatlin said:**
> So anyone got a solution to this problem. I am having this issue and it's very irritating.

ta
t

Yep.  these two posts.  (first one references his second, but very informative):

1st:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=perfect+pulse]("http://ubuntuforums.org/showthread.php?t=789578&highlight=perfect+pulse")

2nd:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

Fixed the issues I was having.

---

