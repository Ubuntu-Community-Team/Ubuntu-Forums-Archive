---
title: "Pleaseeeeeeeeee Helppppp!!!!!"
date: 2007-03-10
forum: General Help
---

### Post by durty_dawg on 2007-03-10
So I have made the switch to Linux, but I still have to use windows for some things. My external hard drives (USB 2.0) are formatted NTFS. So when I switch between machines I have noticed that windows is now reading my hard drives as cd drives\ dvd drives. I just did a test with my flash drive to see if it was Linux and it did the same thing. This has ultimately left one of my external hard drives unreadable by windows. So how to I fix this thing thats going on with my externals, is it even fixable. I have data on these hard drive I cannot afford to lose. I can't replace photos of my 15 months in Iraq. PLEASEEEEEEEEEEEEEEEEEEEEEEEEEE HELPPPPPPPPPPPPPPP!!!!

---

### Post by crispy_420 on 2007-03-10
This is not an Ubuntu based fix but it is quick and recover your files. I've done this on a friend's notebook with great success.

I downloaded [Berry Linux]("http://yui.mine.nu/berry/"). It is a great little live cd that does a great job of recovering data from NTFS drives. Then you just have to decide how to save your files. Maybe another external drive or burn to CD, I suggest the CD route so you don't have to do this again.

---

### Post by durty_dawg on 2007-03-10
OK so I download the cd, and boot to it on my windoze box, so I can recover my NFTS files on my external hard drives. Is it possible that ubuntu is changing the way windoze reads the driver or drive. I know that in order to safe umount the hardware you eject it, or at least I think so. But its obvious that after I eject it turns the drive to cd type drive.

---

### Post by crispy_420 on 2007-03-12
No matter what anyone says, all NTFS read/write support is beta or sometimes alpha support. It may work this time but next time it may screw up your drive. It should not be used on critical data yet. But it will get better. On the other hand ext2/3 read/write for windows is stable. So if you need win and linux support go either ext3 (large file support and stable drivers) or fat32 (native support but files limited at 4GB).

---

### Post by darrenm on 2007-03-12
I'm the anyone ;)

[quote=http://www.ntfs-3g.org/]The driver is in STABLE status. Please see our test methods and testimonials on the driver quality page.[/quote]

---

### Post by crispy_420 on 2007-03-13
So stable that it trashed his file system.

---

### Post by silhouette on 2007-03-14
[quote="crispy_420"]So stable that it trashed his file system.[/quote]
It seems to me that the OP's external hard drives were unreadable before using Berry Linux. Unless Ubuntu does, indeed, have NTFS support.
[quote="durty_dawg"]OK so I download the cd, and boot to it on my windoze box, so I can recover my NFTS files on my external hard drives.[/quote]
Okay but were you ever able to read the drives within Berry Linux? Did they also appear as CD drives there?

Were your drives plugged in when you installed Ubuntu? This might have affected how they are viewed in Linux. But, of course, that wouldn't explain why Windows was affected as well, which is a total mystery to me.

Unless, of course, when you installed Ubuntu it somehow wrote something to the drives to where anything that accessed them from then on would read them as CD drives.

---

### Post by peabody on 2007-03-14
> **durty_dawg said:**
> So I have made the switch to Linux, but I still have to use windows for some things. My external hard drives (USB 2.0) are formatted NTFS. So when I switch between machines I have noticed that windows is now reading my hard drives as cd drives\ dvd drives. I just did a test with my flash drive to see if it was Linux and it did the same thing. This has ultimately left one of my external hard drives unreadable by windows. So how to I fix this thing thats going on with my externals, is it even fixable. I have data on these hard drive I cannot afford to lose. I can't replace photos of my 15 months in Iraq. PLEASEEEEEEEEEEEEEEEEEEEEEEEEEE HELPPPPPPPPPPPPPPP!!!!

Ubuntu should never have done anything to the drives.  Were you able to plug them into other Windows computers for reading?  Do all Windows computers see them as CD drives?

I'd recommend taking the drives out of their enclosures and sticking them inside a computer, but I take it that your externals are self-contained?  This is the problem with external drives that aren't enclosures.  There's no way to break the hard drive out without breaking the propietary factory enclosure and potentially causing harm to the drives.  It could have been that the controller is just foobar and if the drives could be extracted and hooked-up internally, I imagine the data should be readable.  The problem does not seem to be the hard drives themselves, it sounds like a problem with the controllers they're enclosed in.

---

### Post by darrenm on 2007-03-14
> **crispy_420 said:**
> So stable that it trashed his file system.

NTFS-3G isn't in Ubuntu by default?

---

### Post by crispy_420 on 2007-03-14
Maybe he read a guide here and tried it. Things may have gone bad for him.

Or just maybe it could be something so simple as peabody mentioned, faulty hardware.

Is it possible to try and force read/write with out drivers installed?

---

### Post by zorkerz on 2007-03-14
Whatever happened we have a lost soul here.  Who has presumably not solved his problem and i don't believe this is too productive in terms of helping.  That being said I don't really have any idea what happened.  Assuming the problem developed before Ubuntu NTFS support was installed.  Let me just recreat this in my mind.  
-You plugged the drives into an ubuntu computer and found no ntfs support
-then plugged them back into a windows computer and found them as cd/dvd drives

needless to say this should not happen and if i have the correct chain of events it sounds like it could have been caused by ubuntu.  What version are you running?

May I also recommend a more informative title in the future it should attract the attention of those who can actually help unlike me who often just blabs
good luck

---

