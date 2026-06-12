---
title: "Ubuntu 12.04 not shutting down properly on Laptop"
date: 2015-03-14
forum: General Help
---

### Post by m3ideh on 2015-03-14
Hi all, I have a Dell Latitude E6400 laptop and just recently I've decided to wipe it and install Ubuntu 12.04 LTS.

I've found that it only shuts down normally if I never close the lid. If at any point I shut the lid and open it again, it works fine but when it shuts down it just stays on the purple shutdown/bootup screen that has the ubuntu logo and the six dots under it.

Please help, I've tried [this]("http://askubuntu.com/questions/155733/ubuntu-12-04-not-shutting-down-properly") solution already with no luck.

---

### Post by dino99 on 2015-03-14
what you describe is called 'plymouth'
check the logs to try finding some usefull warnings/errors (dmesg, xorg.0.log, /var/log/*)

you also can check the bios settings about powersaving for example and/or what is the default choice for managing the system: bios or the system itself ? (of course i have no clue about that laptop bios, so check it closely)

---

### Post by mörgæs on 2015-03-14
Why did you install 12.04 and not 14.04.2?

---

