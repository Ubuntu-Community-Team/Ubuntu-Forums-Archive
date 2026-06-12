---
title: "Disk space disappearing, delete files and space stays the same.  HELP!"
date: 2007-03-01
forum: General Help
---

### Post by caffienda on 2007-03-01
I recently installed Azureus and am now havind a major disk space issue.  I know that it allocated that disk space needed for a file download when you load a torrent by default, but that is not what the problem is.  

I had 16Gb free.  Installed Azureus.  downloaded a torrent that was 16GB, but only selected 3Gb of the torrent to actually download.  I also tried pointing the program to save the info on a separate hard drive other than my OS drive.  This didn't seem to work very well, so I went back to the OS drive.  Anyway, 20MB into the 3GB download, It said that the disk was full, and the computer got really slow.  

```
df -h
```said that 31/33 gigs was being used and it was at 100%.  I tried deleting a lot of files (about 12GB worth) and it has not cleared up any space.  There are no items in the trash.

I also have VMWare server installed and it stopped working due to lack of disk space. 

What do I do to free up space?  I have deleted as much as I can without seeing any room freed up with df -h:confused:

---

### Post by bodhi.zazen on 2007-03-01
Check your trash. It is a hidden folder in your home directory ;)

---

### Post by caffienda on 2007-03-01
the .Trash folder is empty:confused:

I tried finding large files with this:

```
find / -type f -size +20000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```


What about for a specific device? I am having a space issue with /dev/sda1 that is very suspicious. I'd like to see where the space is being allocated.
Is there a way to do this with a specific folder? Let's say just the /home/ directory.

---

### Post by annda on 2007-03-01
try du (disk usage)

```
du -h suspicious_directory
```

will give you directories size info in so called "human readable format". du -ah will include info on files as well.

```
du --help
```

gives you more options.

---

### Post by Peepsalot on 2007-03-01
[http://www.methylblue.com/filelight/](http://www.methylblue.com/filelight/)
This program can be used to find what is taking up the most space

There are some other similar programs too: kdirstat and another I can't remember right now.

---

### Post by caffienda on 2007-03-01
> **annda said:**
> try du (disk usage)

```
du -h suspicious_directory
```

will give you directories size info in so called "human readable format". du -ah will include info on files as well.

```
du --help
```

gives you more options.


Thanks for the tip!  I'm at a loss here.  I can't find ANY GB files, and I don't see anything over a GB TOTAL..

---

### Post by annda on 2007-03-01
what about plain old nautilus to see how the azureus storage folder is behaving? maybe azureus *forgot* to download only this one file out of many and reserved/took up all the 16 GB? and *forgot* to properly assign the filesize? i'm sorry if it sounds a bit unreasonable, but i learned from my own errors to try everything and look at everything from every angle.

or maybe it's not azureus after all?

---

### Post by caffienda on 2007-03-01
This may sound stupid, but I don't know how to load nautilus.

I also deleted the 3 Virtual machines that were taking up a lot of space, 20GB, and I have not noticed any more dissapearing space, although, I find it hard to believe that I have used 12G of space with a minimal install.

---

### Post by sgstarling on 2007-03-01
nautilus is your file manager, assuming you are using Ubuntu. You know, when you go to your home folder? That's nautilus. 

I know I know, many linux programs don't have their program name in the title bar, so your confusion is very understandable. If I'm ever in doubt, I usually find the program name in it's 'about' screen.

---

### Post by oranguman on 2007-03-09
sorry to bump this but I have a related question. 

to be more specific, caffienda, there are 2 .trash folders, one hidden under (username) directory, one hidden under the "root" directory. Modifying the latter, you have to open a window as root in nautilus (just like when you are "sudoing around" in the terminal, except graphical.) I do this by hitting "alt+F2" and typing "gksudo nautilus". 

another recent memory sink I found, caffienda, was opened because I was opening Virtual Desktops (in this case, Wine) with the "sudo" command, leading all my d/ls (and settings) for utorrent in a separate windows "profile". that dir was under ".wine", "c_drive", and "profiles". You are NOT supposed to open Wine as root, as far as I know. Hope that helps (someone.)


so anyhow, I found my .trashes, and deleted the files within the .root trash from a nautilus window. Great! 

Now, how can I make sure that I don't have to do this every time I try to delete a file?  and

Are there any other places in the system that cache files like this?

---

### Post by onetimeusername on 2007-03-14
I was having the same problem, under SUSE10 (sorry it's not Ubuntu...) and my "deleted" files were in a folder called /.Trash-1000/files. This may be SUSE-specific, but thought I'd add it in case anyone else googles "linux delete disappearing files" like I did and finds this page. :)

---

### Post by baqai on 2007-11-22
i am having the same problem, i deleted around 15gb of files from a ntfs partition (drive which i mainly use for downloads) and it still shows the space as 2.4gb

- i have checked both the trashes (my user and root)
- i have rebooted
- i have turned off ktorrent and checked trashes to see if ktorrent was somehow not letting the files delete

now the files are gone and i am stuck with 2.4gb of space :(

---

