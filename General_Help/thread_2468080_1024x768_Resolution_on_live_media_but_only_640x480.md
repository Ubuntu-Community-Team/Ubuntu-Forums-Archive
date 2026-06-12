---
title: "1024x768 Resolution on live media but only 640x480 option after install"
date: 2021-10-18
forum: General Help
---

### Post by asifnaz on 2021-10-18
I have installed Lubuntu 18.4 32 bit on my old computer  successfully, but when I boot the installed Lubuntu, screen stays at 640x480 60hz. In live USB 1024x768 was working fine . I tried some other distros but result remained the same .Attached screenshots are of Linux Mint but its same problem with Lubuntu as well .
Please Help

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289302&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289303&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289304&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289305&stc=1[/IMG]

---

### Post by guiverc on 2021-10-18
The images don't show Lubuntu, and show a *deprecated* or *unsupported* kernel (*a kernel stack that hasn't been used/supported by Lubuntu since early early 2020 as it's EOL*).

(*the Lubuntu 18.04 HWE stack [upgraded to 5.3 in Lubuntu early 2020]("https://lubuntu.me/bionic-4-released/"), then [5.4 mid-2020]("https://lubuntu.me/bionic-5-released/")*, *so differs to that in your image*)

---

### Post by ActionParsnip on 2021-10-18
Linux Mint isn't Lubuntu

---

### Post by asifnaz on 2021-10-18
I installed Lubuntu first and got similar problem . Later I installed LM and Peppermint with similar results . I will install Lubuntu again and make the thread again . Please suggest me what CLI commands I enter in Lubuntu  and show their outputs here to determined my problem .

Thank you

---

### Post by guiverc on 2021-10-18
You pasted this is a *official* flavor area of UbuntuForums, but your pastes & details show clearly you're not using Lubuntu, or any *official* flavor of Ubuntu, but instead using out-dated & *unsupported* non-Ubuntu software.  If you want to use Linux Mint, you're most welcome to, but I'd not disguise & hide the fact, and use a Linux Mint site, or the non-Ubuntu area of UF where you'd be on-topic.

You do state you get it working at a resolution you're happy with in *live* mode, so I'd take notes of what is running & contrast that with details of the installed system.

I QA-tested Lubuntu releases from 18.10 onwards, using various x86 only laptops (pentium M, celeron), and pentium 4 & D desktop system (including respins of 18.04.2 & later). A couple of devices didn't like HWE kernels (the oldest pentium M (*with intel PAE bug*) didn't like 18.04.5 or the 5.4 kernel; but for them the fix was just to use the GA kernel stack (*it was safer than the prior unpatched 5.3 kernel*)).  I also recall graphic issues with `sddm` on `hp dx6120mt (pentium 4, 3gb, winfast clone of nvidia 7600gt)` on the 5.3 (Lubuntu 19.10) & later kernels; but the issue didn't show when the kernel was used in 18.04.4 (which didn't use `sddm` anyway) though if it did I'd again return to the older GA (4.15) kernel as I don't recall any issues there.   my point here is you have two kernel stack choices.

Your Linux Mint was using an unsupported kernel stack; not a wise choice if you're online - but doesn't matter if you're off-line.  You gave no details as to what you actually tried & had issues, or didn't have issues with regards the on-topic Lubuntu 18.04; your pictures contained only details of an off-topic release. You should have been specific with the on-topic OS.

Did the *live* system upgrade during, or post-install?   If so what were those changes?

That's where I'd look for clues; as the *live* shows what works; but the install shows what doesn't work.

On the QA-test issues I shared; if I installed Lubuntu 18.04.4 LTS on the oldest 2003 & early 2004 IBM Thinkpad r40p, r50p - the *live* system was perfect; however as it upgraded to 18.04.5 and the kernel shifted from 5.3 it was fine with, on reboot and into 5.4 the problems were very evident. By not using GUI, you could login & install the GA kernel stack, reboot & select/use the older GA kernel at `grub` (*which would have security fixes back-ported to it; why the 4.15 kernel is safer than the 5.3 kernel that installed & worked*) & the system is golden/great.

ie. here I'm suggesting comparing the *live* system with what you have issues with post-install.  that's what I'd be doing.   I'd also suggest you provide text of your pastes, and not pictures of text (*they are much harder to read*).

You do realize [Lubuntu 18.04 LTS is *end-of-life*]("https://lubuntu.me/bionic-eol/") . Your system I tend to think of as Ubuntu 18.04 LTS with LXDE (as Ubuntu 18.04 LTS comes with 5 years of support).  You can check our your own system's security status using 

```
ubuntu-support-status
```

which I covered in a few posts on Lubuntu's discourse (eg. [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466)) & another post on the site (link is there where I compare a `ubuntu-support-status` for my *i386*  thinkpad t43 with a prior example of a *amd64 *machine in a warning post.  I talk about alternative *i386 *OSes in that post too if you look (*including in the final post on the thread where I mention I QA-tested a rather recent release of an OS there too*)

Summary

- contrast what worked (the *live* system, with what was installed!)
- don't provide pictures of text when you ask for help, and ask where you're on-topic.

---

### Post by Yellow Pasque on 2021-10-18
Use vesa instead of fbdev.

---

