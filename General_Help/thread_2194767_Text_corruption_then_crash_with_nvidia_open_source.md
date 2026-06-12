---
title: "Text corruption then crash with nvidia open source driver, problems with closed too"
date: 2013-12-20
forum: General Help
---

### Post by ses1984 on 2013-12-20
I have a system with Ubuntu 13.10 freshly installed. It has integrated Intel graphics and an add-on nvidia 8800gt. I would like to be able to use both graphics for triple head output.

This works fine using the open source nvidia driver...for a while. After the system has been on for a while, then I start to get some weird corruption. It looks like symbols for certain characters get replaced with other symbols. So as I'm typing, instead of seeing the characters that I actually input, I'll see something like this:

> SÄ as I'm typing, instead Äf seeing the characters that I actually input, I'll see sÄmething like this:

All the 'o' chars are replaced with 'Ä'. Usually shortly after that, my system crashes or it gets more corrupt then eventually crashes.

If I try to install the proprietary driver, I can't using the normal system and updates window. No additional drivers are found. Using the ubuntu wiki I have found ways to manually install the proprietary driver. This makes the system more stable, but then I can't figure out how to use the output from the Intel integrated graphics. In the system "Display" settings window, if I try to detect displays, I only ever see the displays connected to the nvidia card.

I would like to figure out why the open source driver isn't working and continue to use that one, if possible. If that doesn't work, I'd like to figure out how to use the proprietary driver and get output from the Intel integrated graphcis too.

---

