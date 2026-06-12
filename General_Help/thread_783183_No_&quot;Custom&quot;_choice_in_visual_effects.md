---
title: "No &quot;Custom&quot; choice in visual effects"
date: 2008-05-05
forum: General Help
---

### Post by nastyguard on 2008-05-05
Yeah I know what you're gonna say so read this before you post.
You will probably say something like "Go to your terminal and type sudo apt-get install compizconfig-settings-manager" 
Well yeah I tried to install it, and then reboot - nothing worked. Still no custom. I tried to remove it, install it again, reboot a couple of times, hell even once deleted and re-installed my ubuntu still didn't work. I guess it might be a hardy problem or 64 bit version problem, cause everything worked perfect with gutsy, but I can't say the same about hardy. Any suggestions or any information about the bug (if it is a bug in hardy or x64 version) please reply.

Best regards, Nasty.

---

### Post by FuturePilot on 2008-05-05
Try this
```
sudo apt-get install simple-ccsm
```

---

### Post by Exsecrabilus on 2008-05-05
Just press **Alt+F2** and type in *compizconfig-settings-manager* (after you install it, of course.)

Play around with the settings a bit, and then it'll have to be **Custom**, whether you see it under Appearance or not.

---

### Post by warp99 on 2008-05-05
> **nastyguard said:**
> Yeah I know what you're gonna say so read this before you post.
You will probably say something like "Go to your terminal and type sudo apt-get install compizconfig-settings-manager" 
Well yeah I tried to install it, and then reboot - nothing worked. Still no custom. I tried to remove it, install it again, reboot a couple of times, hell even once deleted and re-installed my ubuntu still didn't work. I guess it might be a hardy problem or 64 bit version problem, cause everything worked perfect with gutsy, but I can't say the same about hardy. Any suggestions or any information about the bug (if it is a bug in hardy or x64 version) please reply.

Best regards, Nasty.
Did you enable the universe repositories in Synaptic? Open the Synaptic package manager and under 'Settings > Repositories' enable the 'universe' repository. Close then press 'Reload'. Scroll down to you get to the compizconfig-settings-manager, right mouse click and choose 'Mark for Installation, then press the big checkmark to 'Apply'

---

### Post by nastyguard on 2008-05-05
Yeah it works fine with the simple compiz config settings mannager (SCCSM) but I would really like to go a bit more advanced like with gutsy. But thank you for helping me get this to work anyway. Thanks people!

---

