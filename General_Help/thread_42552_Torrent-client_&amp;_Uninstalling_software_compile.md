---
title: "Torrent-client &amp; Uninstalling software compiled from source?"
date: 2005-06-18
forum: General Help
---

### Post by Krank on 2005-06-18
Hello!

Recently, I got a bit fed up with Azureus as a Torrent-flient - it's bulky and the worst system hog I have ever seen. I decided to try out some options - I still wanted a good GUI for torrent management, simply because I think a unified GUI is the nicest and most user-friendly (used in this context to mean: It's an easy weay to manage my torrent quickly and efficiently).

So, I set out to search for a torrent-client that could do what I asked - give me a nice list of current downloads and uploads, and monitor a certain directory for new torrents. I found nothing in the way of .deb packages, but I found both g3torrent and Freeloader ([http://www.ruinedsoft.com/freeloader/](http://www.ruinedsoft.com/freeloader/)) as sources, and decided to try them out.

Installing was no problems, they both installed just fine. I quickly found out that g3torrent hated my guts and that Freeloader just didn't do what I wanted to.

(for the record, I'm still looking for an alternative to Azureus)


So, now that I've tried them out and rejected them - how on earth do I uninstall them? I am an old Windows user, and under Windows I'd just delete the dir the prog was in, perhaps editing the registry if the prog added something there, and that was that - but in Linux, the files are "all over the place", and honestly, I don't even know where to start.

Not that either of these progs are large, but being a minimalist, I would really like my Ubuntu system to be at least reasonably free of clutter.

---

### Post by desdinova on 2005-06-18
In the directory you did a "sudo make install" do a

sudo make uninstall

Here's the problem of installing from source when you have a deb/rpm repository... Its always best stick to the packaged software

---

### Post by Krank on 2005-06-18
Ahaaaa... Big thanks, that worked like a charm. I almost feel a bit ashamed I didn't think of that one...

---

### Post by desdinova on 2005-06-18
Don't worry about it - we all learn something new every day ;-) Best way to be !

---

### Post by dresnu on 2005-06-18
you would also like to check "checkinstall" (it's in the repositories) for the next time you want to install a program from scratch

---

