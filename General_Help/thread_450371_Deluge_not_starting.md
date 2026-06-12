---
title: "Deluge not starting"
date: 2007-05-21
forum: General Help
---

### Post by ironmule on 2007-05-21
I'm pretty new to the linux community. I installed Ubuntu 7.04 on my laptop only a few days after it was released and I love it.

Yesterday I installed Deluge and it was working wonderfully. I set it over night to download a couple of torrents and all was good. This morning the downloads were done and I shut down my laptop after closing deluge and pidgin (the only apps I had running). 

I got to work and went to set Deluge to download a smaller file I needed and it wont even start up. The curser shows activity and it shows up as starting Deluge in the bottom panel. But after that... nothing. The activity stops the panel clears and no Deluge!

Being new to Linux I'm not even sure where to start to fix this. Can anyone help me? Thanks in advance

Randy
Recent Linux Addict! :D

---

### Post by ironmule on 2007-05-21
Nevermind. After some further searching online I was able to find a solution. For nayone with similar issues you can use the following command and it may help...

rm ~/.config/deluge/persistent.state

---

### Post by jocku on 2007-11-20
> **ironmule said:**
> Nevermind. After some further searching online I was able to find a solution. For nayone with similar issues you can use the following command and it may help...

rm ~/.config/deluge/persistent.state

Yep, had the same problem, thanks for that command. It fixed the problem for me too.

---

### Post by silviutp on 2008-01-17
Thanks for the solution, I had the same problem,

---

