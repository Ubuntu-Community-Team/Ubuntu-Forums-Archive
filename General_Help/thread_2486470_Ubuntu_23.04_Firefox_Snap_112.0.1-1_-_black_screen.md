---
title: "Ubuntu 23.04 Firefox Snap 112.0.1-1 - black screen"
date: 2023-05-01
forum: General Help
---

### Post by wobwill2 on 2023-05-01
Hi, 

Recent fresh install of ubuntu 22.10 updated to 23.04. On update Firefox loads to a black screen on first start. Killing firefox in the system monitor then restarting resolves the issue. Despite some google-fu which suggests a snap / wayland interface issue? I have been unable to to identify a solution. I've not installed Linux for for over a decade. The internet says the basics on Linux work now?!? please advise.

Many thanks

Will

---

### Post by wobwill2 on 2023-05-01
Update - after posting I've seen a notification advising to update Firefox. I've updated to firefox 112.0.2-1 which appears to have resolved my issue. Many thanks

---

### Post by wobwill2 on 2023-05-02
Hi, it appears that I spoke too soon yesterday. I've booted the laptop today and again on first start firefox loads to a black screen as I've described previously. Another post I've found suggests adding a new environment variable to force firefox to use wayland? but I am unclear how to do this, and certainly have no knowledge of vim. Please advise.

---

### Post by liberaltugboat-r on 2023-05-02
I have the same issue on a fresh install of 23.04.

---

### Post by wobwill2 on 2023-05-04
Hi LiberalTugboat-r

I've followed this guide: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) which appears to provide an effective work-around. At least ever since when I boot ubuntu firefox loads on the first attempt. 
best of luck.

Will

---

### Post by VMC on 2023-05-04
It must be a Firefox issue. I removed Snap, installed Firefox from mozzilla site, I get the black screen. Need to quit, then second attempt works.

---

