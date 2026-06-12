---
title: "[SOLVED] batch rename with bash and tricky filenames"
date: 2007-10-07
forum: General Help
---

### Post by jimmywu013 on 2007-10-07
Hi,

I have a bunch of files with names that begin the ' (the single quote character) and include spaces.
I want to rename them all to just remove the ', but everything I've tried in bash seems to not like the ' character, and the spaces in the names aren't helping either.

ls \'*|cut -c 2- does output the correct new names, but I have no idea how to get mv to know that
mv `ls \'*` `ls \'*|cut -c 2-` doesn't work: i get an error that target filename \'xxxx is not a directory

I really don't want to have to do all this renaming by hand.

Thanks in advance for any suggestions,

Jimmy

---

### Post by Old *ix Geek on 2007-10-08
The following should work.  To test it, I prepended apostrophes onto a bunch of files' existing names, so they looked like this: 'dcp_012345.jpg.  You mentioned having spaces in the names as well; depending on where those are (e.g., between the apostrophe and the first alphanumeric character), it may take some tweaking.
```
for file in \'*jpg
do cp $file ${file#\'}
done
```

Here's a brief listing before:
```
$ ls -C
'dcp_0917.jpg
'dcp_0918.jpg
'dcp_0919.jpg
'dcp_0920.jpg
'dcp_0921.jpg
```

and after:
```
$ ls -C
'dcp_0917.jpg
dcp_0917.jpg
'dcp_0918.jpg
dcp_0918.jpg
'dcp_0919.jpg
dcp_0919.jpg
'dcp_0920.jpg
dcp_0920.jpg
'dcp_0921.jpg
dcp_0921.jpg
```

Note that I **copied** and not **renamed** the files--and I strongly suggest you do the same!  (Or make sure you have the files backed up somewhere else.)

There are ways to eliminate the spaces, too, so if you decide you want to do that and need help, post a followup!

---

### Post by HermanAB on 2007-10-08
You can do things like that with the find command.  Find can recurse through directories and look for patterns, then when it finds a match, execute a program to do something.

This example is from my music repository.  It will find .ogg files and convert them to .mp3:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

The syntax is rather obtuse.  Read the man page a few times.

Cheers,

Herman

---

### Post by jimmywu013 on 2007-10-08
I tried the for loop Old *ix Geek suggested, but it isn't working.  I think it's because of the spaces in the filename.  For example, if all the files are name 'blah blah finalblah.ext I get a string of cp: target `finalblah.ext' is not a directory.  ](*,) :confused:
Also, just wondering - what exactly does the # you put in the cp do?

As for the find command, I'm not sure how I would change the filename even with an -execdir cp.  If I understand correctly, {} gets replaced by the file name, but how would I modify the filename with that?.  

If you haven't noticed, I'm quite a noob at this (have only been using Ubuntu for ~3 months). Thanks for all the help

Jimmy

---

### Post by jimmywu013 on 2007-10-08
**[SIZE="2"]Update:[/SIZE]**

After a bit of experimentation, I tried the following, and it seems to work

```
for f in \'*; do cp "$f" "20`echo $f|cut -c 2- -`" ; done
```

I don't think this is the most elegant or efficient way to do this, so I'm still willing to hear any suggestions.
The 20 is in there because I wanted to prepend it to each filename (the names are actually years except instead of 20xx, they're named 'xx, which I thought was stupid, so I decided to change it)

The next question is how would I go about stripping the spaces out of the filenames?

Thanks again,

Jimmy

---

### Post by Old *ix Geek on 2007-10-08
I wish I could take credit for this, but I can't!  I found a script online that will do exactly what you need; it's [[COLOR="Blue"]**_the first script[/color]_**](http://penguinpetes.com/b2evo/index.php?title=howto_fix_filenames_on_linux&more=1&c=1&tb=1&pb=1) on this page.  I tested it with your scenario and it worked without a hitch.

---

### Post by jimmywu013 on 2007-10-08
Thanks for that link.
I like the for loop in the comment better than the huge script - it's shorter and simpler

Here's a tougher problem:
I ran across a folder where the dates were on the end, so that they look like this
blah blah 'yymmdd.ext

I've already replaced all spaces with _ (underscores).
Now the question is, how do I replace the ' with 20
I can't use a simple sed y/x/x/ because I'm trying to replace one character with two.

PS
I've done a bit of string mangling in php, which has a lot of very nice regular expression/string manipulating routines.  For this task, a simple string replace function would do.  If only bash had as much -- or does it?  I am still very much a newb

Appreciate all your help

Jimmy

---

### Post by Old *ix Geek on 2007-10-08
> **jimmywu013 said:**
> Here's a tougher problem:
I ran across a folder where the dates were on the end, so that they look like this blah blah 'yymmdd.ext

I've already replaced all spaces with _ (underscores).
Now the question is, how do I replace the ' with 20
I can't use a simple sed y/x/x/ because I'm trying to replace one character with two.
By using a combination of that script I pointed you to, and **sed**, I was able to do what you need. :)

Start with: ```
ls blah* > old
```to capture the current file names in file **old**. Here's mine:
```
$ cat old
blahblahblahA'071208.jpg
blahblahblahB'071208.jpg
blahblahblahC'071208.jpg
blahblahblahD'071208.jpg
blahblahblahE'071208.jpg
```
Next: ```
cat old | sed -e "s/'/20/g" > new
``` to change the apostrophes to **20**, and store them in file **new**; here's mine:
```
$ cat new
blahblahblahA20071208.jpg
blahblahblahB20071208.jpg
blahblahblahC20071208.jpg
blahblahblahD20071208.jpg
blahblahblahE20071208.jpg
```
Finally: ```
FILECOUNT=$(wc -l old | awk '{print $1}')
LOOP=1
while [ "$LOOP" -le "$FILECOUNT" ]
do AWKFEED="FNR=="$LOOP
OLDFILE=$(awk $AWKFEED old)
NEWFILE=$(awk $AWKFEED new)
mv "$OLDFILE" "$NEWFILE"
LOOP=$(($LOOP+1))
done
```to rename the actual files.  **ls** should now yield:```
$ ls
blahblahblahA20071208.jpg
blahblahblahB20071208.jpg
blahblahblahC20071208.jpg
blahblahblahD20071208.jpg 
blahblahblahE20071208.jpg
```

---

### Post by jimmywu013 on 2007-10-09
Thanks.  I'm not at my Ubuntu computer right now, but I'll try that as soon as I get the chance.  I think I'll go learn more about this 'awk' as well.

Thanks again for the help!

Jimmy

---

### Post by jimmywu013 on 2007-10-09
I'm finally sitting at my Ubuntu box

Once again, I was lazy and instead of creating a script, I opted for the one liner for-loop.  I used the sed command you showed me, and it worked fabulously.

I am going to teach myself awk one of these days.  

Thanks again for the help

Jimmy

---

### Post by Old *ix Geek on 2007-10-09
You're welcome.  I'm glad to hear it all worked out. :)  Definitely take some time to at least familiarize yourself with awk, sed, tr, and grep.  Those four tools have done more for me over the years than just about any others I can think of.  I'm RUSTY now, because I rarely write [interesting] scripts any more (I've been unable to work since 2003--and there aren't many really complex programming needs here at home!).  You should've seen me when I was actually good at it!

---

