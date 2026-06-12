---
title: "designworkshop software installation"
date: 2007-02-26
forum: General Help
---

### Post by kankana on 2007-02-26
hi all
i hav downloaded an exe file which is DesignWorkshop_Lite-Win.exe i want to install it in wine how to do it plz help

---

### Post by jonnymccullagh on 2007-02-26
Have you installed wine? (you can use Automatix for this).
Have you run: winecfg in a terminal?
if so you should run your executable from the command line using:
wine DesignWorkshop_Lite-Win.exe
That should run the installer.

---

### Post by Olav on 2007-02-26
> **jonnymccullagh said:**
> Have you installed wine? (you can use Automatix for this).
Have you run: winecfg in a terminal?
if so you should run your executable from the command line using:
wine DesignWorkshop_Lite-Win.exe
That should run the installer.
Well, yes, that COULD work. It does with many Windows programs. No guarantees though, and "no batteries included" (meaning, if it doesn't work prepare to solve some of your own problems). This seems to suggest that you may be lucky with your Designer program though: [http://appdb.winehq.org/appview.php?iVersionId=4900](http://appdb.winehq.org/appview.php?iVersionId=4900)

I am using many different Windows programs on Linux every day. Then again I do it in a virtual machine by the name of VMware. There are freeware packages of that available. Another good one is the recently open sourced VirtualBox. 

What all these programs do is create a virtual machine for you in your computer's memory, on which you can install Windows, on which you can install your Windows applications.

Absolutely nothing wrong with QEMU either, but it still needs a little tinkering to get it up to speed. You won't mind if you are a developer or IS type of person, but you would if you just need an easy way to use a Designer program or something.

---

