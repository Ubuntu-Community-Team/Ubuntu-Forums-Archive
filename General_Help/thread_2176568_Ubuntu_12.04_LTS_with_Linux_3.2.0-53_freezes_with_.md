---
title: "Ubuntu 12.04 LTS with Linux 3.2.0-53 freezes with usage"
date: 2013-09-25
forum: General Help
---

### Post by grimm-rob on 2013-09-25
I'm getting consistent hard-stops with any active usage on two different laptops whenever I boot using the 3.2.0-53 kernel. 3.2.0-49 seems to work fine.

First computer is a netbook: Samsung NB30 (non-touchscreen model)
Second computer is a laptop: Sony Vaio VGN-CR13/L (blue)

I can post more detailed information upon request.

Both laptops were purchased in China, but I don't think that matters.

Symptoms are that the system stops: screen doesn't update, mouse doesn't move, numlock/capslock do not toggle the LEDs. The weird part is that this only happens when the machine is being used. When the PCs are idle, I haven't seen either one freeze up.

I did some searches and found nothing, so I'm posting here. I'm going to try doing a kernel bisect when I get time -- I know 3.2.0-53 is bad, and I know 3.2.0-49 is good. What's the standard procedure after finding the bad commit?

Thanks in advance!

---

### Post by speartip on 2013-09-25
I have seen others commenting on hard lockups on the forum.
2 suggestions come to mind. 1st if the 3.2.0-49 works for you with no issues then carry on using that. The 2nd thing you could try is upgrading to the 3.5xxx or the 3.8xxx series kernel, which are in the repos if you have enabled backports.

---

