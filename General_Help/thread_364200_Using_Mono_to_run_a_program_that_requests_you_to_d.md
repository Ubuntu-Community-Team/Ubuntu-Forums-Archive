---
title: "Using Mono to run a program that requests you to download .NET"
date: 2007-02-17
forum: General Help
---

### Post by Sephiroth2088 on 2007-02-17
Well I was overjoyed to find they had made the opensource version of .NET, so I figured I could use mono to run a program that requires .NET framework. Well, I thought all would go well after I installed mono, but I find that that program I'm talking about still tells me I need to get .NET framework. 

So perhaps there is no way around this? though I hope that is not the case. It may be important to note that this app that needs .NET framework will not install without it, and requests it when you run the installation program. It should also be noted this installer program that prompts me to install .NET framework is obviously run in wine.

---

### Post by prensing on 2007-02-19
Well, I can't guarantee that this will work, but the check for .NET is probably only done during the installation. So, if you install on a Windows box and then copy the program directories over, it might work. Of course, Mono does not always run .NET apps properly, so YMMV.

---

