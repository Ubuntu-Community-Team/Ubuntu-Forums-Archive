---
title: "Brave browser problem"
date: 2021-11-02
forum: General Help
---

### Post by uros-likar on 2021-11-02
[IMG]https://i.ibb.co/Q64WDcs/Screenshot-20211102-193918.png[/IMG]

I installed brave browser and I noticed that download window is weird :)  Anyone had similar problem?

How I can fix it? ... I use KUbuntu with some minor modifications. Can this be the cause?

---

### Post by T6&amp;sfpER35% on 2021-11-02
is that a pic of your file manager ? cause my brave browser download TAB doesn't look anything like that

---

### Post by uros-likar on 2021-11-03
This is the window brave opens when I want to download a file

---

### Post by ActionParsnip on 2021-11-03
Have you tried a different theme for the browser? Or a different Ubuntu theme to see if it makes any difference

---

### Post by T6&amp;sfpER35% on 2021-11-03
ok that's your file manager . what happens if you open file manager without brave ?

---

### Post by Shibblet on 2021-11-03
> **uros-likar said:**
> [IMG]https://i.ibb.co/Q64WDcs/Screenshot-20211102-193918.png[/IMG]

I installed brave browser and I noticed that download window is weird :)  Anyone had similar problem?

How I can fix it? ... I use KUbuntu with some minor modifications. Can this be the cause?

Are you using the Brave Snap?  If so, I would advise instead, going to the Brave Website, and using their install script for Ubuntu.

[https://brave.com/linux/#linux]("https://brave.com/linux/#linux")

---

### Post by uros-likar on 2021-11-03
@ActionParsnip => I tried to change brave theme but download window remained the same. I didn't tried to change ubuntu theme yet because current one is suits me and I don't want to change it :) I'll rather change the browser.
@3nd  => Filemanager works fine, firefox download windows is fine. Just filemanager which is opened by brave has problems. 
@Shibblet => Snap? I installed brave with Discover

---

### Post by T6&amp;sfpER35% on 2021-11-03
> Snap? I installed brave with Discover
suggest you try what shibblet said
uninstall brave with discover , then look [here](https://brave.com/linux/)
what version is your's? *menu - about brave*
mine's **Version 1.31.87 Chromium: 95.0.4638.54 (Official Build) (64-bit)**

---

### Post by uros-likar on 2021-11-03
Thanx, that solved my problem. I removed brave with Discover and install it following instruction from that site. Now when I try to download something it opens default ubuntu filemanager and all works as it should.

I expected that all programs downloaded with Discover which came with Ubuntu Installation are working fine. For a noob in linux world this can be frustrating, because you expect that official package manager will give you best results and not that you need seek better alternatives.

---

### Post by monkeybrain20122 on 2021-11-03
> **uros-likar said:**
> 

I expected that all programs downloaded with Discover which came with Ubuntu Installation are working fine. For a noob in linux world this can be frustrating, because you expect that official package manager will give you best results and not that you need seek better alternatives.

There are two types of programs in Discover. You can check that by going to the applications' description and check the publisher. If it is snapcraft then it is a snap. I suppose most snaps work but some are glitchy. Many third party applications such as Brave actually provides their own deb support and that is always preferable to the snap. You can also enable flatpak support manually, these are like snaps but IMO they work better than snaps and provide better access control through flatseal [https://flatpak.org/setup/Kubuntu/](https://flatpak.org/setup/Kubuntu/)

---

### Post by Shibblet on 2021-11-03
> **uros-likar said:**
> Thanx, that solved my problem. I removed brave with Discover and install it following instruction from that site. Now when I try to download something it opens default ubuntu filemanager and all works as it should.

I expected that all programs downloaded with Discover which came with Ubuntu Installation are working fine. For a noob in linux world this can be frustrating, because you expect that official package manager will give you best results and not that you need seek better alternatives.

Yes!  Glad to hear it!  In the immortal words of Hannibal from the A-Team.  "I love it when a plan comes together!"

I am still having some issues with Snaps, regarding a few of the programs that I use.  For some reason, if the file is a Snap, access to the file system is kinda screwy...  I'm not quite sure how to fix this, or if it is something I can even fix myself.  If anyone understands this issue, and knows how to fix it, please let me know.

---

### Post by monkeybrain20122 on 2021-11-03
> **Shibblet said:**
> 

I am still having some issues with Snaps, regarding a few of the programs that I use.  For some reason, if the file is a Snap, access to the file system is kinda screwy...  I'm not quite sure how to fix this, or if it is something I can even fix myself.  If anyone understands this issue, and knows how to fix it, please let me know.

Don't know how to fix snap's access, don't use it. But you may want to try flatpak, I have a few installed and don't have any access problem. There is a unified gui to control flatpak app's access called flatseal (also installed via flatpak), I don't think there is anything like that for snaps.

---

