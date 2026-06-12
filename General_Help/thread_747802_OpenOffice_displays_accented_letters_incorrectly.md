---
title: "OpenOffice displays accented letters incorrectly"
date: 2008-04-06
forum: General Help
---

### Post by pytheas22 on 2008-04-06
My language is English-US and my keyboard layout is en-international with deadkeys.  Lately I've had a problem in OpenOffice where certain accented letters are displayed improperly.  For example, when I type "Bärwalde," it looks like "B%rwalde."  I have similar issues with the character é, which looks like È inside OO.  Interestingly, if I copy and paste the malformed text into a text editor, it displays properly.  It also prints things correctly on paper or to pdf, although words with the characters in question look sort of weird, as if the ä or é is separated from neighboring characters by a wider space than usual.

I've tried pasting the text into new OO documents and restarting the application and computer; nothing helps.  This problem just started recently--I used to be able to type accented characters with no problem.  So I am assuming this is some kind of bug.  It's not the end of the world, since, as I said, the document still looks mostly normal with the exception of some extra spacing around the accented characters.  But I would prefer it to look perfectly normal if possible, as I need to print off some important work pretty soon.  I thought about bringing this to a Windows machine to see if Word can solve the problem, but I would really prefer not to do that if possible.  Any suggestions?

---

### Post by scramasax on 2008-04-07
> **pytheas22 said:**
> My language is English-US and my keyboard layout is en-international with deadkeys.  Lately I've had a problem in OpenOffice where certain accented letters are displayed improperly. ...  Any suggestions?

How if you insert the letters in question from the Character Map (Applications > Accessories > Character Map)?  Does the same thing happen, or not?

---

### Post by pytheas22 on 2008-04-07
What are your keyboard and language layouts, and which build of OO are you using?  I've got 1:2.3.0-1ubuntu5.3.

---

### Post by pytheas22 on 2008-04-07
> How if you insert the letters in question from the Character Map (Applications > Accessories > Character Map)? Does the same thing happen, or not?

Yes, but only with ä ... é seems to be working alright now (it wasn't the other day), as do all of the other characters.

---

### Post by pytheas22 on 2008-04-07
Also it looks like someone else has already filed a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/191292](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/191292) .  Unfortunately no one has a solution other than upgrade to Hardy, which won't be out before I need to print my history thesis!

---

### Post by pytheas22 on 2008-04-07
As an update, here are some more observations:

-when I created a pdf from my document using the create pdf function inside OO, none of the quotation marks or dashes (i.e. - ) were printed--there was just blank space where they should have been.  But "Bärwalde" looked ok.

-when I created a pdf by printing to my pdf printer, everything was displayed correctly, excepted the "Bärwalde" looked like "B%rwalde" in the pdf.

-I booted to a Hardy beta CD inside a virtual machine and opened the document there, and it was fine.  All characters were displayed properly inside OO, and I could create a pdf from within OO that also looked fine.  I guess this is a work-around solution for me, so the issue is essentially solved--although it is possible that the problem doesn't exist in the live CD environment because the system configuration settings are not the same as the ones on my real system, so I'd be interested in knowing if the problem is caused by my version of OO itself or other system settings (keyboard, language...). 

EDIT: I got some time and decided to upgrade OO using the Hardy repository (it's not as hard to enable this as I thought), so I wanted to confirm that the problems disappear in the upgraded version.  I think this is worth noting, since it indicates that the problem did not lie with my keyboard layout, language settings or any other system settings; instead it appeared to be related to OO itself.

---

