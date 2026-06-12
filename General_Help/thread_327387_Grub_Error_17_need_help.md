---
title: "Grub Error 17 need help"
date: 2006-12-29
forum: General Help
---

### Post by Smokin715 on 2006-12-29
I apologize if this may have been posted, I have spent hours searching for a answer.  1st I have(had) a dual boot xp/ubuntu system.  Recently I have been running out of disk space and really needed the space from my linux partition.  I found that I could reclaim that space by reformatting that partition through the disk management tool in windows, and that I would need a boot disk to fix the mbr.  Well I reformatted that partition, created a boot disk with windows on a floppy.  Reboot my pc with the floppy in and bam! it doesn't read the floppy I/O error.  So I reboot and find that grub gives me error 17, no longer able to boot into windows.  Been searching all night for a way to  either fix the mbr (without the windows xp disk, i don't have it anymore) or repair grub from the live ubuntu cd.  So far all I can tell is to reinstall grub I have to have ubuntu installed on one of my partitions, which is the opposite of what I am trying to do.  Is there an easy way to install the grub straight from the live cd?  Downloading isn't an option since I'm using the live cd just to find answers, I can't burn anything to cd's or floppy's.  Is there some way I can change the mbr, say through some setup feature similar to pressing F11?  Had I known erasing that partition would screw booting up to windows I would have left it alone for now.  Can someone Please Help me?  Thanks in advance to whoever helps me out.

---

### Post by Smokin715 on 2006-12-29
Well I don't feel like waiting till tomorrow for a response, so here's what I'm gonna do.  Since I only have 1 hard drive and it has 2 partitions, both ntfs, since I reformatted earlier.  I am going to install ubuntu onto the 2nd partition and give it a much smaller partition, just enough for it to run in case I ever need a back up OS again.  Maybe this will fix my grub error and all will be well, since it will be reinstalled.........Or I'm about to make it worse!!!  Oh well, trial and error, can't learn if I don't try.  I usually can fix anything with windows, but linux (for me) is like learning latin, and I'm not very multilingual.  But hey if you know how to fix my problem let me know, I'll be checking back for answers provided I can get back on after the install.

---

### Post by usien on 2006-12-29
reinstalling ubuntu will get bak grub i think.it seems that modifying partitions out of ubuntu seems to make grub angry and i also got error 17 nd no body seems to hav an answer 2 it, so it seems i hav 2 reinstall my ubuntu too.

---

### Post by Smokin715 on 2006-12-29
Yeah I just finished reinstalling, on windows now!  Only thing was I got the partition sizing backwards.  Ended up giving most of that partition to ubuntu when I meant to give most of it back to windows!  But reinstalling fixed the error, brought back the grub just the way it was supposed to be with a fresh install.  Now to go through all that again.  I need my space back!](*,) :evil:

---

### Post by louieb on 2006-12-29
For future reference try [http://bootdisk.com/](http://bootdisk.com/) I believe you can find a floppy image there  to fix the mbr to boot windows.

---

### Post by Smokin715 on 2006-12-29
Oh well, so much for trying to redo it again.  Tried reformatting the fat partition from windows disk management, and the program starting bugging out, all of a sudden it told me I had 600+ gigs on the fat partition and I only have a 20gig hard drive!:confused: ](*,)   Tried deleteing that and it corrupted the entire disk, erased windows and ubuntu, so much for disk management.:twisted:   I won't be trying that again.  Had to format the whole drive when I installed ubuntu this time.[-(   It's weird though, the disk management didn't have time to erase or format the drive partitions and yet they were gone.  It usually takes at least thirty seconds or more to erase a partition and it erased them in like 2 secs.  I guess now I have to order a new windows xp install disk, so I can reinstall windows, I won't be putting a second OS on my pc again.  Wish my floppy had of worked the first time.

---

### Post by Sef on 2006-12-29
This is from Gentoo's error collection:

[URL="5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it."]5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.[/URL]

---

### Post by Smokin715 on 2006-12-29
Thanks for the replies, but apparently all your suggestions implement repairing grub while ubuntu is installed.  I was trying to do the opposite, and reclaim the space ubuntu was wasting.  Removing ubuntu created the grub errors, and my boot disk for windows failed.  So I couldn't repair the mbr.  In the end I corrupted all of my partitions and had to reformat the whole thing. (Windows Disk Management bugged out and erased everything)  When installing ubuntu again, there were no partitions left to choose from, just the entire drive.  So my windows was gone, unretrievable since I didn't back it all up.  I guess in my case removing ubuntu and keeping windows just wasn't an option without having the original windows xp disk.  Thanks for your help anyways.  Maybe one day there will be an uninstall option implemented into the ubuntu OS, that also replaces the mbr with the original.  Until then I suggest to anyone that doesn't have a original windows disk or MS DOS boot disk that works, don't try to remove ubuntu, or you won't be able to boot into windows anymore.

---

