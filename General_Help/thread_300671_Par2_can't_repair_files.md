---
title: "Par2 can't repair files"
date: 2006-11-16
forum: General Help
---

### Post by mageus on 2006-11-16
There are times when par2 can't repair a file set, but QuickPar can.  Par2 complains that not enough blocks are available.

This tends to happen on sets that are split using HJSplit(e.g. .001, .002, .003...).  Par2 has worked fine on rar sets (r01, r02, r03).

Looking at the par2 output, it loads all the par2 files (<fn>.volxx+xx.par2), but when 'verifying source files', doesn't list any of the .00x files.  It's like it can't see those segments.

Does par2 have a problem working with non-rar (.001, .002, .003) sets?

---

