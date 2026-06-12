---
title: "Repair Corrupt Archives? Any Ubuntu/Linux ZIP &amp; RAR Repair Tools??"
date: 2008-06-24
forum: General Help
---

### Post by OzzyFrank on 2008-06-24
Hi. In my Windows programs (WinZip and WinRAR) you not only have the option to test the integrity of compressed archives, but also repair them if need be. If you can't do it with a right-click (ie: the option is in the context menu), you can do so from a menu once the program is open.

So far from what I have seen in Ubuntu, none of them have the repair option, which kind of strikes me as odd as well as disappointing. Now, I have tried to find and install other programs, but so far all are lucky to even have the test integrity function. So what programs out there do have a repair function? I don't mind getting separate apps for .zip and .rar files if need be. I just hate admitting defeat and booting into Windows just to repair some archives, hehe. Thanks

---

### Post by gardara on 2008-08-14
Winrar runs perfectly with wine, I have repaired some archives that way...
But however I have to agree that it's really strange that this isn't supported by the linux unrar...

---

### Post by SpongeMan on 2010-09-16
the repair option is available using rar see [here]("http://manpages.ubuntu.com/manpages/lucid/man1/rar.1.html"), I hope that helps 
some one as I  found this thread looking for this info too, 
unlike unrar rar is shareware

---

### Post by birkopf on 2012-03-03
> **OzzyFrank said:**
> Hi. In my Windows programs (WinZip and WinRAR) you not only have the option to test the integrity of compressed archives, but also repair them if need be. If you can't do it with a right-click (ie: the option is in the context menu), you can do so from a menu once the program is open.

So far from what I have seen in Ubuntu, none of them have the repair option, which kind of strikes me as odd as well as disappointing. Now, I have tried to find and install other programs, but so far all are lucky to even have the test integrity function. So what programs out there do have a repair function? I don't mind getting separate apps for .zip and .rar files if need be. I just hate admitting defeat and booting into Windows just to repair some archives, hehe. Thanks


Most of additional options under Linux are available from command line. 

For rar archives you already have answer below. To fix .zip archive the option will be -F (upper case and lower case is important). If this wouldn't do the trick try -FF. 

Normally you structure command like below:

zip (or unzip, or rar, or tar... and so on) currupted.zip -F fixed.zip

afterwards you will have new file called fixed.zip
you can extract this file normally by right click...

I just noticed that not all of the file archiving under windows is compatibile under linux. When I was trying to extract password protected .zip file under ubuntu and it was returning error. Extracting the same file by winrar under windows went without trouble. 

Before trying to fix corrupted archives good thing is to try to extract it under windows or mac os with some native packer/unpacker. 

Hope this helps.

---

