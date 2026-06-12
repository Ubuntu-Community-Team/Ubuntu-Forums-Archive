---
title: "Some problems/errors"
date: 2007-05-28
forum: General Help
---

### Post by skulrid on 2007-05-28
Hi.
A progam I use (KTorrent) crashed, now I try to restart It but it wont start. I can see it on the system monitor but nothing happens. I tried to uninstall/install with no sucsess. Now I want to turn off my PC but it wont let me... I press shut down and it does nothing just stays there like as it "crashed"... so I use the reset button. Now it happens all the time I try to shut down or restart the computer. The same day I try to install another version of the program and I get this on terminal :

nuno@ubuntu:~$ sudo tar -xvzf ktorrent-2.2.tar.gz
tar: ktorrent-2.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I'm getting worried now... the system is acting strange lattely.

Nedding some help, thank you.

PS:(after all this I try to start Azureus (another torrent manager) and it also wont start...)

---

### Post by MoLE on 2007-06-03
skulrid,
I suspect that you might have more luck using a version of ktorrent packaged especially for your system.  I note on the [ktorrent.org download page]("http://ktorrent.org/index.php?page=downloads"), they have the latest beta packaged for the last 3 versions of ubuntu!
Same with Azureus - which is dependant on Java - if you use the prepackaged versions, you may have less trouble getting it all working, as the package maintainer has already done the hard work for you.

---

