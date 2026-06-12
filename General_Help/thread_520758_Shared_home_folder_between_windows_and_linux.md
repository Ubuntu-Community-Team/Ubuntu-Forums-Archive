---
title: "Shared home folder between windows and linux"
date: 2007-08-08
forum: General Help
---

### Post by napsilan on 2007-08-08
I'm going to be reinstalling both OS's soon, and I'd like to have them both share the same home partition.  I.E. have one hard drive mount to /home in linux and c:/users in windows.  Would EXT3 or NTFS be a better choice for this?  I know there are a couple ext3 drivers for windows, and ntfs-3g for linux.

---

### Post by apetresc on 2007-08-08
Although Linux has NTFS-3G, it's not as ideal a solution as ext3 driver for Windows. I would recommend using [http://www.fs-driver.org/](http://www.fs-driver.org/) but this is probably a mostly subjective matter.

Moreover, ext3 supports things like symbolic links while NTFS does not. It is a very important feature to have, especially for a /home directory.

Just my 0.02 :)

---

### Post by notwen on 2007-08-08
This is not the best idea.  Are you just wanting to share data between the two OSes?  Linux cannot be installed to an NTFS partition and Windows cannot be installed to an ext3 partition.  Both OSes can however see the differing partition(Linux using NFTS-3G & Windows using the FS-Driver).  If I'm getting your post correctly, you're wanting your /home folder(of Linux) to show up as C:\Users(in Windows)?

---

### Post by napsilan on 2007-08-08
3 total partitions, one ntfs for windows, one reiser/xfs for linux, and a third for /home.  (I guess swap would be a 4th, maybe /boot a 5th).  My question was whether ntfs or ext3 would be better for that shared /home partition, since I know cross drivers exist to go both ways, although I don't think any deal with permissions. (not a huge deal for /home when I'm the only user)

I didn't realize that symlinks would be important there, thanks for that.  

Basically I'm tired of having to manually sync up 2 different documents/music/whatever folders.

---

### Post by merlinus on 2007-08-08
If you create a separate /home (or /data) partition in ubuntu, with the fs-driver it will show up as a drive letter in windows (e.g. h:}.

If you create an ntfs partition in windows, it can be mounted in the /media folder in ubuntu (e/g/ /media/music), and the ntfs-3g driver will allow writing to it from ubuntu.

-merlin

---

### Post by nitro_n2o on 2007-08-08
I agree with the guys.. leave your /home for linux and have another partition like 10GB formatted as FAT32 :) it's the one compatible with both OS's and instead of creating a 'MyMusic' directory in /home create a symlink to your FAT drive 
Just an idea ;)

---

### Post by napsilan on 2007-08-08
@merlinus
I know I can do it either way, my question was regarding which way is better.  I think ext3 is probably better in light of the symlink issue brought up earlier

---

### Post by merlinus on 2007-08-08
ext3 is also more reliable than ntfs and anything fat, and file recovery is easier as well due to the journaling feature.

-merlin

---

### Post by napsilan on 2007-08-09
NTFS journals as well (unsure if NTFS-3g uses it), and the windows EXT3 driver is actually an EXT2 driver so it doesn't use the journal.

---

### Post by merlinus on 2007-08-09
> **napsilan said:**
> the windows EXT3 driver is actually an EXT2 driver so it doesn't use the journal.

Not true, from what I read at:

[http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)

Perhaps it is due to my basic distrust of anything associated with M$.

Anyways, you pays your money and chooses your poison.

-merlin

---

### Post by dak-AD on 2007-08-09
I used to have my computer set up like this:

an exe3 partition

linux symlinking to this as /home/me

windows using fs-driver to mount the partition as exe2, and using it's /Desktop folder as %DESKTOP% via a registry tweak

also, i had the partition's /sharedSettings folder set-up to be used by both firefox-lin and firefox-win (which is more trouble than it's worth, let me tell you).

anyhoo, it works, but win-side you'll notice that several non-vital things don't work, eg you can't set a file as hidden if it's stored on an exe2 partition (presumably, windows uses NTFSs ADS to store info about wether a file's hidden or not, and exe doesn't have ADS; if you install windows to a FAT partition this problem might, in theory, not be there). also, iirc windows wont let you start a filename with . (eg, something you don't want to show up in linux, and so call .blah, might cause problems when accessed under windows sometimes). also, windows kept creating 'hidden' files that weren't hidden in linux or windows, and cluttered up my desktop.

all-in-all, I didn't think it was worth the effort tbh. i'd suggest setting up a partition (i'd choose exe3 and fs-driver, but that's just me) and plonk all you're stuff you wan't to share in there; then symlink linux, and registry-edit windows, so they both treat them as your music/documents folder etc, rather than having a shared home folder.

---

### Post by notwen on 2007-08-09
I'd recommend leaving your /home partition an ext* and simply mount your "shared windows" folder/partition within it using fstab.  I myself would simply use a FAT32 partition which would show up by default in both OSes to share files.  Having one partition that both OSes will be using for system files just doesn't seem to be logical to me.  Good luck in whatever you decide. =]

---

### Post by napsilan on 2007-08-11
Ended up using ext3, but it was kind of a toss-up because both ntfs-3g and ext2fsd had a couple random errors with really big folders.  Was finally able to mount the partition in the "my documents" folder after deleting hidden/system files, but afterwards I found this link on how to mount stuff in documents and settings/username.  [http://www.neowin.net/forum/lofiversion/index.php/t314372.html](http://www.neowin.net/forum/lofiversion/index.php/t314372.html)

Works pretty well, but it is a bit annoying in windows b/c all the . folders are visible, and I did have a couple random errors where it refused to write.  

Is there a way to mount a specific folder on a partition?  Or do you have to mount the entire partition someplace and then symlink it?

---

### Post by apetresc on 2007-08-11
> **napsilan said:**
> Is there a way to mount a specific folder on a partition?  Or do you have to mount the entire partition someplace and then symlink it?

Unfortunately, 'mount' works on device files, it has no notion of a file structure so it can't mount specific directories from a hard drive as far as I know. But symlinking is just as good a solution.

But I'm curious, what "random errors" were you getting with ext2fsd?

---

### Post by napsilan on 2007-08-12
Cannot copy 01 - Your Spirit's Alive: Insufficient system resources exist to complete the requested service

---

