---
title: "Thunar struggles to move files to/from Nexus 4"
date: 2014-05-04
forum: General Help
---

### Post by wolflint on 2014-05-04
[B]Xubuntu 14.04
[/B]When ever I connect my Nexus 4 device it nearly always recognises the device, sometimes when I click on the Nexus 4 icon it opens a folder with no files at all (not even any hidden files), sometimes it shows a folder called 'Internal storage'.
I want to move my music from my Nexus 4 onto Xubuntu, I open the Music folder (Nexus 4) in Thunar, then I open the Music folder in my Home. As soon as I right or left click on any song or folder, Thunar doesn't respond and becomes very laggy/or crashes.

---

### Post by TheFu on 2014-05-04
MTP is the issue.
Because the N4 has the file system internally mounted, it cannot be used as a normal USB device, forcing the MTP protocol to be used. I think we have a choice between using the N4 USB connection as a camera or under some other mode. Do not use the camera mode.

I found that moving large collections or many different files causes it to lock up too. I've tried different file managers and even using CLI tools. It doesn't matter. The connection is flaky, drops, and MTP doesn't support "move" - just copy/delete.

There are many things I like about my Nexus ... this is NOT one of them.

---

