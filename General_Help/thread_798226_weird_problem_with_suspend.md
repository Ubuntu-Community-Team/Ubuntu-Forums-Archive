---
title: "weird problem with suspend"
date: 2008-05-18
forum: General Help
---

### Post by shelper on 2008-05-18
i installed hardy 8.04 amd64 to my computer
but my screen resolution is not right so i followed the instructions here to install the newest driver(not using envy)
[http://blog.vaxius.net/?p=42]("http://blog.vaxius.net/?p=42")
and the resolution problem is solved
then, i found i could not use suspend
more specifically, the x can not resume from suspend, but other terminals are ok

and i followed the instructions here to change the blacklist file,
[http://blog.vaxius.net/?p=43]("http://blog.vaxius.net/?p=43")
then the system gives warning during booting, saying one bad line start with "agpgart" in blacklist file 
and this same warning msg repeat 2 times.
i then recover the blacklist file but the system still keeps saying that. though there is definitely no bad line in the blacklist file as the warning msg

i found this related to the booting parameter, if using single, warning message is gone but still can not use suspend. if using quite splash, the warning disappears.

driving me mad. any idea??googled days. but could not find a real solution, but i believe it relates to the video card driver.
thank you so much!

---

