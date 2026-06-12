---
title: "Ubuntu 12.04 not booting up &quot;mountall.....&quot; error : Please Help"
date: 2014-02-26
forum: General Help
---

### Post by zeetherocker on 2014-02-26
Hey guys... Yesterday night I was my Ubuntu 12.04 to compile a rom... I wanted to install kdiff3 but it was giving me dependencies error.. I googled the problem and found out that I have to remove libc6 with this command : ```
sudo apt-get purge libc6 && sudo apt-get --purge autoremove
``` and reinstall it 
But during the process of uninstallation... The OS hung.. so I had to reset the system... After the restart it just went into memtest... It was never ending so I restarted it again.. and it wasnt booting into Ubuntu... I used a live cd to use boot-repair...
This is the url I got from it : [http://paste.ubuntu.com/6999545/](http://paste.ubuntu.com/6999545/)

Now I can select ubuntu in GRUB menu but it gives me an error..
I've posted the pic in the attachment..
I don't wanna lose my synced android repo...PLEASE HELP ME :(

---

### Post by deadflowr on 2014-02-27
Unfortunately, it would seem that at this point your best course of action would a re-install.

libc6 is a critical package and not having it is going to keep being problematic.

Doing a little scrounging around found this
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=727786](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=727786)

Not much, but should maybe point at a way to re-install the package needed.
Without a complete overhaul.

---

### Post by zeetherocker on 2014-02-27
@deadflowr thanks a lot buddy... I'll surely check the link out and try what u said... I just don't wanna lose my data...

---

