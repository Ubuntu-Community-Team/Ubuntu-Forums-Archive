---
title: "FIrefox/Chromium will play Youtube videos but not other videos"
date: 2019-06-08
forum: General Help
---

### Post by VBMeireles on 2019-06-08
I'm running Firefox Quantum 67.0 on a minimal installation (I believe) of Ubuntu 18.04 on a recently acquired Dell Inspiron I15-3567-D15P.
Embedded Youtube videos will play normally, but embedded videos from other sites just won't play. The videos seem to load, but the rectangle stays blacked out and the playback controls do not come up.
I've tried to watch the same videos on Firefox and Chromium (74.0.3729.169) but the result is the same with both. I've come upon solutions to similar problems that involve installing codecs (libavcodec) and trying Chrome, but before installing more software or resorting to Chrome (which I'd rather not) I decided to come ask you guys for help.

---

### Post by #&amp;thj^% on 2019-06-08
Could you give us some links to the sites that won't play in firefox?

---

### Post by VBMeireles on 2019-06-08
> **1fallen said:**
> Could you give us some links to the sites that won't play in firefox?

[https://pucminas.instructure.com/courses/1939/pages/aula-1-federalismo-e-sistema-constitucional-tributario?module_item_id=164367](https://pucminas.instructure.com/courses/1939/pages/aula-1-federalismo-e-sistema-constitucional-tributario?module_item_id=164367)

I'm afraid it won't be of use, though, since it's not an open site.

---

### Post by #&amp;thj^% on 2019-06-08
> **VBMeireles said:**
> 
I'm afraid it won't be of use, though, since it's not an open site.

+1>>>Preferably one that dose not need a login to view. :D
Just a thought though, sites like schools/university's use microsoft browsers, and no fault of firefox.
Any other site?

---

### Post by PaulW2U on 2019-06-08
> **1fallen said:**
> +1>>>Preferably one that dose not need a login to view. :D
Agreed 100% 1fallen.

I've come across several Firefox bug reports over the past year that require Ubuntu/Firefox developers and bug triagers to create account and attempt to make a purchase using a credit card. That is never going to happen.
> **VBMeireles said:**
> I'm afraid it won't be of use, though, since it's not an open site.
We need publicly accessible URLs in order to help.

---

### Post by VBMeireles on 2019-06-08
> **1fallen said:**
> +1>>>Preferably one that dose not need a login to view. :D
Just a thought though, sites like schools/university's use microsoft browsers, and no fault of firefox.
Any other site?

I tried Twitch and Firefox failed to open the streaming video on their starting page. I can't remember the exact error message, though. Chromium, on the other hand, played the stream successfully.

I decided to just go ahead and ```
sudo apt install ubuntu-restricted-extras
``` and after restarting Firefox the previously unwatchable videos and Twitch started to play normally. Regardless, I'll probably do another fresh reinstall and see if I can identify the exact codec (or package) I need to get instead of having to install the whole thing (I had to click "accept" once or twice and I remember seeing Microsoft - MS - pop up somewhere during the process also once or twice).

I decided to download the video and it turned out to be an .mp4 file (MPEG-4 video). Is that information of any help?

---

