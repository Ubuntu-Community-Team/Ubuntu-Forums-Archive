---
title: "recovering old files after install"
date: 2015-07-01
forum: General Help
---

### Post by kurja on 2015-07-01
I set out to install 14.04 on a machine with a totally borked win7 install on it, and botched the transfer of user's files. I simply put the hdd in a working box and dragged the user's folders into a portable usb drive, then put the hdd back and installed ubuntu on it and all was well until I plugged in the portable drive to put the user's files in there - and one of the backed-up folders turned out to be a symlink to the relevant folder which obviously no longer exist. Uh Oh. Thankfully almost all data is backed up elsewhere, it's just this one folder that was lost, so I'll live but anyway I tried to salvage the situation, here's what I've done:

Using testdisk I sought for an ntsf partition on the drive, and with 'deeper search' two were found. Testdisk can't show any files in either; "File System appears to have been damaged." I chose to write the partition structure to the disk, not because I would have really understood how that will help but because it sounded like it might. Rebooted.

Disk is now showing unallocated space instead of an ntsf partition like I would have expected. With photorec I pulled out files from the disk, and ofc all of that is a disorganized mess of huge number of files in a recovery folder.

Any tips on what else I could try? Is there anything that could possibly be done to search for files that were in a specific folder in a file system that doesn't really exist anymore?

---

### Post by dragonfly41 on 2015-07-01
I take it that the user files you refer to were Win7 files?

First point I would raise is that recovering Windows files is probably best left to native Windows recovery programs rather than Linux.

So you would need to remove your hdd and put it into an external container to be inspected from another Windows computer.

Then search this forum for suggestions on windows recovery packages to use.
I can remember using GetData / RecoverMyfiles but there are others mentioned in this forum. 

Whatever package you use try the evaluation version first to check that your files can be recovered before taking the step of purchasing a licence.

If you want to use the free TestDisk / Photorec then you will have random names for files.

Assuming that you have text rather than images to recover if you can remember some keywords in your lost files you can use packages such as SearchMonkey to scan through these randomly named files to find any matches.

Scanning through images is more difficult.  This involves searching metadata.

---

### Post by kurja on 2015-07-01
Thanks for the advice. I do not have a windows machine here that I could use unfortunately, and the files are of various types (jpegs, office docs etc).

---

### Post by Vladlenin5000 on 2015-07-01
There aren't great chances of recovery to start with - the Ubuntu installation probably re-wrote the most part of the area where your personal files once were as part of a Windows partition. Needless to say the more you use your newly installed Ubuntu the more is written and the chances of recovery decrease substantially.

Whatever you do, whatever you decide to use as a recovery tool, make sure it boots from live media (CD/DVD, USB) if you can't remove that disk and connect it in a Windows PC, as suggested. You can use a USB drive to save the recovered data.
[URL="http://www.proyectobyte.com/hirens-boot-2/hirens-boot-cd-15-2-usb-2014-everything-one-cd?lang=en"]
Hirens Boot CD[/URL] - can also be use in a thumb drive - comes with several tools. There are many other options.

---

### Post by dragonfly41 on 2015-07-01
If you are stuck with photorec then remember that the default option is to recover ***all*** file formats.

So you might narrow down the options by running multiple passes of photorec (one run for each file type).

[Search] [Options] [File Opt] [Quit]

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

run1 .. Set Options to only .doc
run2 .. Set Options to only .docx
run3 .. Set Options to only .jpg

etc. for all your file types.

And remember to save recovered files to an external USB drive or you are at risk of overwriting the areas you are trying to recover.  
So photo rec running in a LiveUSB might be the safest option.

---

### Post by kurja on 2015-07-01
I am obviously not booting with/using the problem drive, like I said it now has just unallocated space on it now and I plugged it back in to my working box as /sdb.

I suppose I'm just going to move the files photorec recovered into /jpeg and /doc folders and try to sort out any useful stuff, then call it a day and a lesson learned about double checking backups before reinstalling an os.

---

