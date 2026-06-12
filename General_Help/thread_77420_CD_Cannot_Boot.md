---
title: "CD Cannot Boot"
date: 2005-10-16
forum: General Help
---

### Post by deat on 2005-10-16
I'm not sure where else to put this.

I downloaded the 'PC (Intel x86) install CD' from - [http://us.releases.ubuntu.com/releases/kubuntu/breezy/](http://us.releases.ubuntu.com/releases/kubuntu/breezy/)
then I burned it onto a CD-R using Roxio. I burned it as a data cd, then attempted to boot my computer using the CD. Even with my computer set up to boot from CD-ROM first, it still boots into my current operating system - Windows XP.

Has this problem been brought up before? If so, how would I go about rectifying this problem so that I can boot Kubuntu from the CD, and install it?

Thanks in advance,
Deat

---

### Post by Saarg on 2005-10-16
The reason why you can not boot from the CD is that you burned it as a data CD. I don't know Roxio but there should be an option to "Burn image". When you find that option you choose the ISO file you download when Roxio asks for it.
You can verify that you burned it wrong by going to windows and look if there is just one file called "kubuntu-5.10-install-i386.iso" on the cd.
If you have directories and files there is some other problem.

---

### Post by snpz on 2005-10-17
U burned this .iso image incorrectly!
I think that Roxio also have an option like "Burn image". U have to select this option (Not "make data CD") and mark where this image is located. After burn process u should be able to boot from this CD!

---

### Post by RasRedox on 2005-10-18
Having just done this successfully, let me suggest trying this:

Put a blank CD in the burner.  (If asked, pick "take no action")
Right click on the .iso image (if Roxio easy CD Creator is installed it should be associated with .iso filenames)
Pick Send to CD from the menu. (The top selection for me)
When CDCreator opens, it will detect the .iso filename and prepare to "burn an iso image"  There should be a Burn CD button.
I wish you luck.  Worked for me.

RasRedox

---

### Post by Princey on 2005-10-20
By default, when you install Roxio, it automatically takes up the iso extension. All you have to do is double click on the iso file and with a blank CD in the burner, click burn image on the dialogue box that comes up. If that's not the case, open roxio easy cd creator, chose burn image file from the menu, locate where the iso is downloaded and that should do the trick.

Good luck.

---

