---
title: "Graphical archive manager with advanced compression options?"
date: 2007-03-09
forum: General Help
---

### Post by Krakatos on 2007-03-09
Well, this is something that really bugs me, so I thought I would ask. Didn't find any recent topic about it anyway...
Due to work/productivity, I create many archives every day. Problem is, they are not always in the same location, so a script is not really a viable option. Now.... I would like to be able to set advanced compression options, depending on the format. 
And here comes the problem. Under windows just about any compression program gives you immediate access to all those options through a comfortable graphical interface. See 7zip, winrar etc. under linux... nothing, at least nothing I can see.
Tried file-roller, tried ark, but they simply don't let you choose the advanced options. For me at least, setting the level of compression, whether an archive is solid or not, and those nifty other options like passwords and such is important sometimes. And the spanning archives would be nice too !

So here I am, asking if anyone can point me to a graphical program that actually lets you do that. I really don't understand why something so basic is not available under the default programs of gnome/kde. 

And please don't tell me to use the terminal :P I'm looking for a graphical program :P And the terminal is not so nice anyway when you do something over and ove,r but the location change most of the times....

---

### Post by SuSUntu on 2007-03-09
Check out Xarchiver:

[http://xarchiver.xfce.org/screenshots.php](http://xarchiver.xfce.org/screenshots.php)

It's in the repos.

---

### Post by SuSUntu on 2007-03-10
Sorry for recommending what appears to me now to be a less-than-adequate piece of software. 

You can go ahead and check it out, but here's my assessment (I hadn't used it before now):

- the version in the Edgy repos is buggy. For example, the drag and drop function hangs without opening the 'add' dialog, then if you attempt to close the Xarchiver window, a status-bar message says, "You must first click the STOP button". *But the STOP button is grayed-out / inactive during the whole process*. The window had to be forced to close (I used the Force Quit applet).

- the compression is dog-slow

So, I compiled the latest version from the Xarchiver site (v 0.4.6) and:

- it is less buggy, e.g., the drag and drop now works

- the compression is dog-slow

Here's a less than thorough test scenario of the compression abilities:

Test file(s) = a .mozilla profile directory with added 4.8 rar file just for fun
Number of files / subdirs = 1313
Size = 134.7MB
Machine: AMD64 (all tests run on the same multi-boot computer) 

**7zip Tests**

- Xarchiver (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = 7zip
Compression: default
Output Archive Size: 55.3 MB
Time To Create: 3 min 09 seconds (yes, that says minutes! / Test conducted multiple times with same results + / - a couple of seconds)

- File Roller From Within Nautilus (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = 7zip
Compression: Default / Unknown
Output Archive Size: NA
Time To Create: NA
NOTE: File Roller could not create the archive - Error Output = WARNING: Cannot find 1235 files

- File Roller - Stand Alone (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = 7zip
Compression: Default / Unknown
Output Archive Size: NA
Time To Create: NA
NOTE: File Roller could not create the archive - Error Output = WARNING: Cannot find 1235 files

- Command Line (7z a -mx3 [archive] [directory])  (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = 7zip
Compression: 3 / Fast
Output Archive Size: 51.5 MB
Time To Create: 57 seconds

- 7Zip (on Windows XP SP2 / Partition Where Archive Created = FAT32)
Compression Algorithm = 7zip
Compression: Fast
Output Archive Size: 51.7 MB
Time To Create: 32 seconds

- IZArc (on Windows XP SP2 / Partition Where Archive Created = FAT32)
Compression Algorithm = 7zip
Compression: Fast
Output Archive Size: 50.6 MB
Time To Create: 61 seconds

**Tar.Gz Tests**

File Roller From Within Nautilus (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = tar.gz
Compression: Default / Unknown
Output Archive Size: 62.7 MB
Time To Create: 11 seconds

Xarchiver (on Linux Ubuntu Edgy 6.10 32-bit / ReiserFS)
Compression Algorithm = tar.gz
Compression: default
Output Archive Size: 62.7 MB
Time To Create: 24 seconds

**Conclusion**
I wouldn't use Xarchiver even though it does have a nicer set of features than file-roller. Guess it's back to the drawing board looking for a Linux GUI archiver with features **and** fast compression ability.

---

### Post by Krakatos on 2007-03-10
Nevertheless I thank you for the suggestion. I'll check the program myself, seems very easy to compile anyway. I must say I really don't understand why something so basic as to be a default in every single windows program I saw was never implemented on linux.

And I still hope maybe that someone does know a program that does what I need... maybe something not in the repos and that needs to be compiled....

---

### Post by Krakatos on 2007-03-10
Well I thought more about it.. aside from any other consideration, there's this thing I do not understand. So I'd like to ask about it too.
Xarchiver is supposed to be just a frontend right? So... how come it is actually slower? I'm doing the tests now, but ... how could it be slower than the command line? I mean, if it is a frontned, it's supposed to just use the command-line tool beneath, so theorically there should be absolutely no difference. Maybe itactually uses different switches from the ones you used?

---

### Post by SuSUntu on 2007-03-10
Your last post poses good questions. We'll need some programming gurus to suggest where the problem lies. I do note on the Xarchiver website that spped is referenced more than once:

[http://xarchiver.xfce.org/changelog.php](http://xarchiver.xfce.org/changelog.php)

Re: v 0.4.4
> 
- G R E A T L Y improved speed and memory usage.


Re: v0.4
> 
Increased speed ! Xarchiver is faster than ever when opening archives.


Why would speed be factored in to the changelogs of various versions of Xarchiver if it wasn't somehow modifying the speed of the underlying compression tools? Otherwise, I think it would say nothing or just say that Xarchiver is neutral in how it impacts speed. Hmm.

Anyway, the default [modifiable] settings in Xarchiver for 7z compression are:

- Recurse subdirectories: Unchecked (7zip man recommends not to use this - it does not do what one would normally expect it to do)

- Generate a solid archive: Unchecked

- Update an existing entry in an archive: Unchecked
 
- Password: Unchecked 

- Compression level: 5

You will note that my command line of

```

7z a -mx3 [archive] [dirtobearchived]

```

tries to match the Xarchiver options the best it can with known information except in one notable case, that being the compression level (Xarchiver = 5; 7z command line = 3). Normally, this would invalidate the test. But during testing, I noticed that if I set the non-Xarchiver tools to Comp Level 5, they where taking longer (as expected, but not as long as Xarchiver) but more importantly, they were producing files significantly smaller than Xarchiver at the same compression level. So, my compromise was to find the Comp Level in the non-Xarchiver tools that more closely approximated the final archive output of Xarchiver when it was set to Comp Level 5. I felt that the fairer comparison was between actual archive output file sizes as opposed to compression level labels (i.e., Xarchiver Comp Level 5 output size should equal Command Line Level 5 output size, but actually Xarchiver Level 5 more closely approximated Command Line Level 3 output size, so I used the latter in the command line).  

Here are those further comparisons to clarify the above:

Xarchiver: Comp Level 5 = 55.3 MB in 3 minutes 09 seconds (Originally Posted Data)
7z Command Line: Comp Level 5 = 47.1 MB in 2 minutes 16 seconds

Xarchiver: Comp Level 3 = 57.4 MB in 1 minutes 15 seconds
7z Command Line: Comp Level 3 = 51.5 MB in 57 seconds (Originally Posted Data)

As you can see, when the speeds of the two tools more closely match at a given Comp Level, the sizes are way off. And when the sizes are more closely matched, the speeds are way off. In any event, Xarchiver couldn't match the output of the command line in speed or size. I even tried to get closer to the 51.5 MB that the 7z command line achieved at Comp Level 3 by bumping Xarchiver up to Comp Level 7 & Comp Level 9:

Xarchiver: Comp Level 7 = 55.0 MB in 4 minutes 14 seconds
7z Command Line: Did not test Comp Level 7

Xarchiver: Comp Level 9 = 54.9 MB in 5 minutes 20 seconds
7z Command Line: Comp Level 9 = 45.6 MB in 2 minutes 6 seconds
Note: 7z Command Line at Level 9 actually beat it's Level 5 performance in both output size and time
 
So, it seems that Xarchiver hits a wall at ~ 55 MB whereas 7z command line can get down to 45.6 MB. That leaves more questions about why Xarchiver as a front-end produces such different results from the command line and other archiving tools. Maybe the author has used some obscure hard-coded switches that are slowing his implementation down, but even if that is the case, we can't change them because they haven't been made available to the GUI. 

Finally, regarding the Tar.Gz results from my first post: note that the output archive sizes for both Xarchiver and File Roller are identical (no options are available to change compression level anyway), but it took Xarchiver approximately twice as long (actually slightly more than twice as long) than it took File Roller to achieve that archive size. These results are probably more meaningful to most Linux users because Tar.Gz is more widely used.

Hopefully someone can explain the discrepancies more clearly or point out that my testing is flawed. Either way, I'm open to comments.  

The end. :)

---

