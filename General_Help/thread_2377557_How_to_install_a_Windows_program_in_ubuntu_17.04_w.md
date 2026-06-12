---
title: "How to install a Windows program in ubuntu 17.04 with dosbox"
date: 2017-11-14
forum: General Help
---

### Post by seekertom on 2017-11-14
I've had good luck running old dos programs in dosbox, but these have been non-install programs, so just copying the files to a suitable folder and running works fine.

But now I have a windows program, Print Shop 23 that I'd like to try under Ubuntu 17.04. But it is installed from its cd, and I'm not sure how to begin to install it.

For example, do I try to do it from within dosbox environment, use a linux installer, or what?

Please guide me, Oh great ones!
thanx st
):P

your help got me where I needed to be. thanks. I'm exploring replacements for my win progs, but I have so much existing data that I need access to, it is difficult. will keep searching. thanks st

---

### Post by monkeybrain20122 on 2017-11-14
Use wine?

---

### Post by HermanAB on 2017-11-15
Uhmmm...  DOSbox cannot run Windows programs - the name should be a clue.  

WINE or a virtualizer with a full install of some version of Windows are the other options.

---

### Post by mastablasta on 2017-11-15
DOS programs are installed just as they would in DOS. so run dosbox, mount the drive and run install.

windows programs are another matter. some might work in wine (or you can use playonlinux as GUI for wine). 
if this is the one: [http://www.broderbund.com/p-145-the-print-shop-231-deluxe.aspx](http://www.broderbund.com/p-145-the-print-shop-231-deluxe.aspx)
 you could only try to run it in wine.

however, if we are talking about this desktop publishing program then i suggest you try Scribus as alternative. IMO Scribus is excelent. i think it is in software center, but they also have a PPA for latest and other versions.
[https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

some people like to live on the edge.

Libre Office Draw is also an option to use.

---

### Post by coldraven on 2017-11-15
At WineHQ they have a rating system for Windows applications. It goes from Platinum (good) to Bronze (not very good). The results for Print Shop Deluxe are here:
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=384](https://appdb.winehq.org/objectManager.php?sClass=application&iId=384)

You could install Wine but you might be wasting your time. Look in the Software Centre for Wine and/or Play on Linux.

---

### Post by Yellow Pasque on 2017-11-15
Wine or run Windows in a VM, unless it's a Windows 3.x program (and you have Windows 3.x installed in dosbox).

---

