---
title: "Recover files from NTFS parition Erased by Ubuntu Install"
date: 2008-02-27
forum: General Help
---

### Post by knightzor on 2008-02-27
hi all

Im in a bit of a pickle so hopefully someone can point in the right direction or throw me some tips.

So basically, i have a laptop which had an xp partition about 40gb 31gb or so used NTFS format. I ran through the ubuntu install and somehow I've missed the partition config so instead of resizing and utilizing the free space its wiped out the hole NTFS partition.

not good. So im trying to retrieve a few files mostly jpeg's, i've tried the latest active undelete which allows you to use a bootable iso, it was able to see the files and recover them to a usb drive but they all seem corrupt bar the odd 1 or 2.

Is there any other utility or program i could use, or should i try a professional service or give up all hope?

Cheers

---

### Post by Zalbor on 2008-02-27
I'm not 100% sure, but I think that if you formatted over the partitions it's unlikely you can find anything...

---

### Post by seshomaru samma on 2008-02-27
mmm..
try [this ]("http://www.cgsecurity.org/wiki/PhotoRec") (and maybe[ this]("http://www.cgsecurity.org/wiki/TestDisk") )

---

### Post by seshomaru samma on 2008-02-27
oh and[ this ]("http://www.diskinternals.com/")

but i think it's not free

---

### Post by ryanhaigh on 2008-02-27
I used this the other day, free and no install required.
[http://www.adrc.com/software/data_recovery_tools/](http://www.adrc.com/software/data_recovery_tools/)
Only problem is it's windows only.

edit: haven't tried on ntfs

---

### Post by knightzor on 2008-02-28
Thanks for the responses guys. I took testdisk for a whirl pre-posting this couldn't quite get that going. I ran photorec last nite, it seems like a really good tool and it was able to recover everything i believe but haven't had a chance to look through the recovered files. I did have a brief look at the jpeg recoveries but it seems its only recovered the preview image of the file not the file itself. AKA i open the folder of the recovery i can see the thumbnail preview for the jpeg's but upon trying to open don't see anything. Will have a thorough look tonight and let you know.

Could that possibly be because im recovering the files to an NTFS formatted external disk?

Cheers

---

### Post by bodhi.zazen on 2008-02-28
Some of the data may well have been over written (when you installed Ubuntu) :(

In case no -one mentioned it, you should not run from the hard drive until your date recovery is complete. (ie run from a live CD).

---

### Post by knightzor on 2008-02-28
> **bodhi.zazen said:**
> Some of the data may well have been over written (when you installed Ubuntu) :(

In case no -one mentioned it, you should not run from the hard drive until your date recovery is complete. (ie run from a live CD).

Yea i know :(

Yea I'm running the ubuntu cd live environment to do the recovery stuff so nothing extra has been written to disk :)

---

### Post by knightzor on 2008-03-02
it seems the small images are actually frame by frame jpeg's of quicktime movies taken with a digital camera. how the quicktime movie became split up like that im not sure but thats whats happened.

Rather then fiddle round with it where handing it over to the professionals so thanks for all the help guys :)

---

