---
title: "ksh history problem"
date: 2021-03-01
forum: General Help
---

### Post by cjsmall on 2021-03-01
I'm on Xubuntu 20.04.02

This is a question about **ksh** command history.  Something had changed recently and I'm looking for a way to restore the old behavior.

For years and up to about a month or so ago, when you typed a command with an error, it would issue an error message and the command would be placed on the history list so that it could be recalled and edited.  However, now the erroneous command generates the error but is NOT placed on the history list.  Here is an example:

 169-> for i in * do echo $i ; done
ksh: syntax error: `done' unexpected
169->

I intentionally left off the semicolon before the "do" and the command fails.  But you can see that the history number has not incremented and the command cannot be recalled to be edited.  This is a real PITA and I have 40 years of editing muscle memory that is being thwarted by this.  I have a hard time believing that someone is mucking about with the ksh code, but maybe.  Anyway, has anyone else seen this and is there a solution to get back the old behavior?

Thanks.

---

### Post by cjsmall on 2021-04-28
It turns out that the old ksh93 was silently replaced with something called ksh2020 which has bugs, including the one I reported here.  ksh93 is not listed in synaptic but it still exists in the repository and I was able to reinstall it with:

apt install ksh93

I have also been told that after the Ubuntu 20.04 release, the ksh package reverted back to 93u, but that is still not reflected in synaptic as far as I can determine, which is very confusing. I hope this helps others.

Here is the link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ksh/+bug/1918017](https://bugs.launchpad.net/ubuntu/+source/ksh/+bug/1918017)

---

