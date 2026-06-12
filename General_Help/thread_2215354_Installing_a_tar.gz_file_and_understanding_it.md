---
title: "Installing a tar.gz file and understanding it"
date: 2014-04-06
forum: General Help
---

### Post by gilloz on 2014-04-06
I've used my old computer with Windows XP and dual boot with Ubuntu 8.04 to start.  I never seriously worked at understanding Linux until now, since Windows XP is at it's End of Life.  A week ago I cleaned up my hard drive complete and installed Ubuntu 12.04 LTS  only.  A regular Live disc would not installed properly so I used the Alternate disc.  I am at a point with Ubuntu in that I am trying to understand how to load a file as oppose to just using the Ubuntu Software Center.  The file is a tar.gz file.  What I have found on this forum is not clear to me.  I have downloaded the file and I have extracted the data which went into a folder.  So, on my desktop I have two items, the downloaded file and a folder with the extracted data.  Here is where I am stuck.  The installation instructions in the Readme file only say to copy and save the data in the "appropriate place".  So my question is, where is this appropriate place?  I'm assuming they mean in one of the System File folders, but which one?  As you can see, this is where I am stuck.  So, if anyone can lead me past this spot I would appreciate it or give me a good link that will give me this information.  I'm determine to get this done and understand what I am doing, with someone's help, of course.  Thanks

---

### Post by Lars Noodén on 2014-04-06
Which application is it?  Can you link to the instructions here?  Also, the program might be in a PPA if it is not available in the repositories.  As always, it is much, much easier to install and maintain if you can get the program from the repositories or from a PPA.  Installing from a tarball is really last resort.

---

### Post by oldos2er on 2014-04-06
Moved to General Help.

---

### Post by Impavidus on 2014-04-06
In case of a .tar.gz, there are no rules. Try to find a readme or install file in the archive. Else find out what kind of files are in the archive. An executable? Source code? In general, stuff installed from a tarball belongs in either your home directory (~/bin) or, if you install system wide, somewhere in /usr/local/.

---

