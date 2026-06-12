---
title: "[SOLVED] F-Spot runs out of memory when importing photos"
date: 2008-02-11
forum: General Help
---

### Post by rockin_goliath on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/190855](https://bugs.launchpad.net/ubuntu/+bug/190855) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Whenever I try to import photos into F-spot from a location on my hard disk, F-spot starts occupying 2.5 gb of system memory. I am using Ubuntu Gutsy 7.10 and F-spot version 0.4.0ubuntu3. F-spot returns the message "Import Error. Error importing /path/to/file.jpg. Out of memory." This happens when I use the import option from the File menu or simply drag and drop from the file browser, but NOT when I import from a digital camera. I was not having this problem the last time I imported photos on Dec 17, 2007. I do not have the option in Synaptic Package Manager to force a previous version, so I assume that the F-spot package itself has not been updated. I have also read on various forums (dated several months ago) that libEXIF could cause "memory leaks" but that package also did not have the option to force version. Could it be possible that a package that was updated after Dec 17 that F-spot depends on could be causing this problem?

I filed a bug at launchpad: [https://bugs.launchpad.net/ubuntu/+bug/190855]("https://bugs.launchpad.net/ubuntu/+bug/190855")

---

### Post by tich on 2008-02-11
i have similar problems with f-spot.  importing pictures almost stops my computer.  and i have no problem editing large video or audio files so importing pictures shouldn't be too problematic!
i don't think it is related to any sort of upgrade it has been doing it on my computers (2) since dapper or maybe even breezy.

i never really thought too much about it because i don't import or look at photos all that often and deep down i just assumed it was some sort of problem with my system.  

 this response probably isn't too helpful  but misery loves company, i guess. or something.

---

### Post by rockin_goliath on 2008-02-11
I just tried some tests, and I do not get the same error in my guest account. Granted, my main account has 4000+ photos and the guest has none, but it nevertheless indicates something that happens of a per user basis. Could this be a database corruption issue? Man it would suck to rebuild the tags of 4500 photos :(

---

### Post by rockin_goliath on 2008-02-12
[SOLUTION] I just realized that the pictures were actually corrupted, but subtly enough were I didn't notice it when I opened them in any other image viewer. I realized this when I found that F-spot would import photos download from the internet just fine, but not the ones I wanted to. I opened all the pictures in gThumb, and used the batch convert function to put them into a new directory, but keep them in jpg format at 100% quality. After that they imported in F-spot perfectly!

---

### Post by villindesign on 2008-02-12
Also related to this issue, I had an import problem with F-Spot when I tried to import a folder containing thousands of pictures. FSpot would give the same error message. I found a text file in one of the folders, and that was the cause. After I deleted all non-pictures from the folder, F-Spot imported without a problem.

---

### Post by apetresc on 2008-02-12
This still should be filed as a bug report against F-Spot. The current behaviour is too fragile, and the error returned is far from intuitive.

---

