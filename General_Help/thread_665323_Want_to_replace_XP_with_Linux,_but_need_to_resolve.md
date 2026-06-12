---
title: "Want to replace XP with Linux, but need to resolve initial problems"
date: 2008-01-12
forum: General Help
---

### Post by bumcheekcity on 2008-01-12
Hi all. I've been using Linux on and off for about 2 years now, and I've been wanting to make the switch on my main machine for ages, but there are still some little things bothering me, that I need resolved if I'm going to make the final move. 

1) I have a Gun for the PC, it's a little USB one, and it works fantastically, just install the little driver program, plug in the gun, and play, it's the WinGun driver, and it's for XP only (not even Vista), and obviosly not for Linux. Does anyone know of a port of that program, or if I could run it in WINE or something?
1b) Failing that, I would be happy yto run House of the Dead in VMWare, if I could use the USB controller in VMWare. Can I do that?

2) Office 2007 stuff will get passed to me a lot through my work. I can use OpenOffice, of course, with 2003 and older documents, but is there anything that will reliably 100% open and/or save as Office 2007 docx, etc. format.

3) Which version of Microsoft Office works in WINE? There are a few (and far between) occasions when OpenOffice doesnt QUITE correctly render some of the more complex weord docs, and it'll die before it opens a 50MB spreadsheet, and yes I do get some of those through. 

4) Networking with Windows XP. This is quite a big one. When I installed some Ubuntu releases previously (7.04 and 7.10), I went to browse my network shares, which loaded OK, and some of the folders, Ubuntu just didn't access. It listed "Movies", "TV" and "Games" for instance, but I could only access "TV", the other two folders were as if they were fake folders or something. It's kind of hard to explain, but if anyone has had this error, they'll know what that means. 

5) If anyone's uses PSPad, then what's the best program to replace it in Linux?

---

### Post by bluesrocker on 2008-01-12
Hi There. Try abiword. Anything you write on Microsoft office, can be saved and open with Abiword. Now, if you saved a document with abiword, and you try to open it with Microsoft Office, office won't read it unless, you right click on it and choose open with... Microsoft Office. Good luck.:guitar:

---

### Post by danwood76 on 2008-01-12
With regards to office2007 stuff, novell do a plugin for open office (it works with all versions not just the novell version) which allows you to open and save all office 2007 documents.

You have to install gnome-vfs from the repositories to get the gnome networking to function 100% correctly with windows shares.

regards,
Danny

---

### Post by hardyn on 2008-01-12
dual boot?

1) i think you are going to have to try it, i would not hold my breath on it working however
2) nope... i would say about 90%.  obviously the less formatting there is the better, but heavily formatted documents will experience trouble; installing the ms-fonts will be required to even have a fighting chance.
3) try gnumeric plays MUCH MUCH better with excel than OOo calc does!
4) i have had trouble with it as well, XP networks much better than vista.  I had trouble with speed more than anything doing this.

look into the dual boot thing, may help keep you working until you know the migration with be successful.

---

