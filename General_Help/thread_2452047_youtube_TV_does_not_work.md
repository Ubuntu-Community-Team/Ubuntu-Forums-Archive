---
title: "youtube TV does not work"
date: 2020-10-15
forum: General Help
---

### Post by rapidrob on 2020-10-15
I put youtube TV on my PC and it opens to the channel I wish to watch but I get an error " This video format is not supported".
I tried Video and  VLC and get the same error.
I looked in the software archive and nothing shows up.

---

### Post by ActionParsnip on 2020-10-15
What is "YouTube TV" please and how did you install it?

---

### Post by Quarkrad on 2020-10-15
Have you install ubuntu's media codecs?  In a terminal type:  **sudo apt-get install ubuntu-restricted-extras**    Also, installing vlc is good for installing various media codecs.

---

### Post by deadflowr on 2020-10-15
Does it require widevine to be enabled?
If using Firefox, widevine may need to be enabled manually.

Also, if you have any browser extensions, like ad blockers, try disabling them.

---

### Post by rapidrob on 2020-10-15
The sudo command did not solve the problem
Widevine is "Always on" in its settings.
Still getting the same error.
My Win 10 Pro computer has no issues opening the live feeds.
Im using Firefox.

---

### Post by CelticWarrior on 2020-10-15
Try Chrome.

---

### Post by rapidrob on 2020-10-16
Chromium worked.Thanks.

---

### Post by SeijiSensei on 2020-10-16
I have absolutely no problems watching YouTubeTV on Firefox. I'm on 20.04 with Firefox 81.0.  I have Widevine and the Cisco H.264 codec enabled. 

Are you using any sort of ad blocker or similar software like Ghostery? Try disabling them and then going to YTTV.  I have both UBlock Origin and Ghostery enabled and can still watch YTTV.

---

