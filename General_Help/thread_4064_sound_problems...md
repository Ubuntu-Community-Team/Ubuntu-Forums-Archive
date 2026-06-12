---
title: "sound problems.."
date: 2004-11-11
forum: General Help
---

### Post by phil on 2004-11-11
Hi i am haveing problems with my sound card under ubuntu linux and was wondering if anyone could help me with it. It used to work fine.

/dev/dsp has vanished, and with /dev/sound/ no longer existing.



After trying "MAKEDEV -v audio", still no dsp exists. However, the output from MAKEDEV suggests it should:

create dsp      c 14 3 root:audio 0660

create dsp1     c 14 19 root:audio 0660

create dsp2     c 14 35 root:audio 0660

create dsp3     c 14 51 root:audio 0660



lsmod returns the sound modules (snd_emnu10k1 etc) loaded.

---

