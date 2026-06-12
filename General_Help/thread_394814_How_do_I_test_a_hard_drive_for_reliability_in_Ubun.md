---
title: "How do I test a hard drive for reliability in Ubuntu?"
date: 2007-03-27
forum: General Help
---

### Post by tictacman on 2007-03-27
I'm wondering how reliable one of my hard drives is and would like to run some tests.  I'm sure there are utilities out there for doing just that but I'm not sure what they might be called.  Any tips for testing the hard drive would be appreciated.  Thanks

---

### Post by der_joachim on 2007-03-27
If you mean physical reliabilty, I'd recommend badblocks, which tests for bad sectors. The file system itself is best checked with e2fsck. 

IIRC, badblocks is either in the repos or installed by default.

---

### Post by tictacman on 2007-03-27
badblocks is just what I was after. Thanks :)

---

