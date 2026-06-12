---
title: "Nautilus cannot handle X: locations."
date: 2008-05-01
forum: General Help
---

### Post by lippa88 on 2008-05-01
Hey i think i have a major problem with ubuntu 8.04.

I've seen bugs on this they are all marked as fixed, well MINES not.. heh

I get the error;

Nautilus cannot handle computer: locations.
Nautilus cannot handle network: locations.

and other applications, and i cannot mount anything. 

Is there a fix?

Thanks

---

### Post by fmonjaraz on 2008-05-21
Has anyone found one????

---

### Post by bankanidhi on 2008-05-27
> **fmonjaraz said:**
> Has anyone found one????
I also face the same problem. When i try to open my computer it give this message. I am using ubuntu 8.04

Couldn't display "computer:".
Nautilus cannot handle computer: locations.

Please help

---

### Post by Cerberu2 on 2008-05-27
i had tat problem to,i reinstalled ubuntu(hardy 8.04), i searched,i found no solution :S

---

### Post by jeffimus on 2008-05-31
Me too, since about 29 May 2008.  

Places / Computer and Places / Network menu commands don't work.  
Can't mount flash drives.  

I tried deleting ~/.nautilus as one thread suggested, but this didn't help.
Next step is to try going back to an older version of Nautilus, if I can figure out how.

---

### Post by Rossback on 2008-06-04
Has no one found a reasonable fix for this? (i.e. not reinstalling). I've been searching for this for weeks. I'm getting tired of mounting removable drives and SMB locations from the shell. My windows and mac colleagues are doubting the superiority of Ubuntu now...

---

### Post by sjordan on 2008-06-06
This problem just showed up for me last night, and I'm also missing my trash applet, but I'm not sure if it's related.

---

### Post by AngryBash on 2008-06-06
I'm having the same trouble with nautilus, and my trash folder too. I managed to find my trash folder in its strange new location, and delete it using "sudo rm". Trash folder is at "/home/*your user name*/.local/share/Trash". But this could be anywhere for you, ive found lots of places where Ubuntu puts my trash. 

You can easily mount partitions manually too. So that hasn't been a problem for me, but it would be nice to see this working in GUI form, makes things so much easier. 

*Waiting for a fix*

---

### Post by Tesiph on 2008-06-07
Downgrading the gvfs packages to 0.2.3 fixed the problem for me ([bug 238144](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/238144)).

---

### Post by sjordan on 2008-06-09
Downgrading the GVFS packages didn't seem to fix it for me.

---

### Post by fmonjaraz on 2008-06-25
I guess one bug so far is better than the 17 I would of had on vista

---

### Post by ex.hav0k on 2008-07-05
This is a nautilus only problem.  I installed Thunar file manager for when i use fluxbox and it doesn't have this problem.  So until there's a fix for nautilus I'll be using Thunar.  hell, i think i'll just switch to flux box, tbqh.

---

### Post by epictetus on 2008-09-08
I'm getting the same error message.  I can't access Computer, Network, or Trash; and my USB flash drive doesn't mount.  This bug is at Launchpad [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889) but there doesn't seem to be a fix so far.

---

### Post by RGPerson on 2009-03-01
This thread had some help for me:

[http://ubuntuforums.org/showthread.php?t=801597](http://ubuntuforums.org/showthread.php?t=801597)

It is a roller-coaster thus far.  One had me reinstall gvfs, but it uninstalled it.  Reinstalled it and it just wouldn't take. Found a way to reinstall Nautilus in another thread (there is a link to that in my post on above thread's page 3).  Then we had Nautilus back but not the desktop and trash.  Found a fix for that, but didn't post it right away and have now forgotten the particulars. It had something to do with a service not stopping at logout.  I edited something to make sure it would stop.  And the desktop and trash came back.

Right now I'm stuck with only one "cannot handle" and that's network: location. I don't know if that was left from the previous problem or if it crept back up after we fixed it.

That and now audio CD's won't mount.  Data will, from the same drive, but not audio.

Gabrielle

---

### Post by crazyfuturamanoob on 2009-03-01
Nautilus refuses to go to fonts:/// but acceps computer:/// trash:/// and some other things. Does fonts:/// even exists?

---

