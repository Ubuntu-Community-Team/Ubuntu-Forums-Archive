---
title: "Can't browse files with WINE applications"
date: 2007-11-13
forum: General Help
---

### Post by luispa on 2007-11-13
Hi,

I installed Wine and executed winecgf. I tried to add drives but changes did not get fixed. So, I created symbolic links in the ~/.wine/dosdevices directory pointing to my Linux partitions. 

The problem is: If I launch a Wine application from the "Applications" menu I'm not able to browse files for loading nor saving.

The curious thing is: If I double click over a file in the winefile browser the associated application starts and I don't experiment that problem, I can browse files for loading or saving.

What could be the cause of this? How can I solve it?

Thank you very much in advance,

Luis Pablo

---

### Post by luispa on 2007-11-13
SOLVED!!! It was a permissions issue. I ran the WINE file manager from a root terminal, that was the difference.

---

