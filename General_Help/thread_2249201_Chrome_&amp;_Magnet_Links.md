---
title: "Chrome &amp; Magnet Links"
date: 2014-10-20
forum: General Help
---

### Post by Rob Sayer on 2014-10-20
Just installed Lubuntu 14.04.1 on my netbook.  Had Xubuntu 14.04 previously, which was slower than I remember, and Lubuntu 14.04 before that, which was pretty bug ridden.  Chrome wouldn't even accept keyboard input and none of the fixes worked for me.  Now I know why some users wait for the .1 release ...

But while it works better I can't open a magnet link from Chrome.  Tried the 1st answer from this, which always worked before:

[http://askubuntu.com/questions/108925/how-to-tell-chrome-what-to-do-with-a-magnet-link](http://askubuntu.com/questions/108925/how-to-tell-chrome-what-to-do-with-a-magnet-link)

Also tried the 2nd answer in this:

[http://askubuntu.com/questions/311537/torrent-magnet-links-open-new-window-but-not-transmission](http://askubuntu.com/questions/311537/torrent-magnet-links-open-new-window-but-not-transmission)

No joy.  It merely opens a new Chrome window.  Chrome is my default browser.

---

### Post by Rob Sayer on 2014-10-21
This worked fine in Xubuntu 14.04.  Not Lubuntu.  Do I have to install Debian to get a working LXDE install?

---

### Post by vasa1 on 2014-10-21
> **Rob Sayer said:**
> This worked fine in Xubuntu 14.04.  Not Lubuntu.  Do I have to install Debian to get a working LXDE install?

Could it have something to do with:> Warning: The choice in the last step is more important than it might seem. Picking lxde did not work for me! In xdg-open, the helper function open_lxde relies on pcmanfm (lxde file manager) and something is wrong with either the code in open_lxde or perhaps it's pcmanfm's fault.from the bottom of [http://askubuntu.com/a/133693](http://askubuntu.com/a/133693) ?

I once made a half-hearted attempt to download something using a magnet link but didn't get anywhere: this was using the Openbox session of Lubuntu 14.04.

---

### Post by Rob Sayer on 2014-10-24
> **vasa1 said:**
> Could it have something to do with:from the bottom of [http://askubuntu.com/a/133693](http://askubuntu.com/a/133693) ?

I once made a half-hearted attempt to download something using a magnet link but didn't get anywhere: this was using the Openbox session of Lubuntu 14.04.

Thanks, but I didn't do step #4 in xubuntu ... it wasn't necessary ... and it didn't seem necessary in lubuntu either.  That link doesn't suggest a solution anyway.

For now I'm using firefox, until I can find a solution.  Frankly when the next Debian stable I'll probably install that with LXDE.  Frankly with all the problems I don't know why Lubuntu has official Canonical support.

---

### Post by vasa1 on 2014-10-24
> **Rob Sayer said:**
> ... Frankly with all the problems I don't know why Lubuntu has official Canonical support.
Frankly, I'm happy that it has Canonical support. Been using it since 12.10.

---

