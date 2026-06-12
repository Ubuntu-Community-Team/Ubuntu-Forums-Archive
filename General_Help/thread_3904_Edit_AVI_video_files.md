---
title: "Edit AVI video files?"
date: 2004-11-10
forum: General Help
---

### Post by kaput on 2004-11-10
I'm looking for a way to edit some video files (or at least downsample them). I've got a Canon Powershot A75 that I'm able to access via GTKam (though I wish I could use Gthumb) that takes fairly decent video with audio.

The files are AVI. Kino won't import them and AVIdemux crashes. Is there a better solution for editing? Or at least a decent way to downsample them?

---

### Post by NemoTheLobster on 2004-11-10
Kino is pretty picky, and only supports DV.  You might try using mencoder (mencoder-custom in multiverse) or transcode (not in the repositories), although I've heard transcode can't produce DV files Kino can read.

---

