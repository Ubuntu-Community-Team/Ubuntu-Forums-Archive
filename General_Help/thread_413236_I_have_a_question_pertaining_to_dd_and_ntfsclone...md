---
title: "I have a question pertaining to dd and ntfsclone.."
date: 2007-04-19
forum: General Help
---

### Post by billdotson on 2007-04-19
I just did a clean install of Windows, immediately after I booted into Ubuntu and made a backup .img of it with dd, and then I used ntfsclone (from the ntfsprogs-1.13.1 package) to make a smaller one.  I keep the dd image because I hear that if the hard drive fails ntfsclone can't restore it back like it was like dd can.

Anyway, I ahd installed ntfsprogs1.13.1 by source by doing:

```

./configure
make 
sudo make install

```

I had been using it but then I noticed in the configure log I was missing dependencies.. uh-oh.  So I cd'ed into the directory and did:

```

./configure 
make
sudo make uninstall

```

I tried to attach the config.log but it says it is too big to upload so oh well.

near the end of the lines in the terminal it said there is nothing to do with uninstall-am or something like that.

Then I went to synaptic and clicked libntfs8 and ntfsprogs to install.  I am assuming since I installed that versions from synaptic (1.12.1) my ntfsprogs install is fine.

Also, since I had a dd image of a clean XP install.. and I wasn't sure if the one I had made with ntfsclone in ntfsprogs 1.13.1 was any good.. I ran the following in the terminal to try to make another using ntfsclone in the ntfsprogs1.12.1 package:

```

 sudo ntfsclone /media/Windows_backup2/Windows_XP.img -s -o Windows_XP_clean

``` 

where /media/Windows_backup2/Windows_XP.img is the path to the image (so Windows_XP.img is the image).  It seemed to copy fine.

I then ran cmp in the terminal to see if they were any different by doing this..:

```

sudo cmp /media/Windows_backup/Windows_XP_clean /media/Windows_backup2/Windows_XP.img

```

and the result was 
```

/media/Windows_backup/Windows_XP_clean /media/Windows_backup2/Windows_XP.img differ: byte 1, line 1

```

is my install of ntfsprogs (the 1.12.1) ok?
can I do what I did earlier and use ntfsclone to make a backup of the clean install from the dd image w/o having to restore the dd image first?

---

### Post by billdotson on 2007-04-19
I fixed everything.. this thread is useless now

---

