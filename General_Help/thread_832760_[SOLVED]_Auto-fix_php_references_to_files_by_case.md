---
title: "[SOLVED] Auto-fix php references to files by case"
date: 2008-06-18
forum: General Help
---

### Post by SonicComKid on 2008-06-18
I have a real problem that I'm sure a shell script can make quick work out of, but something this advanced is WAY out of my league.

Here's the problem: I have tons of php files that were used on what was previously a windows server, which doesn't care about the case of files. A lot of the php files for example would make references like /blah/This  as opposed to /blah/this   When I moved all the files to my Ubuntu server, the first thing I did was fix the names of all the files so that they're all lowercase like they should be, but the php files are still trying to reference them with random case all over the place, and manually editing the php files would take days to do since there's so many of them.

Is there some way I can generate a list of all the files in my htdocs folder, then having it use all those entries as reference to search inside the php files for those filenames at any case, and replace them with the file in lowercase?

ie. if it came across /blah/This.jpg  it'll change the php file's entry to /blah/this.jpg

I'll need the script to recursively go through all the subfolders under htdocs as well to fix all the *.php files. If someone can make such a script you deserve the title linux guru.

---

### Post by maddog39 on 2008-06-18
This seems like a bug in your script rather than a filesystem or other misc problem. Also no shell script will likely be able to interpret your specific source code and then polymorphically change it. What is definately the case is that you're references to these files in a database, flat file, or other data store are still using case insensitive names. You mention that these references are stored in php files which makes absolutely no sense to me because if they arent static then why arent you storing them in a database or atleast as a list of path's in a plain text file. The best way to solve the problem I presume would be to recreate these lists entirely from scratch. You could do this by creating another PHP script and utilizing the glob() function to get directory file listings.

---

### Post by SonicComKid on 2008-06-18
You missed my point completely. I have an entire website made that was originally made in a microsoft server, and as you know microsoft doesn't care about case in filenames.

I have a lot of phpfiles that do things like load images, include other php files, etc. but those references have capital letters in them like include (Nav.php)

Obviously, php files are just plain text files. I need a script to go trhough all of my php files, look for any text in them that reference one of the files in my directory tree such as 'nav.php' and fix the text in the php file from Nav.php to nav.php

The problem is there is a LOT of php files, and a lot of references to images, other php files, etc. etc.

I need a way to mass fix all of these files, or else it'd take weeks to manually read and correct every single php file.

---

### Post by geirha on 2008-06-18
I've made a small script that might do the job. I haven't tested it much, so please make sure you keep a backup handy, and preferably, do it on a seperate tree first. It's hard to make a script that handles every conceivable case, but this should take care of most of them I think.

Assuming your htdocs is at /var/www/htdocs
```

$ cp -a /var/www/htdocs /tmp/htdocs
$ cd /tmp/htdocs
$ bash /tmp/replace-script.bash

```

/tmp/replace-script.bash:
[php]
#!/bin/bash

# create a temporary file
tmpfile=$(mktemp)

# Recursively find all files in the current folder, and make replacement 
# commands for sed. They will look something like: 
# s/\<this.php\>/this.php/ig
find . -type f -printf 's/\\<%f\\>/%f/ig\n' >"$tmpfile"

# Recursively find the php-files we need to change, and do the search
# and replace on them.
find . -type f -name "*.php" | xargs sed -i -f "$tmpfile"

# delete the temporary file
rm "$tmpfile"
[/php]

Please let me know how well (or bad) it does!

---

### Post by cariboo on 2008-06-18
You may want to try someplace like this:

[http://codingforums.com/forumdisplay.php?f=6](http://codingforums.com/forumdisplay.php?f=6)

because what you are asking is way beyond the scope of this forum.

Jim

---

### Post by SonicComKid on 2008-06-18
geirha, I'm not an expert, but reading your script code, is this only trying to correct references to php files inside other php files? because there's also images and various other things the php files are pointing to that may be messed up.  In the plain text of the php file, it's referenceing files by their messed up cased names like blah.com/LOGO.Jpg   I need the script to go around to edit the content of the php files to fix all references to files to lowercase changing them to things like blah.com/logo.jpg

EDIT: Geirha, yah, still didn't work with your current script. I edited index.php and it still says stuff like: 
<img src="images/DLNS-Logo.jpg" width="1024" height="180">
instead of: <img src="images/dlns-logo.jpg" width="1024" height="180">

cariboo907, I'm not coding PHP files. This is a Ubuntu bash script issue. I'm trying to fix errors in php files as though they are simple text files. I need to replace all text of file names to lowercase. so Blah.jpg for example in the code of index.php is changed to blah.jpg

---

### Post by geirha on 2008-06-18
assuming blah.com is a different server, then blah.com/LOGO.Jpg will not be changed, only local references should be changed.

Could you run the first find manually like this, and paste the output? 
```
find . -type f -printf 's/\\<%f\\>/%f/ig\n' | grep -i dlns-logo
```

My script assumes that all files in the htdocs-tree are allready in the correct case (lowercase).

---

### Post by SonicComKid on 2008-06-18
Sure thing, here's the result:

```
dafydd@zairserver:~/htdocs/dlns/dlns$ find . -type f -printf 's/\\<%f\\>/%f/ig\n' | grep -i dlns-logo
s/\<dlns-logo.jpg\>/dlns-logo.jpg/ig
dafydd@zairserver:~/htdocs/dlns/dlns$
```

Also, all file references are local. This is an enclosed website. There should be zero outside references. Also, I already ran a script that made all filenames in my entire directory structure under htdocs all lowercase.

EDIT: Side note - When I ran the script (by going chmod +x to the file when I make the script in nano and run it by typing ./replace-script.bash) it seems to just sit there and do nothing. I'm not sure though as it's hard to tell with my server, it's pretty old. However I left it running for a good half hour and checked a file it should have gotten to almost right away (being ~/htdocs/dlns/dlns/index.php) with me running the script in the ~/htdocs/dlns/dlns/ folder and index.php is completely untouched. I'm not sure if there's some easy way to make it verbose to see if it's working or not, but seems from this end nothing is happening. Because it's an old server I'll leave it running for a few hours or till your next reply, whichever comes first.

---

### Post by geirha on 2008-06-18
I can't quite figure out why it doesn't work for you. I've made a small test-case with your earlier example, and it works here.
```

$ find -type f
./images/dlns-logo.jpg
./test.php
$ cat test.php
<img src="images/DLNS-Logo.jpg" width="1024" height="180">
a link to myself? <a href="TEST.PHP">myself</a>
$ bash /tmp/replace-script.bash 
$ cat test.php
<img src="images/dlns-logo.jpg" width="1024" height="180">
a link to myself? <a href="test.php">myself</a>

```

---

### Post by SonicComKid on 2008-06-18
You replied before my edit, so here's just a quick repaste:
Side note - When I ran the script (by going chmod +x to the file when I make the script in nano and run it by typing ./replace-script.bash) it seems to just sit there and do nothing. I'm not sure though as it's hard to tell with my server, it's pretty old. However I left it running for a good half hour and checked a file it should have gotten to almost right away (being ~/htdocs/dlns/dlns/index.php) with me running the script in the ~/htdocs/dlns/dlns/ folder and index.php is completely untouched. I'm not sure if there's some easy way to make it verbose to see if it's working or not, but seems from this end nothing is happening. Because it's an old server I'll leave it running for a few hours or till your next reply, whichever comes first.


Just to make sure I'm following your instructions properly, I'll show you every line I type:

dafydd@zairserver:~$ cd /home/dafydd/htdocs/dlns/dlns
dafydd@zairserver:~/htdocs/dlns/dlns$ nano replace-script.bash
(I paste in the code, save with ctrl-O and exit)
dafydd@zairserver:~/htdocs/dlns/dlns$ chmod +x replace-script.bash
dafydd@zairserver:~/htdocs/dlns/dlns$ ./replace-script.bash

EDIT: Just to really make sure, here's confirmation of the code:
```
dafydd@zairserver:~/htdocs/dlns/dlns$ more replace-script.bash
#!/bin/bash

# create a temporary file
tmpfile=$(mktemp)

# Recursively find all files in the current folder, and make replacement
# commands for sed. They will look something like:
# s/\<this.php\>/this.php/ig
find . -type f -printf 's/\\<%f\\>/%f/ig\n' >"$tmpfile"

# Recursively find the php-files we need to change, and do the search
# and replace on them.
find . -type f -name "*.php" | xargs sed -i -f "$tmpfile"

# delete the temporary file
rm "$tmpfile"
dafydd@zairserver:~/htdocs/dlns/dlns$
```

---

### Post by geirha on 2008-06-18
I would've put the script somewhere outside the htdocs tree, but it should still work though. Here's a modification of the script, telling you which file it's editing. Depending on how many files you have there, it may very well take a very long time.

[php]
#!/bin/bash

# create a temporary file
tmpfile=$(mktemp)

# Recursively find all files in the current folder, and make replacement 
# commands for sed. They will look something like: 
# s/\<this.php\>/this.php/ig
find . -type f -printf 's/\\<%f\\>/%f/ig\n' >"$tmpfile"
echo "$(wc -l $tmpfile|cut -d' ' -f1) sed commands stored in $tmpfile"

# Recursively find the php-files we need to change, and do the search
# and replace on them.
find . -type f -name "*.php" | while read phpfile; do
  echo "Processing $phpfile"
  sed -i -f "$tmpfile" "$phpfile"
done
[/php]

Notice that I removed the line removing the tempfile, so you'll have a new file in /tmp each time you run it, but you'll be able to see what sed commands it will run for each php-file.

---

### Post by SonicComKid on 2008-06-18
It's working!! I'm watching this as it works, and it's logic is confusing me. Is it normal for it to skip a handful of items in the main folder and work on things in the sub-level folders first?, It did most of the stuff in the ../dlns/ folder minus index.php and a few others, then immedately started doing sub-folders

---

### Post by geirha on 2008-06-18
Glad to hear its working :)

It does it in whichever order find outputs those php-files, and I don't know how find decides the order. ```
find . -type f -name "*.php" | less
```

---

### Post by SonicComKid on 2008-06-18
okay. I'll wait it out and see how it gos. Assumeing all gos well. My greatest thanks! You litterally saved me weeks of painstaking annoying labour of having to go through huge numbers of php files to correct manually x.x'

Hopefully some day soon I'll manage to figure out exactly how your code works at that. Thanks again for your patience with me and incredibly useful script.

EDIT: No idea why, but index.php was the second last, but it is confirmed, it works flawlessly!

---

