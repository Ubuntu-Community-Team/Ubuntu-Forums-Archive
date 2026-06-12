---
title: "Ubuntu.com related services extremely slow?"
date: 2006-08-04
forum: General Help
---

### Post by CallMeAl on 2006-08-04
HI all,

Over the past couple of weeks, I have noticed significant slowdowns when I attempt to access any Ubuntu related downloads.  I live in Michigan, and am using Comcast, but I  have confirmed with others in various parts of the country that the same thing is happening with other ISPs.
For example, I used to be able to download the Ubuntu desktop cd in about half an hour.  now, it's taking well over 3.
I just did an apt-get install of gnome-devel python2.4-dev build-essential automake1.9 and cvs, and the download took over 10 minutes.  I tried installing netselect-apt, in hopes of finding a better mirror; However, for some odd reason, Ubuntu appears to be packaging the debian version of this program, so it was completely useless.
  
Can anyone tell me what is going on, or point me to a thread or web log where this is being discussed?

Thanks,

--Al

---

### Post by wombat20 on 2006-08-04
For downloading large things like desktop CD ISO images you should use bittorrent if possible (some ISPs may ban this?).

[http://en.wikipedia.org/wiki/BitTorrent](http://en.wikipedia.org/wiki/BitTorrent)

---

### Post by CallMeAl on 2006-08-06
Hi,

I understand the benefits of bittorrent; However, the images I am most interested in at this point are the daily live builds.  Whenever I try them, the torrents for those seem to be completely inactive.

The bottom line though is that this slowness doesn't only effect the downloading of disk images.  it pervades everything I  try to do with Ubuntu, including downloading updates.  I really need to determine whether I can do anything about the issue and if not, who I need to approach.  There's some major congestion going on somewhere, but whatever the case, the lag is really causing things to become inefficient.  For example yesterday, it took 7 minutes for me to apt-get install emacs21-- not the sort of performance I would expect on a broadband connection in this day and age.  If I were the only one having the problem, I would perhaps assume that there are issues with my setup; but as I indicated in my previous post, I've checked with several people located throughout the US, and we're all experiencing the same thing.

Can anyone suggest some good tcp diagnostics i might try or something?

Thanks,

--Al

---

### Post by heavyt on 2006-08-08
I also have notice a mark decrease in download speeds when doing an update.

---

