---
title: "System/Administration menu choices disappeared"
date: 2007-01-03
forum: General Help
---

### Post by lordmoosh on 2007-01-03
Hello all,

I reinstalled Ubuntu a couple of days ago and everything was going well. I got Warcraft 3 running under Wine, etc. 

I was watching a video on VLC and I went to my System/Administration menu to open up the Synaptic Package Manager and noticed about half the options were gone. I restarted Ubuntu and it did not help. I went into the System/Preferences/Menu Layout and noticed that the items missing are unchecked. I cannot check them off now. Any idea what happened and how I can fix it? Thank you.

Mujtaba

I am running Ubuntu Edgy with the latest updates as of yesterday.

---

### Post by bselbekk on 2008-03-11
Hi!

I got the same problem after installing latest patches. The reason was that I was no longer in the "admin" group. Type the command 'id' in a terminal window. If you do not see "admin" in the output, then you need to boot Ubuntu in rescue mode, and add you user to the admin group.

To boot in rescue mode: intercept the GRUB bootloader, and select the rescue option.
To add you user to the admin group: find the line with the group "admin" in /etc/group, and add your user name at the end of that line. Then you reboot.

-Bård

---

### Post by bayvista on 2008-04-18
Hi,

Any other ideas? I have the same problem on Feisty and I am in the Admin group.

---

