---
title: "Dual Harddrive-Link broke from Ubuntu to 2nd drive"
date: 2007-08-23
forum: General Help
---

### Post by tinkietruck on 2007-08-23
OK, I have two hard drives.  One is running Windows (Ugh) and the other Ubuntu.  I use the Windows to upload my pictures from my digital camera because it dates them and puts them in files by date.  Well, I rebooted into Ubuntu because that is what we like to use and the link to the second hard drive is broken.  This is the third or fourth time it has broken, but it keeps fixing itself somehow several days later. 

Has anyone else had this problem?  If so, what issues could there be?  I know that's a lot to ask and answer, but any help would be appreciated.  I do know that I haven't installed the latest updates from Windows.  I chose not to.  All the updates from Ubuntu have been installed to date.  

Right now I have all of my pictures that I need on the Ubuntu drive, but there are a few more I would like to add to it, but can't because the link is broken.  

I get the following error when I try to open the link:

**_The Link "link to My Pix on hda2" is Broken. Move it to Trash? This link can't be used, because its target "/media/hda2/Documents and Settings/Clint Mullins/My Documents/My Pictures" doesn't exist._**

I don't want to move it to the trash because maybe it will fix itself in a few days.  

Once I find out how Ubuntu is set up to read the second hard drive, I will update this post.  

Thanks,
Brandy

---

### Post by dragomirov on 2007-08-24
sorry if I may look stupid, but is your windows drive correctly mounted under linux? I mean, if you browse the files in /media/hda2, did you see all the contents?
Another point is that ubuntu after the 7.04 Feisty upgrade tends to mount every hard drive as scsi, so the "old" mountpoint /media/hda2 is actually renamed as /media/sda2.
Give a try and let us know :)

---

