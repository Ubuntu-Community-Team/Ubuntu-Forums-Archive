---
title: "Ubuntu / Firefox/ SiriusXM has no sound?"
date: 2021-02-17
forum: General Help
---

### Post by rapidrob on 2021-02-17
All other forms of video/audio are working . Latest version of Ubuntu. All volumes set to normal no sound but shows music is playing in SiriusXM
What may be wrong? Yes I have a subscription. Other computers on Linux Lite is working
Links here are dead due to age.

---

### Post by #&amp;thj^% on 2021-02-17
First check in "pavucontrol" and you may have to install it.
```
sudo apt install pavucontrol
```
See screenshot to follow, make sure firefox isn't muted, and using the correct device.
That should be a good start, but post back if still having problems.

---

### Post by rapidrob on 2021-02-17
Speakers set to max. I downloaded pavucontrol but it won't open as a program. Not sure what command to use?

---

### Post by #&amp;thj^% on 2021-02-17
In a terminal run:
```
pavucontrol
```

---

### Post by rapidrob on 2021-02-17
There has to be a problem with Firefox. I downloaded Chrome and it works just fine, but I want to use Firefox. F/F is not muted.

---

### Post by #&amp;thj^% on 2021-02-17
> **rapidrob said:**
> There has to be a problem with Firefox. I downloaded Chrome and it works just fine, but I want to use Firefox. F/F is not muted.

In firefox, on the "tab" with SiriusXM playing....you should see a speaker icon make sure thats not muted or X'ed out

---

### Post by rapidrob on 2021-02-18
It is not muted out. Volume set to 90%.

---

### Post by rapidrob on 2021-02-18
I have two other Linux computers ttry out and see if Firefox is working with SiriusXM.

---

### Post by CelticWarrior on 2021-02-18
This is the exact same problem and with the same root cause as [here]("https://ubuntuforums.org/showthread.php?t=2452047"). There's no point in posting repeated threads for each and all media enabled websites you're using.
In that other thread I suggested trying Chrome (you ended up trying Chromium, doesn't matter, almost the same thing) and you reported it as working and that was the end of the story. It shouldn't have been because that suggestion was merely troubleshooting, i.e., intended to rule out a system wide problem with the sound and precisely to avoid the same suggestion as the 1fallen's above. The suggestions are entirely correct and give a correct basic troubleshooting but ignore the previous problem because in each instance **the threads' titles are misleading**. It's not a problem with Youtube TV, SiriusXM or even Firefox - it works for other users with the same websites - [B]it's a problem with *your *Firefox.

[/B]What problem you ask?
I have no idea. Some possibilities were mentioned [here]("https://ubuntuforums.org/showthread.php?t=2452047&p=13992950#post13992950"). So, IMO, it's either some addon/extension or a corrupt profile.

---

### Post by rapidrob on 2021-02-18
Thank you for the kind response. I do appreciate it.
The three other computers using Linux Lite are working on Firefox with no problems while connected to SiriusXM. The one computer running the latest version of Ubuntu  and Firefox still has no sound after installing the recommended software. It does work normally on Youtube and other sites with no issues.
It would be nice to find the cause of the no sound problem on SiriusXM / Firefox.
The only stupid question is the one that is not asked.

---

### Post by CelticWarrior on 2021-02-18
Try running Firefox without addons. Again, just troubleshooting.
If it works fine in safe mode it means there's some addon/extension messing things up.

---

