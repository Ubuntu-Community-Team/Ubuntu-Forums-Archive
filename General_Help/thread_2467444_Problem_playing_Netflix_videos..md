---
title: "Problem playing Netflix videos."
date: 2021-09-26
forum: General Help
---

### Post by dlwy3k on 2021-09-26
After upgrading to the latest Firefox, videos on Netflix no longer work. They did before the upgrade.
Contacted Netflix but was told they do not support Linux. Therefore I came here hoping for help.
Every time when clicking on a movie, the error code F7701-1003 appears.
I have no idea how to solve this.
Does anyone know what to do about this?
Any help appreciated.
Don

---

### Post by QIII on 2021-09-26
> Contacted Netflix but was told they do not support Linux.

Tech support person that does not know what they are talking about.  I watch content on Netflix all the time.  By the way, Netflix doesn't "support Windows" either. 

Which version of Firefox?  When did it change?  Does this issue occur with other browsers?  Does it occur with all content?

F7701-1003 is probably an esoteric Netflix error code that is meaningless to the public.  Can you get a screenshot of that so we can see if there is any text explanation?

---

### Post by Dennis N on 2021-09-26
Use Google to search for the error. You find:
[https://www.online-tech-tips.com/computer-tips/how-to-fix-netflix-error-code-f7701-1003/](https://www.online-tech-tips.com/computer-tips/how-to-fix-netflix-error-code-f7701-1003/)

---

### Post by dlwy3k on 2021-09-26
Thanks for replying.
Firefox version 92.0.
I have no other browsers.
I found this regarding F7701-1003 and nothing helps thus far... [https://linuxhint.com/enabling_widevine_drm_ubuntu/](https://linuxhint.com/enabling_widevine_drm_ubuntu/)
Located libwidevinecdm.so.zip, extracted it and ran it. /home/<your_username>/.local/share/Steam/config/widevine/linux-x64/libwidevinecdm.so
Had to create directories after /share.
cannot execute binary file is the error that appears after trying to run it.

---

### Post by dlwy3k on 2021-09-26
Went here. Tried the suggestions with no result. Even did the reset.
[https://www.online-tech-tips.com/com...de-f7701-1003/]("https://www.online-tech-tips.com/computer-tips/how-to-fix-netflix-error-code-f7701-1003/")

---

### Post by Dennis N on 2021-09-26
> **dlwy3k said:**
> Went here. Tried the suggestions with no result. Even did the reset.
[https://www.online-tech-tips.com/com...de-f7701-1003/]("https://www.online-tech-tips.com/computer-tips/how-to-fix-netflix-error-code-f7701-1003/")

If it were me, I wouldn't spend a huge amount of time searching. I'd just try another edition of Firefox. Either download the .tar.gz file from Mozilla, or else install the Flatpak version. I've used both of these, and you can't tell the difference - except Netflix might work. They will coexist with the other Firefox without any problem.

---

### Post by T6&amp;sfpER35% on 2021-09-27
i use brave and watch Netflix all the time never had a problem.

have firefox 92 installed too but never uses it ,so just to test i tried netflix on it ...didn't work 

[https://i.imgur.com/ZK16SB3.png](https://i.imgur.com/ZK16SB3.png)

[https://i.imgur.com/XoyWqzz.png](https://i.imgur.com/XoyWqzz.png)

ok i see now you must enable the DRM setting to play this content
did that and netflix played fine
[https://i.imgur.com/8vCsSUO.png](https://i.imgur.com/8vCsSUO.png)

sorry for the big pics , i forgot to add them as attachments rather

---

### Post by Gatorade on 2021-09-28
I was also having the same issue with firefox and netflix, mine had a popup at the top of the screen asking to enable DRM.
I just clicked on it and firefox enabled it automatically.

worked fine after that.

---

