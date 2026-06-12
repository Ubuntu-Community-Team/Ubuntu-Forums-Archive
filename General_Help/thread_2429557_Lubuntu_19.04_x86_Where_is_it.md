---
title: "Lubuntu 19.04 x86? Where is it?"
date: 2019-10-19
forum: General Help
---

### Post by adrian2895 on 2019-10-19
Hi,

I'm trying to download Lubuntu for installing it in a low-end computer and I'm looking for Lubuntu 19.04 x86 but on the official website, there's only available the x86 of it, the only x86 available version is an older version of lubuntu. How's that? Does it means Lubuntu won't support x86 anymore? To be honest, I don't like this decision as Lubuntu is meant to be used in low-end computers...

---

### Post by CatKiller on 2019-10-19
[https://lubuntu.me/sunsetting-i386/](https://lubuntu.me/sunsetting-i386/)

> 
Lubuntu has been and continues to be the go-to Ubuntu flavor for  people who want the most from their computers, especially older hardware  that cannot handle today&#8217;s workloads. However, the project and  computing as a whole has drastically changed in many ways since its  origin ten years ago. Computers have become faster, more secure, and  most notably, have moved off of the traditional 32-bit i686 (generalized  as i386 in Debian and Ubuntu) architecture.
 As an increasing number of Linux distributions have focused their  attention on the 64-bit x86 architecture (amd64) and not on i386, we  have found that it is harder to support than it once was. With i386-only  machines becoming an artifact of the past, it has become increasingly  clear to the Lubuntu Team that we need to evaluate its removal from the  architectures we support. After careful consideration, we regret to  inform our users that **Lubuntu 19.04 and future versions will not see a release for the i386 architecture.** Please do note that **we will continue to support Lubuntu 18.04 LTS i386 users as a first-class citizen** until its End of Life date in April of 2021.

This was announced last December or so.

---

### Post by uRock on 2019-10-19
I'd recommend Lubuntu 18.04 or Debian Buster LXDE. Canonical is doing away with almost all support for 32bit.

---

### Post by adrian2895 on 2019-10-19
So, I will be stuck at Lubuntu 18.04 I see.... It's a bit disappointing that one of the most popular Linux distribution has decided this. Even Microsoft still supports x86.

Another question, what will happen when 18.04 gets its end of life? Will I not receive updates anymore? Will I have old versions of web browsers like Chromium without being able to update them?

---

### Post by TheFu on 2019-10-19
For really low-end computers, there is always TinyCore.  [http://tinycorelinux.net/](http://tinycorelinux.net/)  It will probably be crazy fast on any computer made since 2006.

---

### Post by adrian2895 on 2019-10-19
Well, I have been thinking about this and I think I'll stick with Windows 10. I just wanted Lubuntu because I wanted something more smoothly, but sorry, it's pointless if within 2 years I won't be able to get updates.

Thanks anyway.

---

### Post by mörgæs on 2019-10-20
Yes, it's sad that a small number of persons in the Lubuntu team decided to stop supporting 32 bit but it's a fact nevertheless. Still I don't think you should jump to the conclusion that Windows 10 is the obvious alternative. As mentioned above many distros continue to take 32 bit hardware and their users seriously, both some with a look and feel close to Lubuntu and some far from. 

Anyway, you don't have to make up your mind before April 2021 when Lubuntu 18.04 runs out of support.

---

### Post by zimbuf on 2019-10-20
Thankfully, Debian still supports i386 and you can download an image [here]("https://cdimage.debian.org/debian-cd/current/i386/iso-cd/")

---

### Post by mastablasta on 2019-10-21
> **adrian2895 said:**
> Hi,

I'm trying to download Lubuntu for installing it in a low-end computer and I'm looking for Lubuntu 19.04 x86 but on the official website, there's only available the x86 of it, the only x86 available version is an older version of lubuntu. How's that? Does it means Lubuntu won't support x86 anymore? To be honest, I don't like this decision as Lubuntu is meant to be used in low-end computers...

if the CPU on the low end PC is 64 bit you can use the 64 bit OS.

the "low end" is not the limit actually. the architecture is. 64 bit OS can run 32 bit apps (at least for now  and until they pull the plug on 32 bit libraries) but not the other way around. 

i have a 15 year old desktop **single core **PC with 4GB ram. i run Kubuntu on it. on a 64 bit single core 1,2Ghz AMD with 224 MB ram the 64 bit with full DE would be pushing it. still a windows manager only or Lubuntu would run just fine. Programs would continue to be an issue since you need plenty of RAM to run GUI browser (yeah i know there is Lynx available and that would work fine).

if you have a 64 bit CPU and are low on ram you can install Ubuntu 64 bit and then just add icewm, openbox or something like that.

as other mentioned there are also other alternatives. AntiX or MX Linux are both aimed at old PCs and based on Mepis/Debian.

---

### Post by guiverc on 2019-10-21
I have and still use 
 
[LIST]
[*]ibm thinkpad t43 (pentium m, 1.5gb ram),
[*]ibm thinkpad t42p (pentium m, 1gb), &
[*]ibm thinkpad r50p (pentium m, 1gb ram).
[/LIST]
 They have Lubuntu 18.04 LTS or Debian installed on them, and were used to test debian buster x86 (10), Lubuntu 18.10 & 19.04 too until they (Xubuntu & Lubuntu; dec 2018) stopped producing the x86 ISOs.

Personally I'd use Lubuntu 18.04 LTS, and have debian buster (10) as your fallback should you still not have replaced the machines by then (if there old enough to be x86 only; there is a good chance hdd/ram/psu/etc will die between then and 18.04's 2021-April EOL in my opinion, and if even only one component, they may not be cost-effective to repair anyway).

In my case I did buy a x86_64 laptop (thinkpad sl510, 2gb c2d) to replace my r50p; it was used two days before the r50p was put back into use.  The newer thinkpad sl510 is now used for QA-test purposes

As for old browsers; updated browsers often don't work in older cpus; you may get an terse error message about your cpu not being supported, but not always, eg. when adobe dropped support for processors that didn't have SSE2; the browser just crashed (adobe packaging gave the error message at install time; if you ignored the warning the subsequent crashes from then on were on you). These issues are not just limited to GNU/Linux.

---

