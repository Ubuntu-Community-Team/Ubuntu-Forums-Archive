---
title: "Unmet Dependancies"
date: 2013-01-24
forum: General Help
---

### Post by aarongolub on 2013-01-24
So I'm stuck in an unmet dependancies vortex. I'm running 64bit Ubuntu 10.04 on a VM.  I've got MySQL and MongoDB running on this machine.  I started having trouble when I attempted to upgrade to MongoDB 2.2 I was given an alert stating:
The following packages have unmet dependencies:
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10.2 is to be installed

So I scrambled to install libc6_2.15-0ubuntu10.2_amd64 using a .deb installed (after first installing libc-bin_2.15-0ubuntu10.2_am                                                                                                            d64.  Now, when i attempt to install mongodb I get an alert stating this:

 libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10.2 is to be installed

And if i attempt to run  'sudo apt-get upgrade' I get this same message. 

So...basically, I'm at a loss.  How do I surpass this libc6 warning?

---

### Post by mc4man on 2013-01-24
> **aarongolub said:**
>  I'm running 64bit Ubuntu 10.04 on a VM.  
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu10.2 is to be installed

So I scrambled to install libc6_2.15-0ubuntu10.2_amd64 using a .deb installed (after first installing libc-bin_2.15-0ubuntu10.2_amd64                                                                                                             
So...basically, I'm at a loss.  How do I surpass this libc6 warning?
"but 2.15-0ubuntu10.2 is to be installed" means **it was already installed** which if you're using 10.04 is a fairly poor idea & obviously will lead to issues as you've now seen.

(2.15-0ubuntu10.2  is the libc6 used in precise, generally one should not mix libc6 between ubuntu releases

---

