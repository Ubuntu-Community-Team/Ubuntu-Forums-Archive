---
title: "slow computer after login under my profile only"
date: 2021-12-03
forum: General Help
---

### Post by alain.roger on 2021-12-03
Hi,

I have ubuntu 21.10 with KDE plasma 5.
Till I used 1 monitor under ubuntu 21.04 my "loading time" (time from log in / password till KDE taskbar is displayed) was very short. Now I use 2 monitors and I do not know if it's related to this, but my "loading time" is about 2 to 3 minutes. Which is very slow.
So I created another profile just in order to test with an empty usernamespace. In this case "loading time" is about 18s.

Under my standard profile if I check with systemd-analyze, ubuntu returns me 2.3 s for booting and 8.7 for usernamespace.

So I lost ...
How can I do to get all LOGS from the moment I enter my log in password till the moment ubuntu display the KDE taskbar ?
The only error I see with Ksystemlog app is that systemd raise a "Failed to start Tracker metadata extractor."

I was thinking that autoFS could be an issue but I use it for several months now and even when I had only 1 monitor. So I do not understand where is the issue.
I would be glad to understand what's going on with my profile.

Thx

---

