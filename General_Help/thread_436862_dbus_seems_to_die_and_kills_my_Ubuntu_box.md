---
title: "dbus seems to die and kills my Ubuntu box"
date: 2007-05-08
forum: General Help
---

### Post by DavidWhyte on 2007-05-08
Earlier tonight my box locked up on me somewhat.  This happened twice, within an hour or two.  

When trying to hit the webserver it hosts, it wouldn't serve up a page correctly, however, it did show itself as being present.  Likewise, trying to ssh into the box gave a 'connection reset by peer' error as opposed to a 'not found' error you would expect when you get a complete lockup.  There was no response to any key presses however, even the NumLock light stayed on.

Looking in my syslog, there was an issue with dbus at the time of the lockup.  There was also a lot of HDD thrashing, but this could have been to do with logging backtraces etc.  

Attached are the two sets of messages from the syslog.  I haven't upgraded any software since the 3rd of May when official updates were pushed out, as shown below:

```

Commit Log for Thu May  3 08:50:11 2007


Upgraded the following packages:
capplets-data (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
gnome-control-center (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
libgnome-window-settings1 (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
libslab0 (1:2.18.1-0ubuntu2) to 1:2.18.1-0ubuntu2.1
```

Not sure whether I have a bug or something specific to my hardware.  Can anyone advise?

Regards,
Whytey

---

