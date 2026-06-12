---
title: "Synergy key repeat problem"
date: 2008-05-14
forum: General Help
---

### Post by rschneid on 2008-05-14
I use my Ubuntu machine as a synergy server and windows XP as the client so I control both from the Ubuntu keyboard and mouse.  I recently upgraded to Hardy and found that while synergy works fine for the most part, when I use my windows box to connect to the console of HP blades or VMware guests I can barely type a character in those consoles without it repeating a dozen or more times.

Both of these console connections utilize an ActiveX plugin so I think it might be related to that.  However, it worked fine prior to my upgrade of Ubuntu.

Has anyone else seen, and hopefully fixed, this?

---

### Post by nseagoon on 2008-05-22
Hi,

I also use Ubuntu (8.04 amd64 desktop) as the server and Windows XP as the client.

I experienced all the symptoms you described in terms of key repeats, although I was using cygwin rather than blade consoles.

I stopped and restarted synergy on both the client and server. Finally, in an act of desperation, I rebooted my ubuntu host and the problem resolved itself.

Sorry, I don't know why this resolved the problem when simple synergy restarts did not!

BTW, I have synergy configured to start automatically on both hosts; the client has a Windows service and the ubuntu server has:

In /etc/gdm/PreSession/Default :
```
SYNERGYS=`which synergys`
if [ x$SYNERGYS != x ] ; then
        $SYNERGYS --config /home/username/.quicksynergy/synergy.conf
fi
```

In /etc/gdm/Init/Default :

```
/usr/bin/synergys --config /home/username/.quicksynergy/synergy.conf
```

This might not be an optimal configuration but it works. I obtained these steps from [http://ubuntuforums.org/showthread.php?t=48196](http://ubuntuforums.org/showthread.php?t=48196)

Hope this helps.

---

