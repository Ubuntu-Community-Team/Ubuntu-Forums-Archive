---
title: "How to Reduce Size on Disk"
date: 2013-07-07
forum: General Help
---

### Post by Iggy64 on 2013-07-07
Forgive me if this has been asked and answered.  I expected to find an answer by search, but had no luck.  Please point me to it if I simply missed it.

I've been converting to Linux from Windows over the past year.  Now I notice that my files are taking up a lot more room than I expected.  For example, a collection of mp3 files in a directory "Oldies" has
File Size = 98.9 GB
Size on Disk = 791 GB
Most of these files are about 3 to 5 MB in size.
The file system is NFTS.
Another directory on the same disk is "Classical," and it has
File Size = 506.2 MB
Size on Disk = 4.1 GB
These files are bigger, typically 10 to 40 MB.

Another example, on another drive, is directory "Music Box": 
File Size = 11.3 GB
Size on Disk = 90.3 GB
These again are mainly 5 MB mp3 files.
This file system is ext4.

I have many more examples, on ext4 systems and on NTFS.  I seem to be consuming a tremendous amount of overhead here.  That is, the Size on Disk is 8 to 10 times bigger than the files themselves.  Is this due to having block sizes that are too big?  What - if anything - should I do about this?  Most of the files I'll be dealing with are 4 MB mp3 files or 30 MB WAV files, along with assorted txt and pdf files (also small).  Am I misinterpreting what Size on Disk means?  When I worked in Windows, the difference between Size and "Size on Disk" was generally quite small.

---

### Post by Iggy64 on 2013-07-07
Having continued to search for answers elsewhere, I have read that my use of PCManFM may be the problem.  Various people on other forums have reported the identical problem with Size on Disk reported by PCManFM.  

I will study up on how to get correct disk usage info via the CLI.  

I apologize that I did not provide enough information with my question, and that I did not do enough research before posting it.

I will report back if I can find out the correct numbers for my disk usage.

---

### Post by vasa1 on 2013-07-07
> **Iggy64 said:**
> ...
I apologize ....
Hey! Your question was pretty decent compared to several others we see here so no need to apologize! And you came back and clarified. That again is not that common but certainly welcome.

---

### Post by Bashing-om on 2013-07-08
Iggy64; Hi !

You might investigate the "df" command:
```
man df
```
and instance of usage:
```
df -h
df -h /home
df -h /var

```
[INDENT][INDENT]keep'n it simple
[/INDENT][/INDENT]

---

### Post by Dennis N on 2013-07-08
The size on disk numbers are erroneous and happen in older versions of PCManFM. Use PCManFM version 1.0 or higher where the problem is fixed. This means Quantal or Raring releases.

Tip: You might also find Disk Usage Analyzer to be a useful utility.

---

### Post by Iggy64 on 2013-07-08
My thanks to vasa1 for making me feel a little bit less embarrassed.  I normally do a ton of research trying to find an answer before posting a new question.  I think this time I panicked a little bit, searched the Ubuntu Forums, and then posted.  Anyway, thanks for your kind response.

To Bashing-om, who so often has excellent advice to offer, I send my appreciation for the appropriate shell commands.  I had started exploring the df and du commands, going through their man pages.  It seems you have confirmed that I am on the right track.

And Dennis N, that is very helpful info regarding the newer versions of PCManFM.  I will look into upgrading.  And I will take a peek at the Disk Usage Analyzer.  The above-mentioned shell commands will likely serve many of my needs; but I would welcome having a graphical display when I am doing big-picture moves like re-organizing directories or backing up major portions of a disk.

Thanks to all for these kind responses.  I am truly enjoying my migration into Linux.  It challenges me a lot, but friends on this forum make it so much easier.

---

### Post by Bashing-om on 2013-07-08
Iggy64;

We are all in this together.But, I do appreciate the compliment, I try but I do err on occasion !
In respect to looking at a disk with partitioning and usage on your mind..graphically, in my experience there is no substitute for GParted.
GParted is available on the desktop liveDVD, use with discretion as there is no forgiveness of a mistake !
looking can not hurt; but before you push that button, be aware of what !

[INDENT][INDENT]if you break it, you fix it ->ubuntu[/INDENT][/INDENT]

---

### Post by Slim Odds on 2013-07-08
> **Bashing-om said:**
> Iggy64; Hi !

You might investigate the "df" command:
```
man df
```
and instance of usage:
```
df -h
df -h /home
df -h /var

```[INDENT][INDENT]keep'n it simple
[/INDENT]
[/INDENT]

Actually, for stuff like this you want the 'du' command. Disk Usage.

---

### Post by Bashing-om on 2013-07-08
Using the "du" command: very true, Explaining though to a "new user" gets complicated:
My Favorites, as examples:
```
du -h /home | sort -nr | less
##or
du -h --max-depth=1
##getting deeper
du -h --max-depth=1 | sort -hr

```
As with most linux commands, can be as complex as the situation demands.
"Try 'du --help' for more information."

"sudo" may be employed with extreme caution only as required.

Having the need for direct application ... most effective in finding large space consuming files within directories or such.

'buntu is flexible in looking at the file system ..any others means

[INDENT][INDENT]even now, the CLI reveals most[/INDENT][/INDENT]

---

### Post by 1clue on 2013-07-08
For music or photos the typical culprit is the app that copies stuff from your phone or camera every time you connect it.

Check into 'fslint'.  It's an app that looks for duplicate files and other filesystem undesirables and then lets you choose whether to do something about them.

The typical solution for duplicates is to replace all copies of a certain file with a single file and make hard links from the others.

The only caveat is that if you have a bunch of backups or copies of a file, then do fslint, and then edit one of the files, you edit all of the files on that filesystem because they are the same actual file.

So if you do this, you want to keep your backups on a separate drive from your "live" copies if you plan to edit them.

---

### Post by Iggy64 on 2013-07-08
My thanks to Slim Odds and to Bashing-om (again!) for details on both df and du commands.  Remarkably, I read through the man pages for both earlier this evening, and started playing around with them.  The fact that both of you have suggested these and provided examples I could understand makes me feel good that - for once- I was on the right track.  So I am fairly convinced that, in most simple cases, I can use these commands to check disk usage.  

In other situations, when I am trying to get a better overview of a disk (for backup or downsizing purposes), I will likely resort to Disk Usage Analyzer.  I was able to install that as a single package, bringing in no extra baggage.  It does provide a nice overview of where the GBs are going.  GPartEd looks like it gives good overviews as well; but - as an editor - I would have to be very careful with it.  It's a tool I may need someday, though; so I'll make time to learn more about it.  I sure do appreciated all this advice.

And 1clue, thanks for your ideas on potential causes of storage creep.  I do store tons of music, swapping it around from one drive to another, back and forth.  Right now, I don't seem to have a lot of duplicate buildup; but that is certainly something that could happen down the road, especially as I pick up speed working with Linux.  

Thanks, again, to all for the friendly advice.

---

