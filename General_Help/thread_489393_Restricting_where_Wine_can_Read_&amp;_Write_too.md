---
title: "Restricting where Wine can Read &amp; Write too"
date: 2007-07-01
forum: General Help
---

### Post by sefs on 2007-07-01
Hi all,

I want to install wine to Feisty.  But I want it to be in one self contained directory where it cannot do anything at all (Read, Write and Modify) outside of this directory.

Is this the default of wine or do I have to configure it that way.  And if so, after installing, how do I configure it to  be restricted to its own area.

Thanks.

---

### Post by steve.horsley on 2007-07-01
No it is not hte default. Run **winecfg** and look at the **drives** tab. By default it maps Z: to / thus making the entire system visible. Remove this drive mapping and I think wine apps are then restricted to C: which is mapped to ~/.wine/drive_c

---

