---
title: "amarok won't display files on windows partition"
date: 2007-11-18
forum: General Help
---

### Post by d3dtn01 on 2007-11-18
I recently reformatted my linux partition and installed a fresh copy of Ubuntu. I then installed amarok. I have 1/2 my music on my linux partition and 1/2 on my windows partition. The music on my windows partition is in mp3 format. I was able to install mp3 support for amarok. So, now I can play the files on my windows partition with amarok, but amarok won't display the songs in any lists. The only way that I can find these songs are by clicking on the "files" tab and then drilling into a specific directory. The songs don't show up in my collection tab. Thoughts?

---

### Post by AndyCooll on 2007-11-18
In Amarok, under Settings > Configure Amarok > Collection, is the relevent folder selected as part of your collection?

Also, have you done a "Rescan collection" following any changes made?

:cool:

---

### Post by d3dtn01 on 2007-11-19
This worked. Great suggestion. I thought that I had already done this. I definitely checked the directory during the initial configuration of amarok. I think I know what happened. After the first configuration, I rebooted. I had forgotten to customize my fstab so my windows partition wasn't being automatically mounted on boot up. Thus, the next time I opened amarok, the directory wasn't available. After remounting the windows partition, I forgot to reconfigure amarok. Thanks again for the advice.

---

