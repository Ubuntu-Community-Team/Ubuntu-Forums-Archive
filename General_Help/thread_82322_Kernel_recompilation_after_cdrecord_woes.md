---
title: "Kernel recompilation after cdrecord woes"
date: 2005-10-26
forum: General Help
---

### Post by kikinovak on 2005-10-26
Hi,

I'm an ex-Slacker (100% since 2001) recently converted to Ubuntu. I really like Breezy, except for one major bug that's a real PITA: cdrecord doesn't work on a default Breezy install. 

Now I remember having had a similar problem coming from my IDE support being built as a module instead of being compiled into the kernel. As a result, DMA worked only so so... So, go and grab the sources.

Q1: what exactly are the sources for the kernel used in Breezy? Does apt-get install linux-tree-2.6.12 get me the 2.6.12 sources? Or the 2.6.12-9? I also see there is a linux-patch-ubuntu-2.6.12 package installed... and no info about it in /usr/share/doc. Am I supposed to patch my sources in order to get the right ones?

Q2, sort of subquestion to Q1: how patched is a Ubuntu kernel compared to pristine sources from kernel.org?

With Slack, I had a habit. First thing after installing, I grabbed the latest kernel sources from kernel.org, started from defconfig, added _only_ what lspci and dmesg told me to add and left out all the rest. 

Q3: how far will this approach lead me with Ubuntu?

Q4: the linux-patch-ubuntu package comes in a curious form. How am I supposed to apply it, in the eventuality? 

Any suggestions?

Niki Kovacs

---

