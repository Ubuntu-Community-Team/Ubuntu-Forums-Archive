---
title: "Deleting files forever"
date: 2007-12-30
forum: General Help
---

### Post by moonliter on 2007-12-30
How can I delete my deleted files from hard disk so that they can not be recovered anymore from some program recovery deleted files?

---

### Post by lswest on 2007-12-30
you can use the shred command in the terminal, which re-writes nulls over the file after deletion, making it hard (but not impossible) to recover.  Not sure of the exact syntax, but it should be clear with "man shred" in the terminal.

---

### Post by HermanAB on 2007-12-30
Oh good grief, here we go again.  Please people, shred doesn't work anymore.  It was designed in years gone by when Ext2 was the only file system for Linux.  It doesn't work with modern file systems.  Please RTM:
$ man shred

If you need to delete a file, just use 'rm' - that is the best you can do.

If it was a very sensitive file and you absolutely have to delete it without trace, then get a big sledge hammer and give the hard disk a good whack with it.

The military dump their old disk drives in steel smelters, for a good reason.

Cheers,

Herman

---

### Post by badactress on 2007-12-30
I'd agree.. I work for a cctv company & we look after government/military sites all over the world.. the only way to completely wipe sensitive data is to physically destroy the drive. We used to zap them with massive electro-magnetic field but even that wasn't guaranteed to make them  safe. Now we just drill them & hit them with hammers! :)

---

### Post by t0p on 2007-12-30
> **HermanAB said:**
> Oh good grief, here we go again.  Please people, shred doesn't work anymore.  It was designed in years gone by when Ext2 was the only file system for Linux.  It doesn't work with modern file systems.  Please RTFM:
$ man shred

Hmmm... maybe *you* should RTM.

From **man shred**:
>  In  the  case  of  ext3 file systems, the above disclaimer applies (and
       shred is thus of limited  effectiveness)  only  in  data=journal  mode,
       which  journals  file  data  in addition to just metadata.  In both the
       data=ordered (default) and data=writeback modes, shred works as  usual.

> **HermanAB said:**
> 
If you need to delete a file, just use 'rm' - that is the best you can do.

If it was a very sensitive file and you absolutely have to delete it without trace, then get a big sledge hammer and give the hard disk a good whack with it.


Of course shred isn't foolproof.  If a well-resourced forensic lab wants to spend a year going over your disk, they'll recover about everything.  In fragments.

But if you're not a spy or a child pornographer, shred -u will do a pretty god job on any sensitive file you wanna flush.

---

### Post by LaRoza on 2007-12-30
Maybe we should keep the RTFM's to a minimum.

"man courtesy"

---

### Post by b0rka7a on 2007-12-30
> Now we just drill them & hit them with hammers!
ahahhahaha :D

---

### Post by t0p on 2007-12-30
> **LaRoza said:**
> Maybe we should keep the RTFM's to a minimum.

"man courtesy"

You're right, of course.  Just bugs me when someone gives incorrect info and says RTFM when if that person had read the fine manual himself he would have seen he was wrong.

---

### Post by lswest on 2007-12-30
all right:P so my advice was a wee bit outdated... sorry about that, never really used shred, so i didnt realise it became obsolete. sorry for the bad (or outdated) advice!

---

### Post by HermanAB on 2007-12-30
There is equipment that can read data off a disk many layers deep, so even the old 20 times overwrite trick doesn't work anymore.

This is why hard disk encryption is so important.  The only way to really delete stuff off a disk is to encrypt the whole file system and then forget the encryption key.

---

### Post by t0p on 2007-12-30
> **HermanAB said:**
> There is equipment that can read data off a disk many layers deep, so even the old 20 times overwrite trick doesn't work anymore.
But you can tell shred to overwrite a file 146 billion times if you want.
> **HermanAB said:**
> 
This is why hard disk encryption is so important.  The only way to really delete stuff off a disk is to encrypt the whole file system and then forget the encryption key.
How will encryption help if shred won't?  Even RSA can be cracked eventually, theoretically.  Just like even shredded files can be recovered, if someone really has the resources and the inclination.

---

### Post by LaRoza on 2007-12-30
The question isn't what is most secure or if it is possible, but where does the amount of trouble it takes to crack/undelete/recover become not worth the gain.

For military type secrets, physical destruction is probably the best bet. It may be worth a lot to some to use an electron microscope to recover DoD wiped files, but for the average data a PC has, such measures are not needed.

---

### Post by t0p on 2007-12-30
> **LaRoza said:**
> The question isn't what is most secure or if it is possible, but where does the amount of trouble it takes to crack/undelete/recover become not worth the gain.

For military type secrets, physical destruction is probably the best bet. It may be worth a lot to some to use an electron microscope to recover DoD wiped files, but for the average data a PC has, such measures are not needed.

Indeed.  So, if your file system is ext3 data=ordered or data=writeback, and if you're not trying to keep your deleted files from the intelligence services, shred -u will do.  As will gpg.

But if you are a spy/terrorist/kiddie porn vendor, there ain't *no* software can keep your dirty secrets!!

---

### Post by LaRoza on 2007-12-31
> **t0p said:**
> 
But if you are a spy/terrorist/kiddie porn vendor, there ain't *no* software can keep your dirty secrets!!

If you are the last of these, call the police on yourself on help the world become a better place.

(Couldn't hurt, you never know...)

---

### Post by Linder on 2008-02-28
Working as a computer forensic, I can state that the above is true. Information stored on magnetic storage media is notoriously hard to erase. Safest bet is to encrypt it with a high security encryption method and use a GOOD password. Your encryption isn't safer than your password, and even when encrypted, it can be cracked. 

Absolute safest bet? Melt the harddrive. There, evidence destroyed. There is no other safe way.

---

