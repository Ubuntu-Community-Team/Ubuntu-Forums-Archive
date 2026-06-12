---
title: "Help fixing parent of an inode, couldn't find parent directory"
date: 2023-08-31
forum: General Help
---

### Post by khisanthax on 2023-08-31
Hello,

I'm running Ubunto 22.04 as a VM inside proxmox.  I've had this VM for a while but it's been off as I haven't needed it until recently.  When I turned it out I received an error with the filesystem that told me to manually run fsck, which I did as I have before but this time it said that it "couldn't fix the parent of inode: Couldn't find parent directory entry."

[Here's the screenshot.]("https://i.imgur.com/DEQt2gY.png")

[COLOR=#1C1C1C][FONT=&quot]I've recreated the directory that was missing, everything after modules wasn't there. I chmodded the last directory sev-guest, and I removed the sev-guest directory. None of that worked, each attempt I ran fsck and rebooted the machine but still the same error.  Any other suggestions on how to fix the filesystem?

My backups only go back 14 days and apparently this problem goes further back than that so none of my backups worked.[/FONT][/COLOR]

---

