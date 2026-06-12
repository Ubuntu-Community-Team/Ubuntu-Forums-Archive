---
title: "Problems with &quot;winecfg&quot; New WINE config tool"
date: 2005-10-15
forum: General Help
---

### Post by MetalMusicAddict on 2005-10-15
Im getting this when I try to save the config:

[b]err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0[/b]

Happens when I try to define other drives also. I get the same thing as a user or as sudo.

---

### Post by MetalMusicAddict on 2005-10-15
Anyone using WINE in Breezy?

---

### Post by MetalMusicAddict on 2005-10-17
3rd times the charm?

I swear If I post a topic with a clear problem in the title I never get help. Im gonna rant more and post unclear topics so people look. :)

---

### Post by JogerNaut on 2005-10-18
I'm using wine in Breezy. Grabbed it from synaptic and I'm able to use winecfg fine.

If it's just setting the fake filesystem, you can probably set it manually by going to ~/.wine/dosdevices and making a linked directory.

BTW, 'C:' should point to /home/*username*/.wine/drive_c.

---

