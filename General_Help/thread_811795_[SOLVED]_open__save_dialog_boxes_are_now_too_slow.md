---
title: "[SOLVED] open / save dialog boxes are now too slow"
date: 2008-05-29
forum: General Help
---

### Post by el_baby on 2008-05-29
Hi,

In a box I recently upgraded from gutsy to heron I noticed that any time I try to open or save a file, the dialog box (which I think is managed by gnome and not by each application) takes reaaaaalyyyyyy long to display.

That is, it doesn't matter whether I'm trying to save a file in oowrite, or open a folder in rithmbox, it always takes a lot of time (about 25/30 secs) until it opens the standard dialog box

I am not quite sure that this has to do with the upgrade or happened after I upgraded or what...

I don't see anything in either syslog, messages, .xsession-errors or Xorg.0.log...

Any hints?

(I'm command line friendly and know something about linux administration, so don't hesistate to post even if the solution might include fiddling with system settings manually).

Regards

---

### Post by el_baby on 2008-05-30
Bump?

---

### Post by salubrium on 2008-06-01
I'm also having the problem but I have been using Hardy since Release Candidates without issue. I only started noticing in the last couple of days and I thought it was an Inkscape problem because that's all I have been using.. now I realise it's actually a system wide problem with any GTK apps. Approx 30 seconds for the open/save dialogue box to display.

KDE apps seem to be unaffected.

---

### Post by huangja on 2008-06-04
So has this issue been resolved yet? It seems like a fairly large problem because it happens for all applications.

---

### Post by el_baby on 2008-06-05
Well... at least not for me... I tried downgrading libgtk to no avail...

And I have another Hardy at home (upgraded directly from Dapper) which has no problem whatsoever... it must be some strange interaction between different things... anyway, I'll be shutting down the problematic PC ('cause it was a loaner and I have to give it back), so I didn't invest a lot of time in this, these last few days...

---

### Post by kostyabkg on 2008-06-16
I have the same problem.

Check this: [http://ph.ubuntuforums.com/showthread.php?p=5016944](http://ph.ubuntuforums.com/showthread.php?p=5016944). Although this didn't help me :-)

---

### Post by wormie_dk on 2008-06-19
Same problem here... Happened after some upgrade a few days ago

---

### Post by mwohlf on 2008-06-24
I had the same problem on hardy,
after deleting all my bookmarks in nautilus the file dialogs came up right away again, I probably had an invalid smb or ftp mount in my bookmarks...

---

### Post by el_baby on 2008-06-25
I have only a handful of bookmarks and they're all valid :-(

---

### Post by mwohlf on 2008-06-26
I did a "strace -f gedit" then opened the file dialog in gedit to see the output of strace, this gave me a hint about the bookmark file that was being read which took forever...

---

### Post by dobuntu on 2008-07-07
> **mwohlf said:**
> I had the same problem on hardy,
after deleting all my bookmarks in nautilus the file dialogs came up right away again, I probably had an invalid smb or ftp mount in my bookmarks...

I have the same problem since about one week.
I have deleted all of my Nautilus bookmarks and recent doc list too, also tried with disabling my network connection, but with no gain (still about 30 seconds to show a file open/save dialog box).

This is true for all Gnome apps (KDE apps not affected).

---

### Post by practic on 2008-09-08
I also suddenly developed this problem.

I tested creating a new user, and their profile did not have the problem, so I knew it was something in the home directory.

I poked around in there, deleted some unnecessary stuff, but that didn't change anything.  Then I opened the Gnome System Monitor and it seemed that Tracker was taking up some of the CPU time while the dialog was delayed.  I had already decided to use Beagle instead, so I killed the tracker processes, and the dialog came up right away.

I'm not saying Tracker is the problem, because it was working fine up until a day or so, but it has something to do with this app, and removing it solved the problem (at least for now).

Perhaps someone else can take this further...

---

### Post by linguini on 2008-09-09
I also have this problem. After reading the previous post, I stopped the tracker daemon- but this doesn't seem to help.

---

### Post by el_baby on 2008-09-09
Disabling tracker worked for me too :-)

---

### Post by opholdings on 2008-09-09
Ditto on removing all things Tracker.  Everything now runs quick again.

Archive
Browse
Save File

All were 30 seconds before dialog box would appear.

Thanks

---

### Post by JJNova on 2008-09-13
Unfortunately, removing all things Tracker didn't fix the situation for me :'(


edit: correction. I was able to fix the problem with a restart. Not used to having restarts to make things work.


**For those who find this forum in hopes of getting a fix**
Try this. It worked for us!
```

sudo apt-get remove tracker --purge

```

Then restart your computer. ::cheers::

---

### Post by dobuntu on 2008-09-25
It worked for me too!
Tracker uninstalled (I never used it), daemon killed (so no need to reboot),
thanks practic!

---

### Post by netcrusher88 on 2008-11-11
Thanks practic and JJNova!  Worked great.

---

### Post by gdzsi on 2008-11-28
For me, some gtk themes using the murrine engine are painfully slow... don't know why but switching to clearlooks fixes the problem.

---

### Post by Miata-MS on 2009-04-30
> **el_baby said:**
> Disabling tracker worked for me too :-)

Sorry to resurrect an older thread.

Just had this problem crop up on me for the past two days with my Jaunty upgrade. Rebooting helped yesterday, and then today when it did it again I figured I'd see if the ever-helpful Ubuntu community had something that would work.

Disabling all tracker related items in System Monitor (trackerd, tracker-indexer, tracker-applet) instantly fixed the problem with no reboot or X restart.

```
sudo apt-get purge tracker && sudo apt-get install tracker
```

Seemed to fix the problem. Will update if it breaks things again.

Thanks to the posters and the admins for maintaining such a great resource of information

---

### Post by kingaaronj on 2009-05-03
Thanks so much for resurrecting this thread!  I was having this problem and purging / re-installing tracker fixed it.

Thanks! :D

---

### Post by Sharker on 2009-05-06
i have same problem but with purge and reinstall tracker don't work for me. I am 9.04 on 64 bits and with 8.10 works perfect, i put strace log out with gedit when press open button 

read(3, 0x1cfda94, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"&\0\2\0\3\0\200\4"..., 8}, {NULL, 0}, {""..., 0}], 3) = 8

---

### Post by AgenT on 2009-05-06
**PROBLEM:**
The default Tracker configuration is set to eat your computer alive! It is not the fault of Tracker, but with the insane default Tracker configuration (whether this is upstream's or Ubuntu's config I do not know).

Everything in the configuration file is set to MAX: including system resources, memory consumption, and speed.

**SOLUTION:**
1) go to Preferences -> Search and Indexing
2) click the Performance tab
3) set Indexing Speed to at least 10 (the 'slower' the better)!
4) set Resource Usage to "Minimize Memory Usage"
5) click "Apply", then click "OK"
5) logout and log back in again

This fixed it for me!

For reference, I have attached a screenshot of my General and Preference tabs.

**UPDATE:**
Tracker has many bugs, including the tracker-search-tool not showing correct results, or having the results but not showing them in the results window (the results are all blanks). Too big of a hassle! Also note, Tracker has a bug where it will not correctly read the configuration file which is VERY annoying. You can **easily and without a worry ****remove tracker** and all of its components.

---

### Post by pietro2580 on 2009-05-13
Yep, removing tracker did the trick!
Thanks guys!

---

### Post by Ralph Corderoy on 2009-05-18
> **Sharker said:**
> i have same problem but with purge and reinstall tracker don't work for me. I am 9.04 on 64 bits and with 8.10 works perfect, i put strace log out with gedit when press open button 

read(3, 0x1cfda94, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"&\0\2\0\3\0\200\4"..., 8}, {NULL, 0}, {""..., 0}], 3) = 8

A friend's machine was just suffering from this.  I tracked (NPI) his case down to a file locking deadlock and raised a bug.  [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/377899](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/377899)  Perhaps someone may like to read the bug and "Confirm" it if they agree.

---

