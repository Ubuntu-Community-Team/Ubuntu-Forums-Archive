---
title: "Apache2 not appearing in Services control panel"
date: 2006-11-04
forum: General Help
---

### Post by seanf on 2006-11-04
Since upgrading to Edgy, Apache2 no longer appears in my Services control panel. Any ideas how to correct this?

---

### Post by amohanty on 2006-11-04
Personally BUM works great for me, I would suggest trying that. The services control panel seemed a bit -not good enough-.
sudo apt-get install bum

HTH
AM

---

### Post by seanf on 2006-11-04
thanks - bum *is* pretty nice, and I do see Apache in there.

Strange that Services shows things that Bum does not (cron, klogd for example) and that Bum shows things that Services does not (ppp, timidity for example).

I'd still like to know why Apache isn't showing up in Services, when it did on Dapper. I'm guessing it's got something to do with upstart, but really have no idea how to fix it.

---

### Post by amohanty on 2006-11-04
Unfortunately when I find a nice tool, I sort of stick with it, so I couldnt really tell you whats going on. bum is a nice graphical tool. 

Theres an even better one which will allow you to control _everythin_ however  like all good things, it can be very dangerous if not used properly. Its a terminal app:
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

HTH
AM

---

