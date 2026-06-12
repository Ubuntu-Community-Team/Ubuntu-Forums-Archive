---
title: "Is Ubuntu a ticking bomb?"
date: 2007-02-11
forum: General Help
---

### Post by tictacman on 2007-02-11
I've been reading the partition howto over at the tldp.org, when I came across this passage in section in 4.3.2.

"Files have lifetimes. After a file has been created, it will remain some time on the system and then be removed."

and even more worrying:

"Files in /home are likely to have a medium lifetime: several weeks or so."

[http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html)

What a shock!  The first thing to run through my mind is ubuntu is a ticking bomb!  While I sit here being productive, the system is counting down the hours, minutes and seconds until it can delete everything in my home directory without the slightest indication of what it is planning.  And what about my other directories such as my mounted windows partitions, my backup ext2 drive and so on?  There's no mention in the document about those.

---

### Post by geek_Man on 2007-02-11
Okay, I edited my post...

I can sorta see where it's coming from. It's not like files in the /usr/bin directory are going anywhere. Stuff in the /var directory is prone to change. The whole thing about Ubuntu being a time bomb sounds extremely unlikely.

---

### Post by llamakc on 2007-02-11
I've had files in my home directory since 1999, namely my .muttrc and .bashrc files. 

That section refers to ext2 partitions, by the way. Most likely you are using ext3. Also, when the author wrote 'it will remain some time on the system and then be removed' the meaning is not that the system will remove wanted files from /home but that a user will be the one to change/alter/grow/shrink/move/delete files in their home directory.

I worried about partition sizes back when my hard disks where less than 2 gigs, and don't even bother worrying about it anymore (of course, I keep my /home/ on a separate partition).

---

### Post by mich_r on 2007-02-11
This is about REAL lifetimes, statistical :) It is a parameter usefull for setting partitions, backups etc.

Nobody will remove your files, I am 100% sure of that.

---

### Post by koenn on 2007-02-11
you're kidding, right ? 

What you've read is a general discussion on what factors a system administrator should consider when deciding on partition sizes and backup media sizes.
It has nothing to do with the operatiing system randomly removing files after a few hours/days/weeks.

The lifetimes are how long the sysadmin can expect files to exist before they are removed _by a user or by the sysadmin himself_. Not by the operating system - what would be the use of that ? And then how come these forums aren't full of complaints that files suddenly start disappearing for no reason ? 


> 
4.3.2. File lifetimes and backup cycles as partitioning criteria

With ext2, partitioning decisions should be governed by backup considerations and to avoid external fragmentation from different file lifetimes.

Files have lifetimes. After a file has been created, it will remain some time on the system and then be removed. File lifetime varies greatly throughout the system and is partly dependent on the pathname of the file. For example, files in /bin, /sbin, /usr/sbin, /usr/bin and similar directories are likely to have a very long lifetime: many months and above. Files in /home are likely to have a medium lifetime: several weeks or so. File in /var are usually short lived: Almost no file in /var/spool/news will remain longer than a few days, files in /var/spool/lpd measure their lifetime in minutes or less.

---

### Post by meng on 2007-02-11
Yes, although I can see the potential for misinterpretation, this is talking about "average usage" and how this relates to backup policy.

---

### Post by tictacman on 2007-02-11
I have no problems with automatic deleting of redundent tmp files, in fact I welcome it as it saves me looking for them.

So what's with this document?  Is it just out of date? Unclear? Or perhaps its just my fault for not understanding it properly.  

I thought it might be a bit unlikely but the document seemed pretty authoritative  and its last revision was 2005 so I'd imagine that the author knew what ext3 was.

I was reading it in the context of backup but the message that came across was: backup your files because system will remove them before too long.

---

### Post by geek_Man on 2007-02-11
I believe it was about ext2, not ext3.

---

### Post by mich_r on 2007-02-11
I would say you do not understand author's intention. Lifetime it the time the file will be probably removed (by YOU not by the system) - you usually do not touch system files at all, but you sometimes wipe out something in your home directory, and finally tmp directory is the place where files live very short. So as I said before - this is about statistical lifetime (not "forced" one), you need this information when you for example plan a backup shedule.

> **tictacman said:**
> I have no problems with automatic deleting of redundent tmp files, in fact I welcome it as it saves me looking for them.

So what's with this document?  Is it just out of date? Unclear? Or perhaps its just my fault for not understanding it properly.  

I thought it might be a bit unlikely but the document seemed pretty authoritative  and its last revision was 2005 so I'd imagine that the author knew what ext3 was.

---

### Post by tictacman on 2007-02-11
Thanks Koenn, and I think you probably cleared this up for me.  It's just my fault for not understanding, srry guys.

---

### Post by kalikiana on 2007-02-11
> **tictacman said:**
> "Files have lifetimes. After a file has been created, it will remain some time on the system and then be removed."

I need... to back up... now! *gasp*

Seriously, why would you think should anything like that would have been implemented? You really ought to think twice about such strange ideas. Even the debian guys are not that evil although they have strict ways of enforcing their ideals.

---

### Post by cmost on 2007-02-11
Common sense should come into play here.  Would one honestly employ Linux across mission critical scenarios if files were to go "poof" in the night after a set amount of time?  Of course not.  The idea is ridiculous.  I have hundreds of files on my system that have been around since the early nineties.  They've not disappeared yet.

---

### Post by koenn on 2007-02-11
OK, this was fun. 
Anyone made a backup lately ?

---

### Post by geek_Man on 2007-02-11
Nope.

---

