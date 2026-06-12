---
title: "auto-mount partition on startup?"
date: 2013-02-03
forum: General Help
---

### Post by LifeWithoutWindows on 2013-02-03
I need to mount a partition on startup and have it as writeable. How do I do this?

---

### Post by LifeWithoutWindows on 2013-02-03
bump

---

### Post by LifeWithoutWindows on 2013-02-03
bump

---

### Post by Bashing-om on 2013-02-03
No info ???????????? How are we to know what to advise ?

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[INDENT][INDENT]That will help

[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-02-04
@ LifeWithoutWindows: Please refrain from bumping your thread once an hour. Wait twenty four hours before bumping a thread.

Further persistant bumping will result in this thread being closed and further infractions will attract appropriate warnings/suspensions. 

If you are not getting a response it is because there is no-one in the forums, at this point, that can help, but, as pointed out by Bashing-Om, you also give no information on your setup and what you are trying to mount. Help the helpers. No-one here is psychic, as far as I know, so include as much relevant information as you can muster. ;) 

Thanks
BB

---

### Post by omeomi on 2013-02-04
Indeed, additional information such as the type of partition (filesystem) and the system your mounting it on as well as the version of Ubuntu that you are running are much needed to be of any help.

Other than that, in most cases you will need to edit the /etc/fstab file which you can read about in the links provided by Bashing-Om.

---

### Post by dan000 on 2013-02-04
> **LifeWithoutWindows said:**
> I need to mount a partition on startup and have it as writeable. How do I do this?

The file you're looking for is /etc/fstab. Since you don't provide any additional info, I can't help you any further with what should go in there.

---

### Post by Bucky Ball on 2013-02-04
> **dan000 said:**
> The file you're looking for is /etc/fstab. Since you don't provide any additional info, I can't help you any further with what should go in there.

As we've mentioned. 

@ dan000: Incidentally, and a little off-topic so apologies to OP, 10.10 reached end-of-life in April last year and hasn't been supported since; no updates including security updates. You should think about an upgrade, especially if this machine is on the net.

I mention it because your info says that's what you're using.

---

### Post by ibjsb4 on 2013-02-04
And lets not forget :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto-mount+partition+on+startup+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto-mount+partition+on+startup+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Bucky Ball on 2013-02-04
> **ibjsb4 said:**
> And lets not forget :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto-mount+partition+on+startup+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto-mount+partition+on+startup+boot&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

+1. Let's not ...

---

### Post by dan000 on 2013-02-04
> **Bucky Ball said:**
> @ dan000: Incidentally, and a little off-topic so apologies to OP, 10.10 reached end-of-life in April last year and hasn't been supported since; no updates including security updates. You should think about an upgrade, especially if this machine is on the net.

I mention it because your info says that's what you're using.

I'm not on 10.10; I'm on 12.10. In fact, I rarely ever come on Ubuntu Forums, and since I was last on here, they made it impossible to edit your profile if you've made less than 25 posts, so I can't correct that until I make a few more posts. I've been trying to respond to posts on here all morning to get it up to 25 so that I can update my profile. They really should've thought through this <25 rule more thoroughly, like making an exception for profiles that have been on here for a while.

---

### Post by Bucky Ball on 2013-02-04
> **dan000 said:**
>  They really should've thought through this <25 rule more thoroughly, like making an exception for profiles that have been on here for a while.

Possibly right. One for the admins. You might like to post in ***Forum Feedback & Help*** regarding this. ;)

---

### Post by dan000 on 2013-02-04
> **Bucky Ball said:**
> Possibly right. One for the admins. You might like to post in ***Forum Feedback & Help*** regarding this. ;)

Actually, since writing my last comment, I checked the post detailing the change. They said that they didn't grandfather in old accounts because they've had some sleeper spam accounts. It sort of makes sense.

---

### Post by Bucky Ball on 2013-02-05
It does make sense. Spam is constant and they'll get in anyway they can (resurrecting old threads is another one).

---

