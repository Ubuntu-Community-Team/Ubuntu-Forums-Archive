---
title: "How to limit maximum active torrents in rtorrents"
date: 2008-05-07
forum: General Help
---

### Post by kpkeerthi on 2008-05-07
Since my download bandwidth is pretty much limited (256 KBps max), I would like to have at the most two torrents running at the same time and have others queued automatically. I can manually pause the torrents I would like to defer but I usually do torrents during off-hours and leave it unattended. Can't seem to find a solution with google. 

Is it possible in rtorrent?

---

### Post by hyper_ch on 2008-05-07
that is not implemented yet, but I think there's a patch for that... you could also set the max connection to about 90% of your total upload speed.

---

### Post by kpkeerthi on 2008-05-07
Thanks. Much appreciated.

---

### Post by hyper_ch on 2008-05-07
have a look at that:

[http://www.stabellini.net/rtorrent-howto.txt](http://www.stabellini.net/rtorrent-howto.txt)

---

### Post by kpkeerthi on 2008-05-07
Thanks for the link. That should hopefully sort my concern out. 

I stumbled upon [a bug report]("http://libtorrent.rakshasa.no/ticket/13") to address this very issue. I can't believe that its not been addressed for 3 years now. But hey, I love rtorrent for what it is (free/open/functional/bla bla) :)

Thanks again.

---

### Post by hyper_ch on 2008-05-07
that's also where I got that link from... and I think Josef has written a patch... or will write one... (and if he does, you need to install rtorrent from SVN and compile it but that's not difficult).

---

