---
title: "Ubuntu really slow"
date: 2007-02-23
forum: General Help
---

### Post by Twiggy003 on 2007-02-23
Ive looked briefly around and i couldnt seem to find anything.  Ive used Ubuntu before, 6.10 and other versions, but for some reason when i recently installed it again, and all the usual things i install, Automatix, Easy Ubuntu, standard updates etc, since then its been extremely slow, and the system monitor says the CPU is at 99% or 100%, i dont know if there are any logs or anything to check where the cpu is being drained, ive never had a problem like it before.  cheers,

---

### Post by cisforcojo on 2007-02-23
What kind of system are you running?
And what is slow? It might be your gfx driver.

---

### Post by Rui Pais on 2007-02-23
> **Twiggy003 said:**
> Ive looked briefly around and i couldnt seem to find anything.  Ive used Ubuntu before, 6.10 and other versions, but for some reason when i recently installed it again, and all the usual things i install, Automatix, Easy Ubuntu, standard updates etc, since then its been extremely slow, and the system monitor says the CPU is at 99% or 100%, i dont know if there are any logs or anything to check where the cpu is being drained, ive never had a problem like it before.  cheers,

when its at 99-100% did **top** see which app is eating your cpu?

---

### Post by Twiggy003 on 2007-02-23
Well, the kind of system is as i usually do, i dont know what's different.  its always at 98 -100% and the top process is Xorg at 11 MiB, i install my gfx the usual way i always do [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) , the ubuntu way, which uses the older driver i think.  I can use firefox ok, but everything is quite slow.  thanks for the help so far.

---

### Post by srt4play on 2007-02-23
System monitor will show what process is eating all of your cpu time.  

Click on the CPU column in the processes tab to sort by cpu usage.

---

### Post by Twiggy003 on 2007-02-23
ah, never thought of that, ok, something to remember. if you're curious to what it was, i accidentally installed a tremulous server which was running in the background.  feel somewhat silly for not noticing that... lesson to be learnt i suppose, thanks for all anyhow :)

---

### Post by juantovarm on 2007-02-23
that is a bug, Bug 54684, 
sistem>administration>software sources>internet updates check all!!! you will have to see the download of:
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnomevfs2-bin

for more information, follow this link 

[https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/54684](https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/54684)

---

### Post by srt4play on 2007-02-23
> **juantovarm said:**
> that is a bug, Bug 54684, 
sistem>administration>software sources>internet updates check all!!! you will have to see the download of:
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libgnomevfs2-bin

for more information, follow this link 

[https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/54684](https://launchpad.net/ubuntu/+source/gnome-vfs2/+bug/54684)

His problem was with his Tremulous server consuming all of his CPU.  Read again and you'll see that.

---

