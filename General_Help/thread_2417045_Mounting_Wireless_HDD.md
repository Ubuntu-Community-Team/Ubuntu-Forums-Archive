---
title: "Mounting Wireless HDD"
date: 2019-04-19
forum: General Help
---

### Post by phr0stbyte on 2019-04-19
I have been able to connect to the wireless HDD and browse files. All I did was to go to "other places" in the file manager. Question is: How to I map it so that I have a valid path to use in other programs? It shows in file manager as "afp://anonymous@MyPassport.local/Storage". That just doesn't work for a path. Any help?

---

### Post by him610 on 2019-04-19
You might want to check out these links, [https://stackoverflow.org/wiki/Mount_an_AFP_share_from_Linux]("https://stackoverflow.org/wiki/Mount_an_AFP_share_from_Linux") and [https://askubuntu.com/questions/886656/how-can-i-mount-an-afp-share]("https://askubuntu.com/questions/886656/how-can-i-mount-an-afp-share")

---

### Post by phr0stbyte on 2019-04-20
Yep - I was trying to do exactly that, but is wasnt working. Got it going now - it was as simple as: Never mind - I got it. It was as simple as: mount_afp afp://IPaddress/Storage /home/phr0sty/MyPassport

---

