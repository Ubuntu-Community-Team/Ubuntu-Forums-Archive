---
title: "invalid mount option with external HD"
date: 2008-04-28
forum: General Help
---

### Post by krib on 2008-04-28
Hi,
I was just trying to change the name for my external HD because it had a space in it and that was causing problems.
I found fields for changing the name and mount options, and I foolishly re-typed the mount options in again by hand (I wasn't sure if I could leave it blank and it didn't seem to want me to highlight the displayed info to cut and paste).

I also messed up the mount point because it doesn't tell you not to put /media/  in front of the name. I found another post describing how to fix with gconf-editor, but now when I go to mount it says "invalid mount option"

Here are the mount options as listed in gconf-editor. my searching hasn't turned up any online manual that might tell me what the valid options are.

Can someone tell me if I typo'd one of these options? 

[rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other]

it's an ntfs drive and I have ntfs-g3 (is that the correct name?) installed. It all worked fine until I tried changing the name.

thanks

---

