---
title: "help w/ PartImage please"
date: 2007-04-02
forum: General Help
---

### Post by billdotson on 2007-04-02
I recently just got my Windows XP SP2 disc out and formatted my internal HDD (the one Windows was on.. Ubuntu is on the external drive).  I created a 170GB partition for Windows and left the remaining space on my internal unallocated for now.  I want to get Windows at a place where I want it i.e. have all my PC games, Firefox, Thunderbird, Gaim, PDF creator, Office 2003, Democracy Player, etc. installed and configured the way I want it and then make a disc image of it so that I can back it up easily if anything happens to it.  I am keeping my Internet disconnected while Windows is booted so that no updates from MS or spyware from the internet will slip in.

I booted the systemrescue LiveCD, mounted my NTFS partition that is on my external HDD by doing:

```

ntfs-3g /dev/sdc4 /mnt/mine

```

Then I proceeded to make an image of Windows using PartImage.. compressing with gzip.  The file saved correctly, but then I closed and reopened and tried to restore it to see if it worked and when I told it to restore from the Windows.000 image (the path of it being /mnt/mine/Windows.000) It said Invalid compression level.  I know that PartImage is experimental and all but it says that if the HDD isn't fragmented badly and the system files aren't compressed it should be able to save the image.  Even more so it says that if the image saves successfully that it should restore.. unless of course there is some bug preventing it from doing so.  Is there a way to fix this or should I just choose to store it instead of compressing?

If PartImage doesn't work w/ NTFS what free ghost program could I use (legally) to back up my Windows install.  I am not worried about my Ubuntu install messing up it is my Windows install that I worry about.  I would probably stop using Windows almost completely if I didn't like to play the occasional PC game.

Thanks for your help.

---

### Post by Maestro23 on 2007-04-02
If PartImage doesn't work, try to find something here: [http://linuxappfinder.com/backupandrecovery](http://linuxappfinder.com/backupandrecovery)

Good luck.

---

### Post by dcstar on 2007-04-03
> **billdotson said:**
> 
.......
Then I proceeded to make an image of Windows using PartImage.. compressing with gzip.  The file saved correctly, but then I closed and reopened and tried to restore it to see if it worked and when I told it to restore from the Windows.000 image (the path of it being /mnt/mine/Windows.000) It said Invalid compression level.  I know that PartImage is experimental and all but it says that if the HDD isn't fragmented badly and the system files aren't compressed it should be able to save the image.  Even more so it says that if the image saves successfully that it should restore.. unless of course there is some bug preventing it from doing so.  Is there a way to fix this or should I just choose to store it instead of compressing?
......

I know the second compression option of Partimage comes with a caveat that it can only be restored manually, so I only use the first compression option (and it has worked ok for me numerous times).

---

