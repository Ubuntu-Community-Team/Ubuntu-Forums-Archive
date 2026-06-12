---
title: "Un-accessible / ghost folders on usb drive"
date: 2007-08-12
forum: General Help
---

### Post by mikelucasiscool on 2007-08-12
Ok, i have a western digital 500 gb my book i have tons of files on it, one day i booted up and several of my folders had just dissapeared... ok so that is odd.

They weren't deleted and they are still using up storage space (over 30gb), however they don't show in linux with konquerer or, in windows, however they do show up under ls -a like this.

[http://mikelucasiscool.googlepages.com/snapshot1.jpg](http://mikelucasiscool.googlepages.com/snapshot1.jpg)

how can i manually recover these folders? any ideas?

- T4ct1cs

ps please keep in mind it is an external usb drive, and i'm a newb please specific instructions (line by line if it's command i don't know linux command line.. sorry i'm learning but right now all i know is cd and ls -a :D )

---

### Post by Ryzol on 2007-08-14
This is really weird, but since you can see the files under the commandline try this:
1. using the gui create a new folder where you are going to save these files. I'll refer to this folder as safe. 
2. open up the command line and use cd to navigate to where these ghost files are.
3. type "cp -r  * /path/to/safe"  Obviously don't type the quotes and fill in the actual path to safe.
4. Now verify that you can see these files in your gui and that you can access them.
5. Assuming this worked it is now safe to delete these ghostfiles. type "rm -r /path/to/ghostfiles". Before pressing enter doublecheck that this is typed correctly, rm skips the trashcan and **removes** the files so you do not want to put a typo in here.
6. Move the files in safe back to wherever you want them.

Note, doing it this way assumes you have the space to copy all those ghostfiles, if not I'll post an alternative but this is the safest way I know of. 

Oh and for learning the command line I found [http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php) invaluable.

---

### Post by mikelucasiscool on 2007-08-22
Thanks for the help i really appreciate it, especially the command line link you sent me very useful :)

The issue has been 'Neutralized'

I did not get my files back

i could not get permissions of any sort to that drive, i took it into windows and the only option i could find was to run a chckdsk /f and fix the disk, however this puts all my several thousand files into a new dir as 0001.chk - 10000.chk at a time (10k files per time i run it) and then i have to figure out what each one is.

I think the actual problem though is this western digital drive, i ran into a similar issue with it before i started running linux, i got most of my important files back because i had them backed up on the drive i bought before this which was a lacie 250gb drive.

I just finished smashing that 500 GB Western Digital on the floor (well at least the external case the hd itself i may plug into a desktop and try to retrieve files from at some point in the future when i return to germany where i am stationed and most of my other computer things are) this is actually only the second piece of computer equipment i have smashed, the first being a ball mouse (because i already had a new one... i mean come on... it was a ball mouse) anyway they both felt good, and i am tired of dealing with this crap, the only other HD to ever fail me was an 80GB western digital back in 2004 it was an internal ide drive (which are the only 2 western digitals i ever bought... so in other words 100% of the WD drives i bought... ate it) I WILL NEVER BUY ANOTHER WESTERN DIGITAL HD what's the point if it's just going to lose all my data because the file system becomes corrupt on it? this one didn't even ever see harsh conditions! my lacie 250gb lasted a year in kuwait/iraq bumping around in my backpack, and in excess of 100 degree temps with no problems, and here this WD just crashes on a whim in the AC! 

*hate hate hate hate @ Western Digital*

---

### Post by Ryzol on 2007-08-27
Sorry to hear that :frown:. I wouldn't consider your data gone forever though data recovery specialists can do amazing things. I've heard stories of hard drives damaged by hurricanes water logged beyond belief having almost all of their data recovered, so I think your data stands a pretty good chance of full recovery. Also if you really need to make sure your data is extremely failure tolerant you could get an external RAID1. This would basically be an external enclosure with 2 hard drives inside when you write to it, software has both disks write the data so if one fails there's 0 loss. The only time you're screwed is if both disks fail at the same time which is extremly unlikely.

---

