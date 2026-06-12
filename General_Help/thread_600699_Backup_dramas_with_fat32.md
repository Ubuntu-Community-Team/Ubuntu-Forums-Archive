---
title: "Backup dramas with fat32"
date: 2007-11-02
forum: General Help
---

### Post by wheezer on 2007-11-02
I am still a noob at linux.

I have a new Lacie 500gb external. A linux guru (who i cannot reach now) told me to format it as fat32, as linux would sometimes have trouble with NTFS.

Only trouble is, that Simple Backup only wants to make one huge tar file. So the system quits at the 4gig limit.

I've tried using Rsync with some basic params, and while many folders copy fine, I get a zillion "Operations not permitted" on countless folders,for reasons I cannot fathom (I am running from root account).

So the question is, how the hell can a new to linux guy do real backups without taking a week off to figure out the very dense Rsync, and when its' failing.

1) Was my guru right about not using NTFS, or is using it the easy solution, 
2) Is there a better option than SImple Backup? (I can't find one)

Suggestions for dummies really appreciated.

---

### Post by wheezer on 2007-11-02
THis guy knows a lot more than I do, and he's having the same problem
[http://www.itwire.com/content/view/14983/1085/](http://www.itwire.com/content/view/14983/1085/)



**His final comment ...**
[I]Coming from Windows World, all this messing around with mounting drives, setting folder permissions and dealing with complicated admin rights such as "root" is enough to bake your noodle. Once I get over this hurdle I think things should get easier, but meanwhile I'm stuck. I've scoured the web for solutions but nothing quite does the job and I'm out of ideas. Little help?
[/I]

My sentiments exactly.  Just look at all the geeks trying to just help him achieve a simple backup. Nobody but a geek could even follow all their comment threads. He's lost, and so am I.  

How can ubuntu maintain that this product is ready for prime time, when such basic issues are so difficult.  I still can't understand it.  But right now, i just want to be able to use my shiny new backup drive, and at the moment, it's about as useful as a shiny new brick.

There must be some easier solution than spending all this time getting a headache, reading solutions that mostly seem wrong.   

DOES ANYONE HAVE A REAL SOLUTION THEY KNOW WORKS?

Help desperately appreciated.

---

### Post by hikaricore on 2007-11-02
So wait....WHAT?

It's Ubuntu's/Linux's problem that the fat32 filesystem has a single file size limit??

I was under the impression that tar achiving could auto split the files at a certain point.  Might I suggest reading the man files?

Anyway... you could just format it as EXT2/3 and then install the appropritate driver to access this content from ***dows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by lolindrath on 2007-11-02
Hi There,

A couple things, there is already a bug for this exact problem: [https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/144295](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/144295) so hopefully it'll get worked on soon.

To fix your problem for now I would make what you're backing up much smaller. So backup just your /home and exclude any movie or music files that you really don't need, worry first about your photos and documents.

Your linux guru was correct in suggesting FAT32, it allows for the best portability between windows and linux.

--Lolindrath

---

### Post by wheezer on 2007-11-02
> **hikaricore said:**
> So wait....WHAT?

It's Ubuntu's/Linux's problem that the fat32 filesystem has a single file size limit??

I was under the impression that tar achiving could auto split the files at a certain point.  Might I suggest reading the man files?

Anyway... you could just format it as EXT2/3 and then install the appropritate driver to access this content from ***dows: [http://www.fs-driver.org/](http://www.fs-driver.org/)


Autosplit? Read the man files for WHAT?  Tar?  How would simply backup know about that?  

Driver to access?  Say what?  Again, I am rather new to linux, and what is second nature to you, requires a lot of mental process for me (and most).  Perhaps if you can be a bit more specific in your brevity.

I was once told to avoid Ext2. Are you suggesting that it will happily let me back up my linux files and windows files to one single partition (which is what I originally intended? I do not neet a dual boot. Just an external drive.

Before I got this post, I partioned the drive twice. Once for ext3, and once for Fat32/

Should I leave it, or do as you suggest with Ext2

Thanks

---

### Post by wheezer on 2007-11-02
Lolindrath,


I have already set up two partions. One for ex3, and one for fat32. Should I just leave it alone, or is the suggestion to use ext2  valid?  (I guess he meant, ext2. It was ambiguous).  Reading the page he posted, that  seems to have tradeoffs about permissions, and such, but I am not sure I care. Are they get lost completely, or are just not usuable from the backup drive. 

I just want one complete backup, so I can install Gutsy.  Then I want a backup of that, and incrementals.

---

### Post by lolindrath on 2007-11-02
> **wheezer said:**
> Lolindrath,


I have already set up two partions. One for ex3, and one for fat32. Should I just leave it alone, or is the suggestion to use ext2  valid?  (I guess he meant, ext2. It was ambiguous).  Reading the page he posted, that  seems to have tradeoffs about permissions, and such, but I am not sure I care. Are they get lost completely, or are just not usuable from the backup drive. 

I just want one complete backup, so I can install Gutsy.  Then I want a backup of that, and incrementals.

ext3 is the way to go, it recovers from computer crashes and pulling a usb drive out of a computer much better than ext2 or fat32.

The max file size for ext3 is (usually) 16 gigs so you should be good, good luck!

--Lolindrath

---

### Post by LaRoza on 2007-11-02
[QUOTE=wheezer;3692273
1) Was my guru right about not using NTFS, or is using it the easy solution, 
2) Is there a better option than SImple Backup? (I can't find one)

Suggestions for dummies really appreciated.[/QUOTE]

FAT32 is know for its limitations. I recommend it, because it works fine with Linux and Windows. It has a limit on file size, which is 4 GB - 1 byte. 

For larger files, use NTFS, EXT3, or EXT2. There are others, but these are the most popular. If you use Windows a lot, format as NTFS, if you use Linux more, use EXT2.

Either way, you will need a driver for the other OS. Ubuntu 7.10 has it by default, so NTFS might be the easiest solution. EXT2 will just as well, but you will need the above mentioned driver for it.

---

### Post by zaphod777 on 2007-11-02
how is the speed between gutsy and NTFS? say copying a 4 GB file not counting the difference between USB 1.0 and 2.0?

---

### Post by por100pre1 on 2007-11-02
I use Grsync to backup my files to a fat32 hard disk. Fat 32 only allows 4GB files so using compressed backup tools won't work. Try converting the partition to NTFS or ext3 if you want to use compressed backups.

---

