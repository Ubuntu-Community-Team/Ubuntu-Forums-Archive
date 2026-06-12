---
title: "Slow UI animations/response on Ubuntu Desktop 16.04.2 and 16.04.3"
date: 2017-12-14
forum: General Help
---

### Post by ryan-abmx on 2017-12-14
We recently discovered a problem with the two latest updates, Desktop 16.04.2 and 16.04.3. This problem happens in SuperMicro server boards, particularly the X10SRi-F with a Intel Xeon E5-2620v4. There are no additional cards installed in the system, and this happens with a fresh install...no additional packages or changes. This problem does not appear with 16.04.1

The problem appears to be that the animations run in slow motion, but the mouse cursor is fine. Since the cursor is fine, my guess is that the CPU/graphics chip is able to push 60hz out to the monitor but for some reason the rendering is slowed down. The animation is still smooth, but I can see the window get drawn from top to bottom. The login screen also has some issues with colors, I've attached two photos of the problem.

---

### Post by Holger_Gehrke on 2017-12-14
Not really surprising, if one reads the board specs at [supermicro]("http://www.supermicro.com/products/motherboard/Xeon/C600/X10SRW-F.cfm") and then looks up the capabilities of the [ASPEED AST2400 BMC]("https://www.aspeedtech.com/products.php?fPath=20&rId=376") . It's a pure 2D PCIe graphics chip. Modern desktop environments make heavy use of 3D capabilities for effects. Your board has to do all of them in software ... Either get a real graphics board in there or use a server (No Desktop) variant of Ubuntu or one of the lightweight flavours (Lubuntu or perhaps Xubuntu).

Holger

---

### Post by ryan-abmx on 2017-12-14
I suppose I could believe that, but we're only having this issue with this minor patch update. 16.04.1 works fine (and all other Linux distros), I don't think Ubuntu does any major upgrades for such a small patch. Isn't it usually just small kernel bug fixes and security? updates?

---

