---
title: "find broken links"
date: 2007-07-18
forum: General Help
---

### Post by Goliath! on 2007-07-18
Recently in debugging a problem on my laptop I stumbled across a way to locate all broken links on your machine.  I have cravenly stolen this from Mike Loukides in *Unix Power Tools* 1993 pg 294.  Then I adapted it to bash/Ubuntu syntax.

The problem I had was that Java was behaving very oddly (see [http://ubuntuforums.org/showthread.php?t=501918]("http://ubuntuforums.org/showthread.php?t=501918")).  I figured it had something to do with broken links involving either java or jre (java runtime environment).

So my first step was to find all the symbolic link files on my system whose names contained java or jre.  I used this:
```
sudo find / -type l \( -name "*java*" -or -name "*jre*" \) -print  2>/dev/null > a.a
```

find / -type l starts at the root / and looks for all files that are symbolic links (file type l).

The -name option further selects files by their name.  But I wanted files whose names contained java or jre, hence the -or option.  I needed to group the logical or together, or I got funny results.  But the parens ( ) needed to be escaped; hence the backslashes.

I think that nowadays -print is a default option but when I learned this stuff find was not smart enough to automatically print the names of the files it found, so you had to tell it -print.

That funky 2>/dev/null tells bash to not print any error messages (2 is the file number for standard error and /dev/null is a bit bucket).  Find normally prints a bunch of error messages for files it can't open or directories it can't read.  You want to get rid of those.

Note that I used sudo so that find could look in as many folders as possible.

Then I dump all that into a file called a.a.  That file contains a list of all symbolic links on my system with java or jre in their names.

But I only want the ones that are broken.  So then I use this:
```

sed 's/.*/if [ ! -e & ] ; then echo &; fi/' < a.a > a.b
```

sed is a very useful program for editing text one line at a time.  All that stuff within the single quotes is a command to sed.  In general s/something/something-else/ is a substitution of something-else for something.  The regular expression .* matches any line (. is any single character and * says match 0 or more of the previous thing).

So the sed command is going to take every line in a.a and replace it with that if statement.  The ampersand & is sed's keyword for whatever it matched (in our case, the whole line).  The [ -e & ] is true only if the file exists.  It just happens that if a symbolic link is broken, -e says it doesn't exist.  (The exclamation mark ! is a logical not.)

So what we're saying is that we're going to take every line of a.a and replace it with a new line that is a bash if statement.  That if statement will say "if the file doesn't exist, print its name."

We write all that out to file a.b.  So now a.b is a file of if statements - one for each broken link.

All we have to do is make a.b executable and run it:
```
chmod a+x a.b
./a.b > a.c
```

So now we have a file called a.c that contains the full file name (including path) for all broken links.  Voila!

Note that when you execute a.b you'll get errors if some of your file names are flakey (i.e., if the file names contain spaces or other characters that are special to bash).  If you get errors like that, just manually check to see if that link is broken.  Then remove that line from a.b.

You can combine all these statements into a single script if you need to.  To execute a.b use the source statement.

Enjoy!

---

### Post by stylishpants on 2007-07-19
This should handle filenames with spaces properly:

```
find . -type l -print0 | xargs -0 file | grep 'broken sym'
```

---

### Post by toga34 on 2007-09-22
this is what I get from last code... 

miguel@miguel-laptop:~$ find . -type l -print0 | xargs -0 file | grep 'broken sym'
./.mozilla/firefox/1o3iapen.default/lock:                broken symbolic link to `127.0.1.1:+5581'
miguel@miguel-laptop:~$ 

is that the broken link and if so how and where is it so that i may un-break, remove or what ever 
I have to do. I can not update, install or anything with out fixing broken kink...help please.

---

### Post by Goliath! on 2007-09-22
No, I don't think that file is the cause of your problems.  From what I have read, Firefox creates that lock file when it's running to lock your profile.

Try shutting down all instances of Firefox and then re-running that find statement.  I think you'll find your lock file is gone.

Can you be more specific about the symptoms you're getting?  What makes you think you have broken links?

Take a look at this (it might help solve your problems):[http://home.att.net/~cherokee67/ffwontstart.html]("http://home.att.net/~cherokee67/ffwontstart.html")

---

