---
title: "DVDFab Decrypter 3.0.7.2 works on Dapper"
date: 2007-02-03
forum: General Help
---

### Post by wargames on 2007-02-03
I just updated my wine installation to Wine 0.9.30 and then tried DVDFab Decrypter 3.0.7.2 and was able to rip a dual layer dvd movie successfully in about 20-25 minutes. In the past, with a earlier version of DVDFab Decrypter 2.9.x would result in garbage VOB files with green artifacts. But the newest version 3.0.7.2 has been totally rewritten with a new design and interface and worked great on my Dapper installation.

I got DVDFab Decrypter 3.0.7.2 from softpedia.com:
[http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVDFab-Decrypter.shtml](http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVDFab-Decrypter.shtml)

And I installed Wine 0.9.30 using the WineHQ respository of:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

added to the end of my /etc/apt/sources.list using the Wine installation instructions from the wiki:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I also used VobBlanker 2.1.2.0 successfully using this new Wine 0.9.30 as well.
You can download VobBlanker from here:
[http://www.afterdawn.com/software/video_software/dvd_tools/vobblanker.cfm?view=all](http://www.afterdawn.com/software/video_software/dvd_tools/vobblanker.cfm?view=all)

There's a new VobBlanker 2.1.30 beta out but I have not tried it yet since it was still in beta form.

I used the "winecfg" to set both DVDFab and VobBlanker to run as if under Windows XP in the Wine configuration screen.

Anyway, I hope others try the new Wine and DVDFab Decrypter on your systems and tell us if it worked ok. Try to backup different DVD's to help verify that it works. Hope this helps you to backup your DVD's.

---

### Post by carusoswi on 2007-07-06
What is VOB Blanker?

Caruso

---

### Post by carusoswi on 2007-07-07
> **wargames said:**
> 
Anyway, I hope others try the new Wine and DVDFab Decrypter on your systems and tell us if it worked ok. Try to backup different DVD's to help verify that it works. Hope this helps you to backup your DVD's.

I downloaded/installed DVDFABHDDecrypter on my 7.04 installation under Crossover.  It appears to function in identical fashion to my DVDFabDecrypter installation on XPSP2, but, the output is overrun with artifacts and is not viewable.  What do you think is causing that problem?

Also, I pointed the output to a large NTFS partition on my slave drive, but think that should not affect the output.  Do you agree?  FWIW, I am testing on both OS's using the same disks.  The file sizes are identical.  The XP output plays fine in VLC, the Ubuntu output is garbage.  I'm going to boot back into XP to see if the Ubuntu output will play from XP.

Any suggestions appreciated.

Caruso

---

