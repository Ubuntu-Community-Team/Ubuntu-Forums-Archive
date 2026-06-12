---
title: "Looking for an Application to manage documents"
date: 2007-06-05
forum: General Help
---

### Post by wjhildreth on 2007-06-05
Hello all,

I work for several Rural hospitals in the United states. Most of these hospitals make very little money and as such are willing to look at 'non Microsoft' solutions to their needs. Usually, this takes the form of email or websites. Now, I have a chance to make another choice for Linux and I need some help finding an application that will perform the needed task.

Here is the scenario:

Old medical records take up lots and lots of space that could be better used for something else. However, before a medical record can be destroyed (the paper copy) there has to exist an electronic version.

At this point, the hospital scans the medical record to a PDF file and these are then burned to CD or DVD for long term storage. This saves a huge amount of physical storage space. The records that get scanned and stored in this manner are usually patients that have expired or have not been to the hospital in some number of years.

The problem with this solution is that occasionally a record has to be accessed for legal reasons or what have you. The problem is finding the record. The user had ti insert the cd and look for the record by hand.

What I would like to do, is let the user insert the cd and be able to search and store informaion about the record.

For example: store demographics about the patient and other info like admission number, medical record number, visit type, ER, OP, IP, OBS and the like. Then with this information stored for each PDF file, the user should be able to search the system and find what Disks the records (PDF) are stored. Alternatively, the records could be copied to a file server for fast access (With backups of course) 

I guess I am looking for some sort of document management system. If I can implement it here, then I know of several more rural facilities that could benefit from the same solution.

One last requirement, it would need to be a networked solution. The records should be available to more than one person at any given time.

Can someone help me, please?

Warm Regards,

Joe Hildreth

---

### Post by MontanaMax on 2007-06-05
To make the records available to more than one person at a time, I think the solution will have to avoid keeping a single copy on a CD, and instead keep a master copy in a single database that has shared network access. On the good side, storage is getting cheaper and cheaper these days.

I'd suggest looking at some of the system on sourceforge like [http://www.knowledgetree.com/](http://www.knowledgetree.com/) or [http://docsys.sourceforge.net/](http://docsys.sourceforge.net/) or [http://contineo.sourceforge.net/index.html](http://contineo.sourceforge.net/index.html) or [http://www.epiware.com/](http://www.epiware.com/)

There are commercial _really expensive_ applications that do these functions that I've been involved in either evaluation or installing, but I wouldn't recommend them for small (less than 2000 users) systems.

Good luck!

- Jon

---

### Post by wjhildreth on 2007-06-05
MontanaMax:

Well I looked at some of these management systems but none of them are really what I am looking for. Truthfully, they are a bit overkill for what I need. None of them allow you to create custom fields for your files either. Thanks for your help though. I do appreciate it.

If you think of something that might me a bit simpler, please give me a shout. You have helped me define what I need.

1) The ability to set up fields relating to a file (In this case medical records) Medical Record Number, Admission Number, Patient Name and that sort of thing

2) The ability to upload a file to a central repository and add data to the above created fields.

3) Allow only users created within the system to access these records (files)

4) Use MySQL or other database to index the information.

Thanks again for your help.

Regards,

Joe Hildreth

---

### Post by MontanaMax on 2007-06-06
I also spotted this program "Simple Document Management  System" - [http://sdms.cafuego.net/what.html](http://sdms.cafuego.net/what.html) - it doesn't appear to be supported currently, but it's GPL based and very basic looking, so you could probably tweak it to handle the data fields you're looking for in Requirement 1 and have the base system take care of Requirements 2, 3, and 4 out of the box.

This is another one I've found that looks reasonably well tested and already included meta-data elements about documents - but I'm not sure of the level of effort needed to customize the meta-data types.  [http://sourceforge.net/projects/mydms/](http://sourceforge.net/projects/mydms/)

I'm suprised that I'm having such a difficult time finding a simple, small business oriented open source document management system with customizable meta-data elements - everything I find seems to be huge, Windoze, commerical, or stand-alone. I did find a thread of someone being happy with a KnowledgeTree install on Ubuntu, but it still sounds a little complicated for what you might need.  [http://ubuntuforums.org/showthread.php?t=235486](http://ubuntuforums.org/showthread.php?t=235486)

Good luck!

---

### Post by wjhildreth on 2007-06-06
I will take a look at it. I also looked at OpenDocMan. It is closer to what I need, but not quite there either. Thanks for your help.

Regards,

Joe

---

### Post by wjhildreth on 2007-06-08
Well I have been digging around in the source for SDMS 2. I think there is some stuff I can use. I will have to re-write a fair amount to make it work for my needs. Namely, documents are stored in BLOBs rather than the file system. I would feel safer having them in the file system just in case the DB went south for the winter. The file system as created all exists programatically in the database, but there is no reason not to replicate it in the file system and use the db version for fast lookups.

Anyway, thanks for helping me locate something I can work with. I plan on fooling around with the source and looking at openDocMan a little closer too.  Thanks for your time...

Regards,

Joe Hildreth

---

