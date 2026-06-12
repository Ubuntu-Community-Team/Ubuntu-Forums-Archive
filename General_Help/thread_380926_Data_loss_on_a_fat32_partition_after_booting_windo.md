---
title: "Data loss on a fat32 partition after booting windows"
date: 2007-03-10
forum: General Help
---

### Post by susscorfa on 2007-03-10
ok this is a quite complicated story, so i try to explain it well


i have a dual boot machine  with 4 important partitions a nfts with windows installed , a fat32 with data, a root partition and a and a home partition.

my windows desktop is a folder on the data disk. 

my windows was in hibernation

i moved a folder with my email data to this same folder

every thing went good for a while till i booted my windows so it waked up from hibernation without any problems or error messages. 

then i shutdown my windows and booted ubuntu again. when starting thunderbird it didn't work and the folder is gone i cant find it in windows  or ubuntu

any one any sugestions how to recover this mail folder 

thanks in advance

---

### Post by thingy on 2007-03-10
hmm

If you haven't made ANY modifications to the FAT32 drive, you might be able to recover the folder using a recovery utility like: Freerecovery.

[http://www.softwarepatch.com/software/filerecovery.html](http://www.softwarepatch.com/software/filerecovery.html)

I've not used freerecovery itself but there are utilities out there which can trawl through the fat32 partition and look at files that appear on disk but not in the file table and allow you to recover these files.

Are you sure you've not simply moved ths folder into some other location? Did you do a file search on each drive to search for the e-mail data files itself?

---

### Post by susscorfa on 2007-03-10
i have searched it but it is unfindable i didn't make any modifications so i'm gone try free recovery

thanks for your reply

---

### Post by fransfrans on 2007-03-13
I had exactly the same problem, I had thunderbird set up to look in the same local folder in both ubuntu 6.10 and Windows XP and suddenly some of the files (concepts and trash) lyckily not the most important ones where gone. (not completely gone, the file was still there but it was empty, 0kb) Also another file that I opened to attach to an e-mail in Thunderbird Was gone (also an empty file)

---

### Post by UI-Freak on 2007-06-06
I just experienced this problem as well, and since I use my PC for production, serious stuff, I am beginning to doubt whether I dare to continue using Ubuntu. I mean, after all, that the FAT32 driver in Linux is probably reverse engineered and not 100 % free of bugs. Whoever and whatever is to blame my problem is real, right here and now.

I am dual booting between Ubuntu 7.04 and Windows XP SP2. I *never* had problems with my FAT32 data drive in the years of using XP, but since I started dual booting between Linux and XP I experienced this problem two times. I lost a lot of work and data, and have this feeling of stepping on thin ice. I am working with significant amounts of data that are hell to backup while not connected to a network (this is a laptop and I am travelling).

I used the hibernate feature on XP while in Linux, and I wonder if the problem can be found here, somehow? Perhaps something is cached in Windows XP? I think the file list on the FAT32 drive looks like it did when I hibernated XP?

It kind of makes sense that something could be cached in XP and written back to disk when booting after hibernating, or does it? I ran several checks on the FAT32 partition and found no problems.

I am very sure I did not just move some files. They were GONE! Some where missing, others where 0 bit files. Very disturbing.

---

### Post by UI-Freak on 2007-06-06
Actually, now I remember, that *some* files where again visible when I rebooted Linux. Other gone or 0 byte.

Now, THAT is weird, is it not? How can it be?

---

### Post by possessedskier on 2007-06-08
I had similar issues when sharing a FAT32 partition and hibernating Windows.  Any files written to the FAT32 partition from Kubuntu when Windows was hibernated weren't visible when I booted into Windows.  Everything worked ok when Windows wasn't hibernated.  This shows that it's probably not safe to write to a shared partition when one of the operating systems is in hibernation.

---

### Post by hikaricore on 2007-06-08
Am I to understand that some of you are **hibernating/suspending** to dual boot between windows and linux?

Because that is a really really terrible idea.  Like seriously why?  Why would you do that?

---

### Post by possessedskier on 2007-06-08
I hibernate Windows on my laptop because it starts up much faster than the normal Windows startup.  I've never had a problem if I don't write to partitions mounted in Windows when it hibernated.  I haven't booted into Windows in 2 months, so it's no longer an issue for me anyway.

---

### Post by UI-Freak on 2007-06-08
Exactly, because it is faster. Anyway, now that I know that [COLOR=Red]hibernating [/COLOR]is probably the problem, I wont do it.

But it still is dangerous stuff. Windows hibernated a few times on its own, when I forgot to turn off my laptop, and then I booted into Linux, not knowing about the danger ahead.

---

### Post by susscorfa on 2007-06-11
well i see many people experience this problem so i think we should make a bug report about it altough i fear the problem is in windows xp sp2 hibernation functions and not in ubuntu it self

why i use the hibernation thing because computers go into hibernation by them self and then i forget or are to lazy to boot the os again and shut it down properly

---

### Post by susscorfa on 2007-06-19
[https://bugs.launchpad.net/ubuntu/+bug/121157](https://bugs.launchpad.net/ubuntu/+bug/121157) <-- is the bug report i made

---

