---
title: "How can I re-insteall Ubuntu 7.10 on top on an existing ubuntu"
date: 2008-02-13
forum: General Help
---

### Post by yinglcs2 on 2008-02-13
I think some files in my ubuntu got corrupted.  I run 'fcsk', it said some files is bad .

Can you please tell me how can I re-install ubuntu on top of existing installation, trying to recover the corrupted files?

Thank you.

---

### Post by tact on 2008-02-13
If you have /home on a separate partition  (good idea to do it next time you reinstall fully) then you can just reinstall ubuntu and let the installer format all partitions except the one where you keep /home. 

Then you get a clean fresh install but all your config files and data that were in /home remain untouched.  Careful though... if you slip up and accidently format the partition that holds /home then you lose it all so the standard disclaimer applies - back up first...  :)

If you don't have /home on a separate partition already then I am not sure what you can do to just reinstall the operating system....  sorry.

---

### Post by SteveLaw on 2008-02-13
First of all I have no idea what I'm talking about, so this reply is more of a question.  

I myself just recently did a reinstall to repair a bodge-up I made - but I had a separate /home partition and so it was relatively easy.

However, because I have an ATI card I used the "alternative" CD and I noticed it had an option to "repair installation" that I don't remember seeing on the standard CD.  I didn't try it (I had already deleted my install partition manually prior to reinstalling) but I wondered what that does?  

Woulld that help the OP?

---

### Post by p_quarles on 2008-02-13
The alternate CD might help. The live CD can also be used as a repair tool in its normal mode, as can other live distros (such as Knoppix or DSL) that tend to be used as system rescue tools. 

This might help as well:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

