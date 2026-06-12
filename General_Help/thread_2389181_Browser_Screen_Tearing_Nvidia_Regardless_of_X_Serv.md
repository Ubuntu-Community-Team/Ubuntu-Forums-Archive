---
title: "Browser Screen Tearing Nvidia Regardless of X Server Settings"
date: 2018-04-12
forum: General Help
---

### Post by clap07 on 2018-04-12
[SOLVED]

I finally figured out what the problem was, it was my browser! I was using the Opera browser (didn't give me any problems on Windows). If anyone still has this problem after trying "force composition pipeline" or "force full composition pipeline" I would recommend that you see if your particular program is the problem. Also, don't use Opera on Linux!

Current settings: "force composition pipeline" (full pipeline wasn't needed). Driver 396.

[Original Post]

Hello everyone, 

I am a newly converted Windows user and I have really been enjoying my Ubuntu/Mate (mate desktop) setup, even though I have run into some technical issues. Perhaps the most annoying of these have been my issues with screen tearing. I just upgraded to 18.04 in the past few days, but I was having these issues before then with 17.10. I was hoping the upgrade would help, but it hasn't. 

I have tried going into the Nvidia X settings and forcing "full composition pipeline" but this seems to bear inconsistent results for me - even with it checked it is tearing at the moment. Any help would be greatly appreciated.

Specs:
Nvidia proprietary driver metapackage 390
Nvidia Geforce GTX 760
Ubuntu 18.04 64-bit
Mate Desktop 1.20.1
Linux Kernal 4.15.0-13-generic x86_64

EDIT: Composition pipeline (not full) seems to be helping, I will have to see if things stay that way.

RE-EDIT: Forcing composition pipeline seemed to help for a while, but upon reboot, I had the problem again. Also, I tried removing the composition pipeline setting altogether, but that didn't solve it either.

---

