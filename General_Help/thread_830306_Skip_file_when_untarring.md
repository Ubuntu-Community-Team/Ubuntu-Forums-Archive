---
title: "Skip file when untarring"
date: 2008-06-15
forum: General Help
---

### Post by sparrowkc on 2008-06-15
I have a tar archive that keeps failing to extract.  I gets about 25% in then stops.  How can I tell tar to skip the file it fails on when extracting?

---

### Post by HalPomeranz on 2008-06-15
It may not be that the archive is bad, it may just be that the file the command is "sticking" on is really large and is taking a long time to unpack.

In any event, you can use the --exclude=... option to skip files in the archive.  If the archive is really corrupted, however, this may not do you any good.

One option to skip over damage in an archive is to try forcing the data through dd with the "noerror,sync" options turned on:

```

dd if=somefile.tar.gz conv=noerror,sync | tar zvf -

```

"noerror" causes dd to skip bad blocks, and "sync" causes dd to output a block worth of nulls in place of the bad block so that tar doesn't get horribly confused.

---

### Post by sparrowkc on 2008-06-16
It's a 85 gig archive, and the file it stops on is a video.  It finishes 2.5 gig of the video, but the file is bigger than that.

---

