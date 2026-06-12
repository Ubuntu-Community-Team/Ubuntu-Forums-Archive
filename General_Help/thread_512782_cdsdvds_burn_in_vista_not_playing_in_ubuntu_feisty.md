---
title: "cds/dvds burn in vista not playing in ubuntu feisty"
date: 2007-07-29
forum: General Help
---

### Post by torrent478 on 2007-07-29
Whenever I burn a cd or dvd from vista on my desktop to put in my laptop running feisty I get an error: mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad options, bad superblock on /dev/scd0, missing codepage or other error. 

Things I burn from my xp partition with the same cd burner work fine.

Is this just a vista problem? If it is I can ignore it for a while, but as more people start to use vista this is going to become troublesome for a lot of people I might immagine

---

### Post by NutrOn on 2007-07-29
It's not a Vista thing it's either a Linux thing or a Fiesty thing. I'm having a similar problem but so far there is no indication  they have a fix.:(

---

### Post by bigjack on 2007-07-29
You are not alone!

Please check out these two threads that I started.  The problem appears to be something that is not simple to correct.  People will tell you about codecs and eventually someone might ask you about hdparm.conf and fstab and a bunch of other stuff--I've been there.  They might be part of the problem but the solution is not with them.  The solution is beyond my knowledge of computers but I am working on finding someone who knows how to solve the problem.  What surprises me is that all the threads that deal with this problem have not been combined and that someone who actually understands the kernel has not contributed to solving the problem.

[http://ubuntuforums.org/showthread.php?t=506890&highlight=some+cds+dvds](http://ubuntuforums.org/showthread.php?t=506890&highlight=some+cds+dvds)

[http://ubuntuforums.org/showthread.php?p=3102028#post3102028](http://ubuntuforums.org/showthread.php?p=3102028#post3102028)

In the end, the problem might have to do with cdrom.h in the kernel.  But who can correct it or advise us how to correct it?

---

### Post by torrent478 on 2007-07-29
I read your threads big jack and my problem isnt quite the same as yours. I'm guessing it has something to do with the way Vista writes cd's from the default CD burner, The computer that I burn from has both xp and vista on it, and cd's I burn in xp are fine, I think im going to try installing nero on both the xp and vista partition to see if that will work. My guess is that if they do, the problem lies with the built in cd burner in vista. I hope they come out with some sort of fix for this in the next release, because as more people adapt vista this is going to become quite annoying for many a linux user.

---

### Post by daverave999 on 2007-07-30
I am also unable to mount optical media. I'm pretty convinced it's not my hardware seeing as it has only happened recently, seemingly the same time as this happening to several other people. Broken by an update?

---

### Post by Irihapeti on 2007-07-31
I have my desktop set up as dual-boot Vista (home basic) and Ubuntu feisty, and I've had no problems reading CDs/DVDs with either system. That is, providing they are burned as mastered format in Vista.
I notice that Vista tends to default to the UDF file system in some cases. Maybe you have formatted your disks to UDF, which I understand isn't available in XP (though I gather it will read them). If that's happened, unfortunately you can't go back and reformat as ordinary format.

Nero and many other programs only use the mastered format, so they avoid this problem. Once there is data on the disk, Vista seems to recognise it as mastered format and the built-in writer behaves accordingly.

There are utilities to read UDF in Ubuntu, in the repositories. I haven't got them going yet. I'm still fairly new at this command-line stuff.

Hope this helps.
Irihapeti

---

