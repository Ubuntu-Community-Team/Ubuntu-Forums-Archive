---
title: "Rhythmbox crash"
date: 2007-05-10
forum: General Help
---

### Post by jackhynes on 2007-05-10
I get this output when trying to play one of my White Stripes albums, does it mean the file is corrupted or is it a rhythmbox fault? I play the song and it plays for a few seconds then rhythmbox crashes and closes...

```
rhythmbox
sys:1: Warning: Two different plugins tried to register 'ArtDisplayPlugin+RBPythonPlugin'.

(rhythmbox:20031): Rhythmbox-CRITICAL **: rb_plugin_activate: assertion `RB_IS_PLUGIN (plugin)' failed

** ERROR **: file mp3-c.c: line 518 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...
Aborted (core dumped)
```

Why is rhythmbox crashing?

---

### Post by jackhynes on 2007-05-11
Bump

---

### Post by Zeratul7 on 2007-05-24
Disabling some plugins could be helpful.

---

