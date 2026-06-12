---
title: "Intel / Nvidia graphics problems...."
date: 2021-05-20
forum: General Help
---

### Post by Furycd001 on 2021-05-20
Hey Guys.. I've been having some screen tearing & graphics problems with intel / nvidia on a fresh install of Xubuntu-core 18.04.5. I tried the regular Xubuntu 20.04.2 .iso but couldn't get it to boot after the installation had finished. Been trying for the past few days now to get graphics to fully function with no luck so far. I have the nvidia-driver-460 installed & if I select On-Demand or Performance Mode my laptop will fail to boot. The only way I can get back to the desktop is by booting into recovery mode and running "prime-select intel" from the root console. Screen tearing is everywhere and I can somewhat watch youtube in firefox, but local videos played through mpv will not load at all. I've attached an nvidia bug report just incase someone might be able to make something of it. Please help & many thanks in advanced....

[ATTACH]288517[/ATTACH]

---

### Post by guiverc on 2021-05-20
Are you aware that *flavors* of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not *flavors*), so you're asking about a release that is actually EOL.

See [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/) or a recent UWN - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses) (or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)) which highlights the EOL notices for Lubuntu/Ubuntu-MATE/Kubuntu & Ubuntu-Budgie.

Xubuntu didn't announce EOL but refer [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) and you'll see EOL was 29 April 2021.

---

### Post by Furycd001 on 2021-05-20
Ahhh right ok thanks for the heads up. Didn't know that. I might try & upgrade to 20.04 then....

---

### Post by Furycd001 on 2021-05-20
Ok so I've upgraded to 20.04.2 from the terminal & I'm still having the same problems....

```
 sudo do-release-upgrade 
```

Selecting either of the Nvidia options in Nvidia settings renders my laptop unable to boot. sudo prime-select intel fixes this, but screen tearing and video problems are still a thing....

This is what my nvidia settings window look like >> [https://imgur.com/y51lzd8.png](https://imgur.com/y51lzd8.png)

---

