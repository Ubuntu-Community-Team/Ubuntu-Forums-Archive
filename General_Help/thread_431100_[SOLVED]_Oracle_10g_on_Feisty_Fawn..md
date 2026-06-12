---
title: "[SOLVED] Oracle 10g on Feisty Fawn."
date: 2007-05-02
forum: General Help
---

### Post by shankariyer on 2007-05-02
Has anyone been successful in installing Oracle 10g Standard Database ( not XE ) on Feisty Fawn ?

I referred the documentation here, many links are broken.

I got this error, closer to the finish, not sure what it means and what to do from now...

> UnsatisfiedLinkError exception loading native library: njni10Any pointers? Thanks,

Kramer.
> Platform: AMD64, Feist Fawn 64bit, Oracle 10g Database ( Linux x86_64 )

---

### Post by egarbage on 2007-05-09
I have gotten Oracle 10g R2 to run on Ubuntu 6. Basically you have to make the kernel adjustments as outlined in the Oracle 10g documentation under the pre-installation section as well as the packages outlined in the same section. The trick is to use the &#8211;ignoreSysPrereqs switch with runInstall.

---

### Post by TomFumb on 2007-05-19
For me it worked fine out of the box, no error messages or complications. Oracle-XE 10g on Ubuntu Feisty, just double-clicked on the .deb, no special arguments. I'm not just trying to be smug, but just saying it's not necessarily a Feisty thing

---

