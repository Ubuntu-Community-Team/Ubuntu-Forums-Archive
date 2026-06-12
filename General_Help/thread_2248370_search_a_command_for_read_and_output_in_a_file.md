---
title: "search a command for read and output in a file"
date: 2014-10-14
forum: General Help
---

### Post by martin19882 on 2014-10-14
Hi,

nice that I can be there.. i hope people can help me.

I am looking for a command that outputs the following to me:

the command should search in all directories and all subdirectories who calls directory.ssb and after finding all these  directories 
they should look into the directories and should find the all files who calls: 
.XYZ . than they have to look into this file.
if in that files is:  " blabla " than it's OK,  If NOT then write this path into the file( outputting me in a file) .

Then I can look at this file and see all the paths who have not blabla in the files .XYZ
hope that was understandable .

thanks in forward

---

### Post by tgalati4 on 2014-10-14
Welcome to the forums.

I'm not familiar with the use of the term *blabla*.  Perhaps you mean [foobar]("http://en.wikipedia.org/wiki/Foobar").

There is the *find* command.

```
man find
```

It is used as follows:

> tgalati4@Mint14-Extensa ~ $ cd
tgalati4@Mint14-Extensa ~ $ find Music
Music
Music/Mamas_Calling.mp3
Music/The_Good_Bad_Ugly.mp3
Music/Freenas_Music
Music/Adam-Lambert-Mad World.mp3
Music/Podcasts
Music/Podcasts/show_6663043.mp3
Music/Western_Guitar.mp3
Music/Good_Bad_Ugly.mp3
Music/03 Summer Day.mp3
tgalati4@Mint14-Extensa ~ $ find Music >> Music_directory_files.txt
tgalati4@Mint14-Extensa ~ $ cat Music_directory_files.txt 
Music
Music/Mamas_Calling.mp3
Music/The_Good_Bad_Ugly.mp3
Music/Freenas_Music
Music/Adam-Lambert-Mad World.mp3
Music/Podcasts
Music/Podcasts/show_6663043.mp3
Music/Western_Guitar.mp3
Music/Good_Bad_Ugly.mp3
Music/03 Summer Day.mp3


---

### Post by TheFu on 2014-10-14
No it is not clear. Sorry.

The use of "who calls" is unclear to me.  Please explain.  Do you mean "named" that or with text inside containing those characters?  Also, searching binary files for strings will be slow. If you are looking for method names or function calls, then there are better ways to search libraries.

This will get you the first part ... 
```
find / -type d -iname directory.ssb
```

Might be useful to look through the "advanced bash scripting guide" to figure out the rest. Google will find that free document.

---

