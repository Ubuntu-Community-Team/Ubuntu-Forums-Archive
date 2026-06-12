---
title: "[SOLVED] Unicode filename in Wubi mounted NTFS partition"
date: 2008-05-24
forum: General Help
---

### Post by unicorn_2003_1 on 2008-05-24
Hello world! :)

First of all, big thanks to all the developers of the wonderful Wubi and *buntu systems.

One problem though: I installed Xubuntu on my Windows Vista ntfs partition through Wubi, the thing is Xubuntu can't display/create files with unicode filenames, like Chinese characters and those french accents, etc. I can't create a file with unicode/wide character names through Thunar, neither can Deluge create torrent files with those characters.

It was OK to create a file with a wide character filename on Xubuntu's own partition though (its own disk file).

So anything I can do to correct this? I guess it should be some editing in a certain config file, just don't know where to do that. Thanks in advance!

---

### Post by ago on 2008-05-25
[https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682)

Down the discussion there is a deb to install from tormod.

---

### Post by unicorn_2003_1 on 2008-05-25
Big thanks, the .deb file worked. This procedure is so handy, I think we should definitely include it in the next Wubi release.

---

