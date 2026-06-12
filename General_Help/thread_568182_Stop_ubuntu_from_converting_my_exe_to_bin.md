---
title: "Stop ubuntu from converting my exe to bin"
date: 2007-10-05
forum: General Help
---

### Post by twoleggedman on 2007-10-05
I have three partitions on my 80 gig laptop hardrive, ubuntu a exfs, storage as fat32 and windows as ntfs.  My windows install never seems to be able to download large files, about half way through the connection always seems to stall, so I use my ubuntu install to download large install files for windows to my storage partition where both OSs can read. 

For some reason Ubuntu seems to be insisting that every .exe file d/l is a bin file, and will name it approprietly. When I try to open the file in Windows, it does not recognize it, and will not let me change the extension.


what do I do ? Anyone else run into a problem like this?



Thanks

---

### Post by brydonhunter on 2007-10-05
I have never seen this happen. Which browser are you using to download the file. Perhaps you have a hardware, network card, problem. If you crash in Windows and the download "seems" corrupt....

Are you booting Windows to install this file? Which partition are you saving these files to? Any detail you can give will help us help you.

---

### Post by twoleggedman on 2007-10-05
In this case the file im downloading is a patch for Americas army. I have an ati 200m and it ran like crap in ubuntu.

Im using mozilla firefox to browse, and the file I am saving onto my storage partition, which is fat32, so its accesible from both my ubuntu and windows install. Ive had this problem with my windows wireless drivers for a while, where I can not download large files other than torrents with out the d/l timing out. I have reinstalled my windows partition a bunch of times, tried diffrent wireless drivers, tried my router in a bunch of diffrent configurations, and still to no avail, the d/l's never make it, and never a stop at the same spot. Interestingly enough I use the exact same drivers with my ubuntu install with ndiswrapper (bcm4319) and everything always works great.

In anycase, I digress. The problem from before was that I cannot seem to d/l an .exe file in ubuntu with firefox with out it saving it as a bin file. It doesnt not give me the option to save it as anything but a .bin file no matter where I save it (to a linux partition or not)

is this just firefox? Is there a way other than renaming that will let me change it to an .exe? Cause renaming it just makes it a .exe.bin 


Thanks in advance

---

### Post by GavinZac on 2007-10-05
:/ firefox doesnt behave like that for me, as I've been downloading a few .exe's in order to run with Wine.

---

### Post by shad0w_walker on 2007-10-05
Firefox shouldn't be doing that, I have no troubles downloading exe files (Have to do it from time to time for the family) 

I don't have a clue what exactly is causing this behavior but until things get sorted out might i suggest you have a look in the repos for a download manager? It's not the most integrated way of doing things but it should do fine until a solution is fine.

---

### Post by GavinZac on 2007-10-05
the DownThemAll extension for firefox works as a good integrated download manager.

---

### Post by blackaardvark on 2007-10-08
Well I've just ran into the same problem. Windows drivers being saved as ".exe.bin" extension. You're not alone is all I can say.

---

### Post by twoleggedman on 2007-10-19
black aardvark


In windows it turned out to be  a pretty simple solution: turning on file extensions in the folder options, and than renaming the extension.....in this case deleting the .bin

Still not sure why this was doing this, but now I've just wiped and installed gutsy, so we'll see if it does it in 7.10

---

### Post by mahousaru on 2007-10-19
I had this problem a while back and mine was caused by writing to a directory that sets files to executable by default, eg fat32 volumes or mounting samba shares without the right flags.

FF will detect that the file is executable when it renames it from .part, and then it will add the bin extension too.  Bleeping annoying, its something that has been logged on the Mozilla site, but I am not too sure what they have done with it.

---

### Post by oaksterdam on 2007-10-19
i'm having the same problem (new fiesty install, firefox 2.0, fat32 file system).

mahousaru - could you post a link to the mozilla blog where this is discussed?  i haven't been able to find anything else on the subject other than this (and your response was very helpful - thanks).

---

### Post by mahousaru on 2007-10-19
*scratches head*

I think I am going mad as I can't seem to find any references of it... 

It wasn't that long ago and I was using Ubuntu 7.04 and mounting a samba share to an OpenSuSE 10.2 server, to get around the issue of FF and TB not being able to save to gnome network shares.  I noticed that my files such as mp3 were being renamed to mp3.mp3, zip files to zip.zip and exe to exe.bin.

After hunting around a bit I swear it was on the mozilla site logged as a bug, but in their case it was saving to fat drives, as files needs to be set to executable for some reason.  This led me to remount my shares using the file_mode=0640 which solved the problem for me.

I've tried saving to a fat usb drive with gutsy and it saves the file with the correct extension, but I have noticed that it does not save it with the executable flag (rw on user).  The disk is correctly mounted with a umask of 077 and when I create a file manually it is created as rwx on user.  So me thinks that gutsy ff is doing something funky with file rights when it saves.  When I save the same file using opera to the disk it has the correct rights of rwx. 

I've just re-installed my vmware box to ubuntu and need to rebuild vmware, so I can't test in 7.04 to reproduce the problem atm.  I'm off on the razz so won't be able to play with it until tomorrow.  

I'll keep looking for the bug report as this is really irking me now...

*Edit*
It might have been an launch pad bug report...

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77788](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77788)

I think I am going senile with old age, oh well at least beer is meant to improve memory now

---

