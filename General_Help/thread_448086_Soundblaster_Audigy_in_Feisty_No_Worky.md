---
title: "Soundblaster Audigy in Feisty No Worky"
date: 2007-05-18
forum: General Help
---

### Post by cybersavior on 2007-05-18
Hey all, I'm having sound problems (isn't everyone) with Feisty.  Here's a breakdown.

My card is a Soundblaster Audigy.  It worked great in Edgy out of the box.  I wanted to do a clean install so I reformatted and did Feisty from scratch (I lost all my old config files).  

The card is correctly recognized, 
```

$asoundconf list
Audigy

```

All relevant volume controls in alsamixer have been turned up.  I've spent the last half-hour or so trying what I've found in the forums to no avail.

Any help would be appreciated.  Thanks in advance.

---

### Post by riven0 on 2007-05-18
How about trying to reinstall and then restart alsa? That usually works for me.

> sudo apt-get install --reinstall alsa-oss && sudo /etc/init.d/alsa-utils restart

---

### Post by cybersavior on 2007-05-18
Sorry, that didn't work.

---

