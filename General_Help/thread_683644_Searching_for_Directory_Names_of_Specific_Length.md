---
title: "Searching for Directory Names of Specific Length"
date: 2008-01-31
forum: General Help
---

### Post by mkwerner on 2008-01-31
Greetings all,
If I've posted this in the wrong section, I apologize for that...I've been a long time reader, but I've never posted my own thread.

Anyway...

I have a huge directory of music with tons of subdirectories...and under those, there are even more!  What I'm trying to do is this:

I want to search for directory titles of a specific length under the master directory...not file names, but directory names.  For instance, I'd like to generate a text file of all directories whose names are greater than 30 characters.  Is this possible?  

I was reading the find man page yesterday, and while you can specify "type -d" for directory, there didn't seem to be an option for name character count.  Other than that, I'm not very good with scripts, so I wouldn't even know how to spec out something like this.

I appreciate any / all suggestions, even if it's, "Sorry man, you can't do that.

Thanks for your time, and have a great day!

Cheers,
M.

---

### Post by Fraktyl on 2008-01-31
Unfortunately, it would have to be some type of shell script.  Look at it this way, it's another neat little trick you can learn.

Off the top of my head, you could do something like this:
```

#!/bin/bash

NUM=5

for i in `find . -type d -printf "%f\\n"`
do
   LEN=`echo $i | wc -c`
   [ $LEN -eq $NUM ] && echo $i
done

```Cut and paste that into a file.  Then cd to your MP3 directory.  Run the script.  You can change the NUM=5 to be the length of what you're looking for.  This will only find things of the exact size.  If you wanted to find things that were at LEAST the size of NUM, then change the -eq to -ge.

The script also has to be somewhere in your path, or you'll have to type the full name to the place you saved it.  I think $HOME/bin is normally part of the path, so you could save it there.

This will only print the final directory name.  It strips off all the proceeding directory names from it.  So /mp3/Scooter/The Stadium Techno Experience would only show: The Stadium Techno Experience.

Like I said, it's pretty basic, but should give you some starting points.  Check the man page on find for other examples of the -printf statement.

---

### Post by mkwerner on 2008-01-31
Fraktyl,
Thank you so much for your response - that's all I was looking for...a starting point.  I spent so much time yesterday seeking that out...and you were able to provide it for me!   No worries on using a shell script - I'm comfortable enough with it.   

Much thanks - I'll try it when I get a break (at work) and let you know how things go!

Again, thank you very much!

Take care,
M.

---

