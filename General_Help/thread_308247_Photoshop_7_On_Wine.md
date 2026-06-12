---
title: "Photoshop 7 On Wine"
date: 2006-11-27
forum: General Help
---

### Post by wongpk on 2006-11-27
Hi there, I'm just installing Ubuntu on my friends laptop. He just switches, and I'm installing Photoshop  for him but it seems like there are lots of problem and I need some help now and quick?

here are the error message:
> 
wiehanne@wong:~$ wine /home/wong/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  38
  Current serial number in output stream:  38


Anyone know why?

---

### Post by edemark on 2006-11-27
hi i have just checked appdb in winehq on photoshop 7 with wine 0.9.25 on dapper it gets garbage evaluation. Here is the link [http://appdb.winehq.org/appview.php?iVersionId=1336](http://appdb.winehq.org/appview.php?iVersionId=1336)  downgrading (in case you use 0.9.25) might help but you should give some more details (about the version of ubuntu you use and about the version of wine) 

good luck

---

### Post by byonk on 2006-12-02
following edemark's link to WineHQ, I noticed a HOWTO about the BadDevice error under Ubuntu ... it suggests "comment or delete the entries in your /etc/X11/xorg.conf, which are related to wacom. This is installed randomly, but if you haven't got a wacom it isn't needed at all."

okay, this worked for me. give it a try. unfortunately i do have a wacom tablet which i'd like to have work as well.

---

### Post by bover on 2007-01-27
i am having this problem too..
and as it is wrote to remove all entries in the xorg.conf that are relative to wacom..
it broked X :( so i was forced to use backed up xorg.conf..and as result all wacom's entries stayed at the same place..
please guys help me.

---

