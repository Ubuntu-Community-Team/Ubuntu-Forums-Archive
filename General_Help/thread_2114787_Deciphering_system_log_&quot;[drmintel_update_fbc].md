---
title: "Deciphering system log: &quot;[drm:intel_update_fbc], fbc set to per-chip default&quot;"
date: 2013-02-11
forum: General Help
---

### Post by hubertofliege on 2013-02-11
My Asus B53J keeps crashing.  The memory was bad, so I replaced it.  It still keeps crashing though.  The system log keeps repeating this, over and over:

> Feb 10 23:25:12 andrew-B53J kernel: [ 2030.361174] [drm:intel_update_fbc], 
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.361178] [drm:intel_update_fbc], fbc set to per-chip default
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.361181] [drm:intel_update_fbc], fbc disabled per module param
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.617305] [drm:drm_mode_addfb], [FB:31]
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.627008] [drm:drm_mode_addfb], [FB:32]
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.627055] [drm:intel_update_fbc], 
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.627057] [drm:intel_update_fbc], fbc set to per-chip default
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.627059] [drm:intel_update_fbc], fbc disabled per module param
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.643639] [drm:drm_mode_addfb], [FB:31]
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.643712] [drm:intel_update_fbc], 
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.643717] [drm:intel_update_fbc], fbc set to per-chip default
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.643719] [drm:intel_update_fbc], fbc disabled per module param
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.660228] [drm:intel_update_fbc], 
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.660233] [drm:intel_update_fbc], fbc set to per-chip default
Feb 10 23:25:12 andrew-B53J kernel: [ 2030.660236] [drm:intel_update_fbc], fbc disabled per module param
Feb 10 23:25:13 andrew-B53J kernel: [ 2031.307719] [drm:drm_mode_addfb], [FB:32]
Feb 10 23:25:13 andrew-B53J kernel: [ 2031.324889] [drm:intel_update_fbc], 

I don't know what this means.  I can't find anything by searching for terms.  My graphics card is an ATI Radeon hd 5770, I think.  Does this mean anything to anyone?  Is there somewhere I can look up what log messages mean?

---

### Post by hubertofliege on 2013-02-15
Gonna top this.  Any one?  I'd be super grateful.

---

### Post by dkz666 on 2014-02-06
Having a very similar issue on a Galago Ultrapro. Would appreciate any word on resolution.

---

