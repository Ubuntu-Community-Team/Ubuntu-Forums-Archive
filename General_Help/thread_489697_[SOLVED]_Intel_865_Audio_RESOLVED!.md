---
title: "[SOLVED] Intel 865 Audio RESOLVED!"
date: 2007-07-01
forum: General Help
---

### Post by MrFSL on 2007-07-01
I have scoured these and other forums trying to find why I could get no sound on my integrated intel AC97 ICH5 audio. I have an Intel D865GLC motherboard but this fix will resolve issues on several systems both Intel and others.

BACKGROUND:
My audio was correctly detected and the correct ALSA modules were loaded. I had tried every fix I could come across and even tried to recompile and update the alsa-drivers package to no avail. Eventually I destroyed my Feisty installation altogether and now need to reinstall.

SOLUTION:
As it turns out the issue was simple to resolve. On the motherboard in a jumper block for FRONT PANEL AUDIO. I do not have any front panel audio on my case so I didn't hook anything up. HOWEVER! - From the manufacturer this block is supposed to come configured with 2 jumpers that connect the front left and right sends to the rear left and right returns. My motherboard did not come with these jumpers in place. I connected these two jumpers and now everything works!

Layer One Troubleshooting (guess I missed this one!)

I think this should be added to the audio troubleshooting guides! What a simple (although not all together intuitive) fix!

Hope this helps others. I have found dozens of posts about audio not working properly but setup seems correct.

Cheers,
MrFSL

---

### Post by auburn on 2008-05-06
At this point I still need to experiment some more; but I think your post solved my sound problem too. I have a gigabyte mobo: 8penxp.

---

