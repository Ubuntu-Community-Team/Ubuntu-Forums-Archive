---
title: "[SOLVED] bittorrent tracker - keep getting errors and superslow transfers"
date: 2007-11-22
forum: General Help
---

### Post by bluepowder7 on 2007-11-22
hi guys,

i'm attempting to download PCLinuxOS using a torrent, and for some reason it just isn't progressing anywhere near what it should.  last night, i tried directly downloading the ISO images, and got to around 330megs out of 670megs and then the download stopped - either claimed it was finished, or just seized and wouldn't resume.  so, i found some torrent trackers, and i'm trying those, but again i keep getting crazy low speeds, lots of errors, and half the time the torrent will just grind to a halt.

i'm using the built-in bittorrent app, which isn't gui based (just pops up a small dialog box telling me how far it's progressed, what speed, and what errors are happening).  the error that keep popping up over and over again - on any of the 4 torrents i've found and tried - is:

"rejected by tracker - Tracker error 3"



what does it mean?  how can i get these blasted torrents to actually run at speeds exceeding 15KB/s?  i'm on DSL, and even though the line speed is currently down at 440k (instead of the 1.5meg that it SHOLD be at), the torrents are still a far cry from their potential.

can anyone help me sort out this torrent thing?  i'm keeping Ubuntu, but want to install PCLOS as a different flavour, just to see how things are different there.

---

### Post by rune0077 on 2007-11-22
I think its either:

a) because the default BitTorrent uses the default torrent ports, and some torrent hosts doesn't allow you to use them (because Internet providers deliberately slows them down). There's no way to change ports on BitTorrent (or maybe there is and I just don't know about 'cause I've never really used it), so you'll have to download some other torrent software that has this feature (Azerus, Deluge, BitTornado, etc).

or, more likely b) it's because you need permission from the host to use the torrent. Try going to the hosts webpage and see if you can register, then try downloading the torrent while you're logged in as a user on the website and I'm almost 99% sure that it'll work (well 75% sure at least)

Hope that helps

---

### Post by bluepowder7 on 2007-11-22
hmm, if i install and start to use a different torrent software, will it be able to recognize a partly-finished torrent and finish it, or would i need to start from scratch?

i just checked the progress, and the one torrent that i've had for the past 8 or 9 hours has managed to get itself half way done.  says it'll take another 10 or so hours to finish, which in reality means some time this weekend (what with the constant drops, slowdowns, etc).  would be nice to find a better torrent software that can finish up that job rather than restart...

i'll look into the whole registering thing, though.  it hadn't occurred to me and i didn't come across it while i was using torrents around a year ago.  must be a new thing...

---

### Post by bluepowder7 on 2007-11-22
update:

ok, i signed up at that first torrent tracker site (LinuxTracker), and managed to get it to continue downloading and appending to my existing half-done file, so that's going along at a good 450KB/s (i assume it's kiloBYTE and not kiloBIT).

also downloaded Deluge, opened up some ports, and gonna use that for the next download (did a quick test, and seems to be going quickly too)

thanks for the help!  :)  gonna mark this thread solved now.

---

