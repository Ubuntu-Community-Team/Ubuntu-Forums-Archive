---
title: "Poor OOO 2.4 GVFS SMB Interaction?"
date: 2008-05-06
forum: General Help
---

### Post by yogensha on 2008-05-06
When I try and open a spreadsheet on an GVFS mounted SMB share, OOO prompts for credentials.  It shouldn't, since GVFS is already providing access.  I can't provide the proper credentials, because OOO assumes the workgroup is 'MSHOME', and doesn't allow me to change it.

I also tried browsing to the file in the File|Open dialog, but get the same results.  Suggestions?

---

### Post by yogensha on 2008-06-30
I hoped some future update would clear this, but it's still kicking my butt.  Anybody else seen this?

---

### Post by danwood76 on 2008-06-30
You might be able to change the workgroup in the smb.conf file located:
/etc/samba/smb.conf I think the default is workgroup though which most people use anyway.

GVFS is a bit weak at the moment, I have problems even browsing my network at home so I end up having to type smb://IP/Share to get my shares but once they are mounted they run perfectly.

Hopefully with the update in a week or so there will be an improvement in this, though I dont hold my breath.

---

### Post by yogensha on 2008-06-30
GVFS in general seems stable and functional to me.  It really looks like OOO isn't GVFS aware in Ubuntu.

I have to punch in a URL as well, which doesn't bother me so much because it mounts it on the desktop after I've been there once and it sticks until the end of the session, which is usually a few weeks long for me.

Having to work on a local copy is a huge hassle though because I don't get the benefits of file locking and such.

Changing the default workgroup should help alot though, thanks for the tip!

---

### Post by leemid on 2008-06-30
I agree, OO.o and GVFS don't play nicely - OO.o had no trouble with Gutsy. Every time I open ODF documents from a Samba share in Ubuntu I corrupt them, and the repair function doesn't do the trick. So then I have to repair them from Windows before they'll work again.

Annoying. :(

---

