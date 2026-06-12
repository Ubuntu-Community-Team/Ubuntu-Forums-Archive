---
title: "apt-get install apt"
date: 2007-11-20
forum: General Help
---

### Post by HoCuS_PoKuS on 2007-11-20
Hello,


     I am still a little new to Linux Ubuntu. I have recently installed Ubuntu again to a hard drive that I was using and I am getting the same error as before.

During my boot up, Ubuntu goes into the recovery shell and does a scan. The scan says this error message: apt-get is not install to install type: 

apt-get install apt

I have typed in sudo apt-get install apt & sudo aptitude install apt
None have worked.

I can't do anything, nor do I understand why this is occuring. The hard drive is from an older PC of mine, which had Windows XP on it ((I bought this pc around 2000-2001)). I have browsed the internet and have not comed across much help.

If anyone can please exlpain what I can do to fix this problem, I would most grateful.
-JOSH

---

### Post by irw on 2007-11-20
This has happened on my laptop when one of the partitions in /etc/fstab is missing / the UUID is wrong.

I have no idea why it comes up with the apt message.

Try looking at which disk partition gave the error - when at the command line press shift-page up to see what has just scrolled off the top of the screen.

When you allow the computer to continue to boot, is it all working?

Another option once logged on is to type ¨sudo mount -a¨ in a terminal - that will tell you which partitions are causing the problems.

---

### Post by HoCuS_PoKuS on 2007-11-21
> **irw said:**
> This has happened on my laptop when one of the partitions in /etc/fstab is missing / the UUID is wrong.

I have no idea why it comes up with the apt message.

Try looking at which disk partition gave the error - when at the command line press shift-page up to see what has just scrolled off the top of the screen.

When you allow the computer to continue to boot, is it all working?

Another option once logged on is to type ¨sudo mount -a¨ in a terminal - that will tell you which partitions are causing the problems.

It is another HD that I am using. I have one HD with Windpws XP and this second HD is Ubuntu. I am begining to think that this just may be a hardware problem on the Ubuntu HD. I don't think that should be the problem though, I took it from my older PC that I bought in 2000-2001.

---

