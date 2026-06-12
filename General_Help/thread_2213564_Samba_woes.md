---
title: "Samba woes"
date: 2014-03-27
forum: General Help
---

### Post by carlo3 on 2014-03-27
Hey guys, been pulling my hair out for days over this. I'm sure the problem lies not with the samba config itself but permissions and I'm at a loss to figure out what's wrong!

Here's my samba config share:

[documents]
  comment = documents
  path = /allspark/documents
  vaild users = carlo, natalie, @smbusers
  browsable = yes
  guest ok = no
  read only = no
  force group = smbusers
  create mask = 0775
  force directory mode = 2775

I've got the 2 users carlo and natalie in the smbusers group. /allspark/documents has owner chief and group smbusers (chief is the main login on the server).

In windows, I access my share via carlo and all is good I have all the correct permissions and files are owned by me. On the laptop with ubuntu and logging in as natalie, when I connect to the share and try to copy a file into the share I get an error message saying the file cannot be found.

I think the problem may lie with the ubuntu laptop and permissions, I can make a new folder just fine and checking the permissions via ls -l shows it's all correct. Why I can't drag existing files from the laptop into it I have no idea. If I create a new file directly on the server too I can't edit it and save it afterwards.

---

### Post by carlo3 on 2014-04-03
For anyone having issues with something similar to this, I solved the problem by forcing uid=user and gid=group  in /etc/fstab. After this everything worked as expected and all issues were resolved! 

Very strange since I know for a fact the user and group exist both on the laptop and server but hey I'm sure it's something that I haven't configured 100%.

---

