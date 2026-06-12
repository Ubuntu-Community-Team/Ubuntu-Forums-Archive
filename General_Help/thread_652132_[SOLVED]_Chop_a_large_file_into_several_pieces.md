---
title: "[SOLVED] Chop a large file into several pieces"
date: 2007-12-28
forum: General Help
---

### Post by e_james on 2007-12-28
I want to repair an avi file but most av software won't process it because it's faulty and the rest get confused because they try to understand the corrupted structure. I am confident that I can recover most of the content if I can first break the file into pieces without regard to the type of file. I have one application so far which will cut out pieces but even it seems to pay attention to structure leaving me with several pieces, each with the original flaw.

Can anyone suggest a way to break up a 1GB file as pure data without trying to tidy up the start and end of each piece? I will consider Windows software as well as Linux. 

I can probably write my own application, if absolutely necessary, but maybe I don't need to reinvent that wheel.

---

### Post by ghostdog74 on 2007-12-28
how about split? go to terminal, type man split.

---

### Post by SOULRiDER on 2007-12-28
> **ghostdog74 said:**
> how about split? go to terminal, type man split.

I was gonna suggest that. A couple of days ago someone posted with the same issue. The solution was to use the split and join commands but there were also other graphical apps that could do this. I suggest you search for the thread and see if you get any good ideas :)

---

### Post by e_james on 2007-12-28
Thankyou both for the suggestions. I will have a look at split and join. I thought there would be something straightforward but I didn't know where to start.

---

### Post by nick_h on 2007-12-30
You can combine the split files with the *cat* command.

---

### Post by e_james on 2007-12-30
nick_h

Thanks for that suggestion. I haven't had time to try out the split yet but I did look at the command syntax for *split* and *join*, and it seemed to me that *join* only works for text files.

---

### Post by ~LoKe on 2007-12-30
Split and join are not to be used together, as far as I've read.

---

### Post by dlegend on 2007-12-30
I know for Windows they have a program called "AVI Preview" found here: [http://www.avipreview.com/](http://www.avipreview.com/)

It allows you to view incomplete AVI files which may work for you.

---

### Post by dagnabit dang doohickey on 2007-12-30
lxsplit makes splitting and joining a breeze. A Debian i386 package is available for download [here]("http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/lxsplit.php").

This is the part of the lxsplit README explaining usage:
> 
LXSplit is capable of splitting and merging files, with the -s and -m flags respectively.

Example:
To split a huge file into smaller pieces of 15MEG each, you would invoke the following command:

 > lxsplit -s hugefile.bin 15M

Output sized can be given in (M)egabytes, (k)ilobytes and (b)ytes.

Merging smaller pieces into one big file is done by invoking this command:

 > lxsplit -j smallfiles.bin.001

All resulting files (from either splitting or joining) will be placed in the current directory.


---

### Post by nick_h on 2007-12-31
> I did look at the command syntax for split and join, and it seemed to me that join only works for text files.

Yes, use *cat* instead of *join*.  For example:
```
split -b 10m xxx.avi xxx_
cat xxx_* > yyy.avi
rm xxx_*

```

This splits the file xxx.avi into xxx_aa, xxx_ab, xxx_ac, etc...
Then it combines it again into yyy.avi
Then you can delete the individual pieces with an rm command. (Be careful that you don't happen to have any other files starting xxx_ :) )

---

### Post by krussell on 2007-12-31
Hi:
I use a nice windows based software for this.
It is called "The File Splitter", google it and you can find many free splitters in the web.
Then use wine to run Flie Splitter. It works like a breeze.

Thanks

---

### Post by e_james on 2007-12-31
Thanks to all for the suggestions. It will take several hours of processing for the whole file and I'm not ready to commit one of my PCs to that job right now, but the progress so far looks good. Since the repair programme (VirtualDub) runs in Windows, "The file splitter" was the obvious procedure to test first but I expect "split / cat" and "lxsplit" would achieve similar results. It takes a little bit of lateral thinking because I don't actually want equal sized pieces. I wasn't sure in advance but it is essential to concatenate a header section with each piece before the repair process.

I think I can safely mark this thread solved.

---

### Post by nick_h on 2007-12-31
If you need to take a header off a file and put it in another file then you might want to look at the *head* command.

---

### Post by e_james on 2007-12-31
*Head* appears to be a command to display the first few lines of a text file. Am I missing something?

This is the strategy which seems to be working so far.
-First I break the file into 6 x 150MB pieces. 
-VirtualDub will repair the first section by recreating the index and fixing the header and footer as necessary but it can't do anything immediately with the other sections because there is no header to fix. 
-Using VirtualDub editing facilities I cut about 1 minute of recording from the start of the first section and then I split this into 2 pieces. Now I have a "broken" header section.
-Using The file splitter reassembly tool I attach this header to section 2 etc. These can then be repaired.
-When I have repaired all the sections as 6 separate avi files VirtualDub can reassemble them into a single avi file.

Unfortunately there appears to be significant data corruption in some of the sections and it is a characteristic of video software that data corruption can crash the application or even the computer. If the corrupted areas are small enough, I can cut them out and salvage the remainder but, if the corruption is too extensive, I will probably give up.

Edit
So far I have recovered the first 80 minutes of a possible 120.

---

### Post by nick_h on 2008-01-01
It looks like you have sorted the problem anyway, but I was thinking *head* would be useful to manipulate the header.  If you knew how big the header was (say 200 bytes) you could have used something like:

```
head -c 200 part1.avi > header
cat header part2.avi > new_part2.avi
```

---

### Post by e_james on 2008-01-01
nick_h

I **was** missing something. I just had another look at the command options and it seems that, by using *head* and *tail*, I could cut any file into unequal sections. For now I will press on with the current strategy but your alternative could turn out to be very useful, especially for cutting out the corrupted data. Thanks for the idea.

---

### Post by dagnabit dang doohickey on 2008-01-01
You might want to take a look at the video repair tools [here]("http://www.videohelp.com/tools/sections/video-repair-fix").

---

### Post by e_james on 2008-01-02
dagnabit dang doohickey

Thamks for the link. It's an interesting collection. The consensus of the reviews seems to be that no one tool deals with all problems. Having tried one or two, I'm inclined to agree. The cutting procedure is still beneficial.

---

