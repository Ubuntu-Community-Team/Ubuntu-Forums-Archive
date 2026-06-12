---
title: "Ubuntu freezing on 5 dots."
date: 2013-05-10
forum: General Help
---

### Post by shadowlyr on 2013-05-10
I am trying to use Ubuntu 12.04 on my laptop, and had burned it to a disc and then downloaded it onto my windows for the dual boot and everything. When I try to start up in Ubuntu now it will load up to where it says Ubuntu and the dots will go around a couple times turning orange and white until it finally stops on five orange dots and won't move any more then it already has. I've assumed it's frozen and have looked around the web and haven't really found any solutions. But can someone here maybe help me? By the way I know it's not the disc because it is working on other computers that I have tried it on.

---

### Post by Irihapeti on 2013-05-10
It sounds like it's something to do with the computer hardware. Can you give details i.e. CPU, graphics chip/card, amount of memory? Also whether you're using the 32 or 64 bit version of Ubuntu.

Firstly, have you installed Ubuntu as a dual boot, alongside Windows, or are you using Wubi? That will affect what happens next.

Can you boot from the live CD, or is that where the lockup is happening?

---

### Post by shadowlyr on 2013-05-10
> **Irihapeti said:**
> It sounds like it's something to do with the computer hardware. Can you give details i.e. CPU, graphics chip/card, amount of memory? Also whether you're using the 32 or 64 bit version of Ubuntu.

Firstly, have you installed Ubuntu as a dual boot, alongside Windows, or are you using Wubi? That will affect what happens next.

Can you boot from the live CD, or is that where the lockup is happening?

I have 4GB of memory, [COLOR=#000000][FONT=HPSimplified]Intel HD graphics 4000 with up to 1664MB total graphics memory, [/FONT][/COLOR][COLOR=#000000][FONT=HPSimplified]2.4GHz 3rd generation Intel Core i3-3110M Processor, and I am using the 64 bit version of Ubuntu. I also have it set to dual boot, and I tried yesterday from live CD and it was freezing, and put in the CD today and it downloaded while I was on Windows and it installed it and I don't need the CD anymore to boot it up (of course) and it is still freezing on the 5 dots.[/FONT][/COLOR]

---

### Post by Irihapeti on 2013-05-10
If Windows installed it, then it sounds like it may be a Wubi install. Unfortunately, I have no experience that, so I'll leave it to someone who does. Hopefully, someone will come along shortly.

With the information you've given, someone else should be able to take over.

---

### Post by shadowlyr on 2013-05-10
Awesome, Thanks anyways. I really like Ubuntu better then windows let me say.

---

### Post by sanderj on 2013-05-11
> **shadowlyr said:**
> I am trying to use Ubuntu 12.04 on my laptop, and had burned it to a disc and then downloaded it onto my windows for the dual boot and everything. When I try to start up in Ubuntu now it will load up to where it says Ubuntu and the dots will go around a couple times turning orange and white until it finally stops on five orange dots and won't move any more then it already has. I've assumed it's frozen and have looked around the web and haven't really found any solutions. But can someone here maybe help me? By the way I know it's not the disc because it is working on other computers that I have tried it on.

In the first second of the Ubuntu boot (so after the BIOS boot), can you press F6 and get a boot options menu? I would remove "splash quiet" from the boot options line, and continue the boot. That way you can see the boot log and see on what Ubuntu hangs.

---

### Post by shadowlyr on 2013-05-11
[ATTACH=CONFIG]242462[/ATTACH]This is what happens whenever I boot into Ubuntu and press F6. It doesn't give me that options menu.

---

