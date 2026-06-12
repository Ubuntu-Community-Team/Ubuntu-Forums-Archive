---
title: "Windows cannot find ubuntu"
date: 2008-04-28
forum: General Help
---

### Post by Brian R. on 2008-04-28
Could somebody please tell me what i am doing wrong. Installed Hardy Heron and can get ubuntu to see windows machine, have set up network printer ok. Windows can see ubuntu machine and the network printers but nothing else. Have right clicked the folder i wish to share, selected share, clicked share this folder, and allow other people to write to this folder, clicked Create Share. Get dialog box "Nautilus needs to add some permissions to your folder in order to share, click add permissions automatically. Then back to share and click Create Share and get the following error message.

'net usershare' return error 255:net usershare cannot open usershare directory /var/lib/samba/usershares. Error permission denied. You do not have permission to create a usershare. Ask your administrator to grant you permission to create a share.

---

### Post by Raptor45 on 2008-04-28
I think it may be related to a known issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/175689](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs/+bug/175689)

Samba has all kinds of permissions issues with gvfs it seems. No word on a real fix yet, but there are several workarounds.

---

### Post by brommage on 2008-04-28
I had a similar problem.  I'd like to hear the possible solutions.

---

### Post by Brian R. on 2008-05-16
> **brommage said:**
> I had a similar problem.  I'd like to hear the possible solutions.
I have solved my problem with windows not seeing ubuntu. The problem is in the Samba Config file, you have to edit it.

---

### Post by Sleaka J on 2008-05-16
I just added the current user sharing the folder to the group "samba" (Or something similar. It will exist if you've installed Samba). Log out, log in. Problem solved.

---

