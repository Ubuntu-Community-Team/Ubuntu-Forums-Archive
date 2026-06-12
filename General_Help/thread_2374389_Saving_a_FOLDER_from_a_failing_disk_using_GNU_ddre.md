---
title: "Saving a FOLDER from a failing disk using GNU ddrescue"
date: 2017-10-15
forum: General Help
---

### Post by Margaret Dumont on 2017-10-15
Hello,

I have an external hard disk which has lately started to run unbearably slow. Since I suspect it is failing, I would like to urgently backup the most important files.

This hard disk is normally used on a Windows system but I am attempting this backup from a computer with Ubuntu. I've tried the traditional copying of the folder with the important files from the compromised HD to the healthy one using Caja. And it seems like this is indeed happening, but the rate is veeeeery slow. It claims that it will need 1700 hours, which is more that 2 months... not very reasonable, specially because I'm not sure the disk will last that long.

The failing hard disk is of about 1 TB but, since I don't care about the rest of files and I don''t have that amount of free space easily available to make the backup, I would like to copy ONLY the most important files, about 100 GB.

I've read in its manual that GNU ddrescue is able to copy FILES and that it starts with the bits that can be copied fast, coming back to the toughest bits later on, in order to maximise the rescued output before the HD fails. 

However, all the information and examples I find are about copying the whole partition. Does anyone know how could I copy only the contents of that folder using GNU ddrescue before it is too late?

Additionally, I understand that GNU ddrescue doesn't care about file system because it copies 1s and 0s but, then, I don't understand how will I be able to access the files afterwards, because I won't be able to simply mount the image as in the case of backing up the whole partition. Any ideas?

Thanks!

      Margaret

More info:
- The failing external hard disk is a WD Elements with a single NTFS partition of about 1TB. It doesn't seem to have SMART.
- The destination NTFS partition for the backup of the files is not empty and has only about 150 GB of free space. It is on another external hard disk.
- I am using a computer with Ubuntu Mate 16.04 LTS with ntfs-3g and gddrescue installed.

---

### Post by dragonfly41 on 2017-10-16
I will chip in with some suggestions.

First you have made it more difficult for yourself by keeping all your eggs in one basket.   It might have been better to split your 1 TB drive into multiple partitions. You are short of space to receive any recovered files.

I have a dual boot (in fact multi boot) setup and I use different tools from time to time for recovery.   Thankfully less frequent these days since I've invested in a new desktop.

Your WD Elements drive does seem to be quite modern. Some of the recycled drives I have had to get by with have seen years of life in old laptops etc.

Since you see failure when connected to both Windows and Ubuntu, have you eliminated the possibility of a faulty USB cable as a common factor?

Your drive (NTFS partition) might be more readily recovered using Windows tools.  However the downside of using Windows is that most recovery tools come at a price.

Starting with Western Digital there is this free test utility.   Data Lifeguard to test your disk.

[https://support.wdc.com/knowledgebase/answer.aspx?ID=940](https://support.wdc.com/knowledgebase/answer.aspx?ID=940)

Another tool in Windows is from here ..

[https://www.easeus.com/storage-media-recovery/western-hdd-bad-sector-repair-tool.html](https://www.easeus.com/storage-media-recovery/western-hdd-bad-sector-repair-tool.html)


If the above do not help you then another tool to try is TestDisk 7.1 which is available for both Windows and Ubuntu.

Finally I suggest a very comprehensive tool R-Studio from [http://r-tt.com.](http://r-tt.com.)

There is a version of R-Linux in Ubuntu but it only recognises ext2/ext3/ext4 file systems.

For NTFS data recovery you need to go to the Windows version of R-Studio.

You can use this in evaluation mode and if it finds your files you then will have to purchase a licence (which can be as much as cost of another WD Element drive).

This toolset allows *folders* to be selected for recovery (as you emphasise in your post).

[COLOR=#0000ff]
**[Later thoughts]**[/COLOR]

On the subject of slow speed of ddrescue I have read that using the reverse copy mode might help to overcome bad areas.

The argument is **-R**

[https://superuser.com/questions/413650/is-there-any-way-to-speed-up-ddrescue](https://superuser.com/questions/413650/is-there-any-way-to-speed-up-ddrescue)

---

### Post by Margaret Dumont on 2017-10-19
Thanks dragonfly41 for your extensive answer.

I rarely use Windows in my life. This is a hard disk from a friend. I already suggested he tried disk checks from within Windows but he told  me that he wasn't able to execute any of those. I offered to help  trying out with my Ubuntu computer and I seemed to be able to connect to  the drive, recognized the files and so on, so I wanted to try to  recover those important bits.

I'm afraid that buying software for this, specially Windows software, is not an option in this case. He might not even have the money to buy the new hard disk, and I am not willing to buy programs I will never need. Although I will suggest him to divide his hard disk in partitions for the future, if he finally gets a new one.

From your post it is not clear to me whether it is possible or not to run "GNU ddrescue" only for files/folders (ie. if you think this is not possible or if it indeed possible but you think Windows tools would work better). The problem is that I don't know the syntax because I haven't found any examples, and I am afraid to try without having any idea what I am doing.  :P

---

### Post by dragonfly41 on 2017-10-19
Given your constraints then I suggest that you focus on trying testdisk in your Ubuntu setup to recover selected files.
I suggested testdisk as an option above in my reply.

You will need to study the recovery workflow before starting.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And have some space prepared and ready to save any recovered files.
Test disk will ask you at some stage where to save recovered files.

> [COLOR=#000000]From your post it is not clear to me whether it is possible or not to run "GNU ddrescue" only for files/folders

Not that I am aware of.[/COLOR]

---

### Post by untrustytahr on 2017-10-19
> **Margaret Dumont said:**
> 
From your post it is not clear to me whether it is possible or not to run "GNU ddrescue" only for files/folders. The problem is that I don't know the syntax because I haven't found any examples, and I am afraid to try without having any idea what I am doing.  :P

Well, I didn't think you could... but my google fu led me to this exact problem that someone asked ddrescue's author a decade ago:
[https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00000.html](https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00000.html)
and apparently it can:
[https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00001.html](https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00001.html)
[https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00002.html](https://lists.gnu.org/archive/html/bug-ddrescue/2006-09/msg00002.html)

The problem is that ddrescue will not recurse through a directory; it only works will files, so you will probably have to use a "find -exec" or xargs to get the filenames and pipe it into ddrescue.  The problem with that method is, if the disk is truly failing, the "find" command would fail and quit.

---

### Post by dragonfly41 on 2017-10-19
> [COLOR=#000000]I seemed to be able to connect to the drive, recognized the files and so on, so I wanted to try to recover those important bits.[/COLOR][COLOR=#000000]

Please clarify what you mean by "recognized the files".   You might be able to use a file manager such as Thunar or just Nautilus to navigate to "recognized" files and save them.

And regarding the above tip re: ddrescue recovering *files* (not *folders* as you have requested) if ddrescue grinds slowly (due to encountering bad blocks in an area of disk) you can try the reverse copy option -R which I read about.

Finally there is another tool .. photorec which comes with testdisk .. if you can define filters (file types) to be recovered. For example if the valuable files all have .doc extensions ( or .jpg or .png etc) then you can narrow down search by specifying .doc as filter.  However with photorec you lose filenames which might be a problem with 100 MB of files to recover and requiring manual vetting of each file content.[/COLOR]

---

### Post by dragonfly41 on 2017-10-19
Referring to your earlier post#3
> [COLOR=#000000]The problem is that I don't know the syntax because I haven't found any examples, and I am afraid to try without having any idea what I am doing. 
please study the examples given in the link in my earlier post#2 .. they are very helpful .. for example read about the -R and -K arg options which might help in your situation.

[/COLOR]https://superuser.com/questions/413650/is-there-any-way-to-speed-up-ddrescue

---

### Post by Margaret Dumont on 2017-10-20
Dear dragonfly41 and untrustytahr, 

Thanks a lot for your responses. 

> Given your constraints then I suggest that you focus on trying testdisk in your Ubuntu setup to recover selected files.

Sorry! I missed that Testdisk was for Ubuntu, I'll take a look then.  :)

When I say that it seems to "recognize" the files  and folders, I mean that it mounts the file system and seems to be able  to provide a list of contents (at least it does with Caja). However it  takes a looong time to do so, and every time you try to change folder or  to change the view or whatever it takes an enormous amount of time  (normally I go away to do something else and come back half an hour  later to check if it has shown the contents of the folder).

Since I did not have any clue what  else to do, simply  copying some of the files using Caja is what I have been attempting to do up to now. However, as I said, at the present speed this is going to take  several weeks, if not months, and I am not sure the hard disk will hold for that long.  That's why I wanted to use GNU ddrescue. Because I've read that, the way  it works, it saves on a first pass the blocks that it can access fast and easily,  and only later keeps on trying with the rest which are slow or have other problems. So I thought that would be the best way to maximize the amount of rescued data in case the hard disk fails during the process.

Occasionally,  it halts because of an error in a file, so I note down the file and  resume. But I always have the doubt of whether it has finally completely  stuck or it is still going on, because nor the progress bar nor the  numbers grow fast enough. It would be useful to know which particular  file is copying at that moment and see if it's growing in size.

I used Photorec in the past and, to be honest, I was not impressed. The whole thing was a mess, so I'll leave it for a last resort.

> Well, I didn't think you could... but my google fu led me to this exact  problem that someone asked ddrescue's author a decade ago

That's swell! It was exactly what I was looking for!   :)

I was already expecting GNU ddrescue not to work with folders out of the box, because it didn't mention it in the manual, but I was hopeful to be able to use a terminal script or something of the sort to browse through the files and then ask GNU ddrescue to take care of those, which is essentially similar to what you suggest, right? However, I am not familiar with such scripts in order to automatize the process for files and folders recursively, that's why I was hoping to find an example somewhere.  :)

Well, at the very least I'll be able to use the file command with the files that are giving errors on copying with Caja.

> The problem  with that method is, if the disk is truly failing, the "find" command  would fail and quit.

Would it work if I first was able to build a text file with a list of the files? They could have the path and then maybe I could read the lines of the file recursively to introduce that whole path in the terminal command "calling" GNU ddrescue? What do you think?

Also, to be honest, I am also quite confused by the fact that there are  two programs called ddrescue (well, ddrescue and GNU ddrescue, but both  of them are called in the terminal by ddrescue), so I am never sure if  people are talking about one or the other.  :P

[https://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue#211579](https://askubuntu.com/questions/211578/whats-the-difference-between-ddrescue-gddrescue-and-dd-rescue#211579)

Thanks!

     Margaret

---

### Post by untrustytahr on 2017-10-20
> **Margaret Dumont said:**
> 

I was already expecting GNU ddrescue not to work with folders out of the box, because it didn't mention it in the manual, but I was hopeful to be able to use a terminal script or something of the sort to browse through the files and then ask GNU ddrescue to take care of those, which is essentially similar to what you suggest, right? [COLOR=#ff0000]** Yes**[/COLOR]

However, I am not familiar with such scripts in order to automatize the process for files and folders recursively, that's why I was hoping to find an example somewhere. **[COLOR=#ff0000]This sounds suspiciously like someone asking for a script to do it for you. Am I right?[/COLOR]**:tongue:

Would it work if I first was able to build a text file with a list of the files? They could have the path and then maybe I could read the lines of the file recursively to introduce that whole path in the terminal command "calling" GNU ddrescue? What do you think? [B][COLOR=#ff0000]Yes, this is certainly a possibility. You could read in the filenames in a while loop.
[/COLOR][/B]


So first things first.  I haven't used ddrescue. I've only read some of the manual.  One of the first warnings is that it is best to not work on a mounted read/write drive as it may make the disk worse. /end disclaimer

I would probably do something like this:

```

#!/bin/bash

shopt -s globstar


for file in ** 


do
	if [ ! -d "$file" ] 
	then
	  printf "STARTING FILE: %s\n" "$file"
	  ddrescue <options> "$file"  /path/to/recovery_device/"${file##*/}" mapfile_"${file##*/}"
	  printf "FINISHED FILE: %s\n\n" "$file"
	fi
done

```

You would have to decide on which options to run ddrescue with as well as the target destination.  This is not really an efficient way to do it... it handles everything as an individual file (including the mapfile-that's alot of mapfiles).  The destination will also overwrite file names with the same name as it is putting them all in the same destination.  It should give you some idea of how to do it.

---

