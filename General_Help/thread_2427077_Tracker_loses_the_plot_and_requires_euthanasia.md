---
title: "Tracker loses the plot and requires euthanasia"
date: 2019-09-17
forum: General Help
---

### Post by rbmorse on 2019-09-17
For reasons I do not understand, but fully admit are probably user related, my Ubuntu started
running poorly at first boot this morning.  Followed by an uncommanded DE reset. 

The system log reported an out of memory condition -- this box has 64 GB of physical RAM so 
that's unusual to be sure.  Htop showed one of the tracker related daemons eating RAM in 16 GB chunks until 
there was no more, then flushed and repeated. Occasionally the DE reset when memory maxed out. 

Condition Persisted over a reboot. 

So, the question here is, knowing that totally removing tracker is not recommended, is this the approved 
method for putting tracker to sleep: 

```

systemctl --user mask tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service

tracker reset --hard

```

or should I just append the string
```

Hidden=true

```

to the tracker related desktop files in /xdg/autostart, followed by the tracker reset --hard command?

---

### Post by cruzer001 on 2019-09-17
I prefer systemd

My thinking would be to just mask tracker-store.service and let the others set idle.  If that will do the job.

[s]Also looking around I see xdg/autostart/tracker.store.desktop has this line in it--
```
X-GNOME-Autostart-enabled=true
```[/s]

---

### Post by rbmorse on 2019-09-17
I don't know if this is related at all, but the excitement with Tracker started after I re-formatted my personal data partition (which is separate from /home and lives on a different physical SSD) to F2FS.  

This got me curious, so I did a clean install on 19.04 with the data partition formatted as EXT4.   All normal.  Re-formatted the data partition to F2FS and once again Tracker went psycho. 

I think I'll pay a visit to bugzilla and see if this behavior has been previously reported.

---

