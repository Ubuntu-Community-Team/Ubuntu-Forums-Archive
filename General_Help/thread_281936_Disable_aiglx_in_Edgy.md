---
title: "Disable aiglx in Edgy?"
date: 2006-10-21
forum: General Help
---

### Post by kernco on 2006-10-21
I upgraded to Edgy, but my computer doesn't have a good graphics card, so I have to use the vesa driver.  The addition of aiglx has made things like scrolling and moving windows very slow.  Is there a way I can disable it?

Thanks,
Colin

---

### Post by rjhale3629 on 2006-10-23
Ths might be the  same thing that is happening to me. I upgraded to Edgy with a ATI Radeon IGP 320 M video card and it was so bad I went back to dapper after a week. Hopefully someone will come up with an answer.....I guess commenting it out in xorg.conf (if it's even there) doesn't work....or might work.....Anywho...

Randy

---

### Post by gumbald on 2006-10-23
Was it slow on a base install or after you'd install an appropriate driver? My fresh install was painful until I got the Nvidia driver sorted...

---

### Post by rjhale3629 on 2006-10-23
I tried upgrading from dapper and then re-installing the whole thing. The only time I've ever had a driver that works is with mandrake and suse. I think suse has a binary driver by ati for this card. Other than that it's vesa....and it's painful for edgy - like I said I went back to dapper. This is the only post I've seen with a possible cause for the problem.

---

### Post by kernco on 2006-10-24
rjhale3629, I've tried a removing a lot of things from my xorg.conf, but unfortunately, no luck.

gumbald, it is definitely a problem with my driver, however I have tried everything I can think of to get it installed/working and nothing has worked.  I don't really need the eye candy of aiglx/beryl, so at this point it would be a much better solution for me to just not use it.

---

### Post by rjhale3629 on 2006-10-24
Right after I posted that - I did some checking - not much checking - but it appears that aiglx is enabled in xorg (compiled into) for this beryl compiz stuff - I'm trying to figure out if there is a xorg for edgy that doesnt have it enabled (compiled without it). I'm all up for eye candy but my laptop with a vesa driver can't handle it. I have hope.....there has to be a way. 

Randy

---

### Post by kernco on 2006-10-24
What if we change our package sources to dapper, reinstall xorg, then change back to edgy?  We will probably have to keep unchecking the xorg updates when we use the update manager, but it might work.

---

### Post by gumbald on 2006-10-24
AIGLX being enabled shouldn't matter, without Beryl installed there's no extra graphics processing involved. I think that AIGLX improves your graphics performance, it certainly did for me. Follow one of the guides in the [http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320) thread?

---

### Post by cmost on 2006-10-24
"What if we change our package sources to dapper, reinstall xorg, then change back to edgy? We will probably have to keep unchecking the xorg updates when we use the update manager, but it might work."

This isn't a good idea.  It might be useful for you to know, however, that you can "pin" packages at whatever version you want in the /etc/apt/preferences file.  Take a look on Google for the syntax.  If you pin packages in this way, then they won't appear "upgradable" in Synaptic, even if there are newer versions in the repos.

---

