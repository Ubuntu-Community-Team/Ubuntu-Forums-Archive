---
title: "Messed up Beryl; Probably an Easy FIx"
date: 2007-03-01
forum: General Help
---

### Post by brharri1 on 2007-03-01
I was playing around with my beryl settings, trying to see if it ran smoother under XGL or AIGLX. I right clicked the beryl icon at the bottom of the screen, and for rendering I selected 'force XGL' at which point my screen freezes. I know the solution is just to switch it back to 'automatic,' but whenever I load beryl-manager, it loads into XGL and freezes. Is there a way to change that setting without loading beryl-manager or a way to load beryl-manager without it defaulting to use beryl?

Thanks,

-Brian

--EDIT-- Argh sorry the premature post, it turns out the lines 

Option "DisableGLXRootClipping" "True"

and

Option          "TripleBuffer" "true"

were removed from my xorg.conf. I put them back in and everything is ok.

---

