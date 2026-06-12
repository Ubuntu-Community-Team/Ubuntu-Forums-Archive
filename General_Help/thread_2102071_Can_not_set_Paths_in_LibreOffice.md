---
title: "Can not set Paths in LibreOffice"
date: 2013-01-06
forum: General Help
---

### Post by Onesimus on 2013-01-06
Hi,

I have recently installed Ubuntu 12.10, and am using LibreOffice 3.6.2.2, and I am trying to attempt to set particular paths in LibreOffice, more specifically:

the Directory Path to my Templates, 
(Tools->Options->LibreOffice->Paths)

and also the paths for trusted Sources for Macros (Tools->Options->LibreOffice->Security->Macro Security->Trusted Sources.  

Neither of which appear to work.  They don't set the selected path, but merely my home directory.

Can anyone else replicate this behaviour and offer a workaround.

---

### Post by Quarkrad on 2013-01-06
I had this the other day - apparently there is a bug in libreoffice, not 12.10.  I found this on google - [https://bbs.archlinux.org/viewtopic.php?pid=1209114](https://bbs.archlinux.org/viewtopic.php?pid=1209114).  I did not follow this exactly - I remember deleting everything libreoffice' via Synaptic and then reinstalling just Writter and Calc.  With just these two installed you can set the path (it works!) and then reinstall the rest.

---

### Post by fantab on 2013-01-06
That is strange! in my 12.04 it is working. Its only in the later versions of '**libreoffice-gnome**' package that I was faced with this issue. 

@Onesimus:- Try removing the package '**libreoffice-gnome**' using Synaptic and reset the default save path. If it works then reinstall the above package.

---

### Post by Onesimus on 2013-01-06
> **fantab said:**
> That is strange! in my 12.04 it is working. Its only in the later versions of '**libreoffice-gnome**' package that I was faced with this issue. 

@Onesimus:- Try removing the package '**libreoffice-gnome**' using Synaptic and reset the default save path. If it works then reinstall the above package.

@fantab
I tried your suggestion, but it makes no difference.

@Quarkrad
I have stopped short of totally removing libreoffice, and re-installing it writer and calc - changing the paths.  Then re-installing the rest, only to have a system that produces the same bug.

---

### Post by fantab on 2013-01-06
> **Onesimus said:**
> @fantab
I tried your suggestion, but it makes no difference.

@Quarkrad
I have stopped short of totally removing libreoffice, and re-installing it writer and calc - changing the paths.  Then re-installing the rest, only to have a system that produces the same bug.

Okay, I just noticed... My bad... 
You have to also remove libreoffice from /home/USER/.config/libreoffice delete the folder... it stores your user customizations and deleting this will remove the earlier set defaults.

Remove ~/.config/libreoffice and remove libreoffice-gnome... set your default path and reinstall libreoffice-gnome. It should work.

Edit: If you want to reset the path again then you may have to repeat the workaround... the bug isn't fixed yet.

---

### Post by Quarkrad on 2013-01-06
I've just re done everything and can confirm the last post. You must remove libreoffice-gnome and ~/.config/libreoffice first.  Reset the path to where you want and then reinstall these two files.  I have a step by step process of what I did but the last post explains.

---

### Post by Onesimus on 2013-01-08
Thanks for all the suggestions (unfortunately, none of them fixed my issue).

I have now decided to downgrade from 12.10 to 12.04.

It wasn't just this issue, but I have had display issues with 12.10 every 5 minutes requiring me to logout and log back in again.

---

### Post by sup on 2013-03-03
Corresponding bug: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1070891](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1070891)

---

