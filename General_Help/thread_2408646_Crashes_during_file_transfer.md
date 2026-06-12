---
title: "Crashes during file transfer"
date: 2018-12-21
forum: General Help
---

### Post by outdamnspot on 2018-12-21
I have an old laptop that I dropped accidentally; the hard drive started dying, making it impossibly slow to use, but I needed to rescue some files off it. My dad took the HD out and plugged it externally into our desktop computer, but when I tried to access the 'user' folder and grant permissions, it would just load for hours and not do anything (someone said it may have corrupt files on it, and thus be unable to grant permissions). A friend told me to try setting up a Live Linux USB, since Linux doesn't care about permissions. It worked and I can get into the 'user' folder now, and was able to save some Jpegs I wanted. 

However, I also need some Lightroom catalogues. I don't believe they are corrupted since I can get into the folders and see them all. But as soon as I try to transfer larger files to the Ubuntu desktop (~600mb), the transfer gets to about 100mb, then just stops and crashes eventually. This seems to happen with any large file.

Is there anyway I can get these files back without it crashing?

---

### Post by HermanAB on 2018-12-21
Hmm, well, disk files are random access and can be read in blocks, starting at any byte position.

So, using a utility like data definition 'dd', you can read any file in chunks of say 10 or 50 MB, starting at progressively larger offsets and reassemble the resulting blocks again using the failthful kitty 'cat'.

Another option is using the utility 'split' and 'cat'.

Some googling and man page reading will get you going - I don't want to spoil your fun by giving it all away.

---

