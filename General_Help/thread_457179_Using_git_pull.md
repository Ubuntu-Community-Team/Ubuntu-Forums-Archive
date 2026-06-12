---
title: "Using git pull"
date: 2007-05-28
forum: General Help
---

### Post by davef1m on 2007-05-28
I had to do compile a kernel to get a computer working (needed badram patch - won't work as a module).
Now I'm trying to use git to update my source tree.  I guessed I needed to change the URL line in .git/remotes/origin since the source is no longer where [https://wiki.ubuntu.com/KernelGitGuide](https://wiki.ubuntu.com/KernelGitGuide) claims it is.

But now, when I tried 'git pull' it seems to start working, but then it dies with:
<code>
fatal: Entry 'debian/abi/2.6.20-15.27/amd64/generic.modules' not uptodate. Cannot merge.
</code>
I guess this is because I had to remove the vboxdr line - it caused the compile to fail.
Do I really need to try and put that line back in the files I edited, and if so, why won't the kernel compile with it?

---

