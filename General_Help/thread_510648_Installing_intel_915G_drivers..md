---
title: "Installing intel 915G drivers."
date: 2007-07-26
forum: General Help
---

### Post by Albertahawk on 2007-07-26
Hello,

I was having issues with Americas Army, so I decided to check my video drivers, seems ive been using the i810 drivers for my 915G using card, So, i downloaded the drivers from the intel site, go to install them and it turns up this:

:~$ sh /home/hawk/Desktop/dripkg/install.sh
Could not locate 'pkginfo' file. Aborting.

pkginfo is right there next to install.sh, so I dont know whats up.

Also, trying to reconfigure X the 915 drivers arent there, so im out of ideas.

---

### Post by hedgefighter on 2007-07-27
I may be wrong but I believe the i810 driver covers the 8xx and 9xx cards. I use it on my 945GM. If you want the updated drivers they're in the repo called "xserver-xorg-video-intel".

Just install them. You shouldn't need to reconfigure your xorg.conf

```
sudo apt-get install xserver-xorg-video-intel
```

---

