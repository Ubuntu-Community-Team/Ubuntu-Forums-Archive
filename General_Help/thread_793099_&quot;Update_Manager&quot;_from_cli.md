---
title: "&quot;Update Manager&quot; from cli?"
date: 2008-05-13
forum: General Help
---

### Post by talz13 on 2008-05-13
Is there a way to get the full update functionality of the update manager from the cli?  I don't really like having to VNC into my server just to click the update button.  I tried apt-get upgrade, but there were still a couple packages in the update manager that didn't get handled.

I did set up my update manager to automatically install security updates, though, so that should cut down on critical issues going unpatched for long.

---

### Post by minaev on 2008-05-13
`apt-get update' and `apt-get safe-upgrade' usually do the whole thing.

---

### Post by songshu on 2008-05-13
i only did it with debian on numerous occasions both never with Ubuntu, i heard something was changed although not sure what exactly, so you might want to google my advice to perform a simple good old ```
apt-get dist-upgrade
```

---

### Post by talz13 on 2008-05-13
EDIT:
I just ran ```
sudo apt-get dist-upgrade -s
``` and it said 0 packages to upgrade, so that looks like it won't stomp over everything like I used to think it would.


> **songshu said:**
> i only did it with debian on numerous occasions both never with Ubuntu, i heard something was changed although not sure what exactly, so you might want to google my advice to perform a simple good old ```
apt-get dist-upgrade
```

I was under the impression that dist-upgrade would upgrade me from gutsy to hardy.  If it doesn't, I'll definitely use that.  Reading the man pages for apt-get makes it sound more like it'll just upgrade my packages, not the whole OS, is that right?

---

### Post by songshu on 2008-05-13
> **talz13 said:**
> EDIT:
Reading the man pages for apt-get makes it sound more like it'll just upgrade my packages, not the whole OS, is that right?

upgrade the packages, that is exactly what it will do, 
and since the complete OS consists of packages there will be little else left.

you would have to adjust the /etc/apt/sources.list so it would say hardy instead of gutsy, but i sort of assumed you already knew that.

once again, i would do this on debian without a doubt,but i never did it with Ubuntu so i can give you no guarantees on this.

---

