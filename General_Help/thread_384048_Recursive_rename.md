---
title: "Recursive rename?"
date: 2007-03-14
forum: General Help
---

### Post by grte on 2007-03-14
I'm trying to change the case of all files in a directory, but doing this one directory at a time is tiresome.

I use the command rename "y/A-Z/a-z", and having checked the manpages, found no option to do this recursively.  Is there some function of the perlexp that will do this?  Some other way?

---

### Post by Mr. C. on 2007-03-14
> **grte said:**
> I'm trying to change the case of all files in a directory, but doing this one directory at a time is tiresome.

I use the command rename "y/A-Z/a-z", and having checked the manpages, found no option to do this recursively.  Is there some function of the perlexp that will do this?  Some other way?

Here's a fun programming problem I gave to my students some time ago.  This will do you well:

See Week 10 Answers to homework: [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

---

### Post by peabody on 2007-03-14
from python:

Edit: AARG!  Never test unposted code, I fixed a bug.

old line was:
each_file = os.path.join(dirname, each_file)

that was wrong, below is right.

```

import os
for dirname, folders, files in os.walk('.'):
    for each_file in files:
        old_file = os.path.join(dirname, each_file)
        new_name = os.path.join(dirname, each_file.upper())
        os.rename(old_file, new_name)

```

---

### Post by silhouette on 2007-03-14
Or bash:

```

cwd="$PWD"

for dir in $@; do
   rename_recursive "$dir"
done

rename_recursive()
{
   cd "$1"
   for file in "$1"/*; do
      if [ -d "$file" ]; then
         rename_recursive "$file"
         cd "$1"
      else
         mv "$file" "`echo $file | tr A-Z a-z`"
      fi  
   done
}

cd "$cwd"

```

---

### Post by Mr. C. on 2007-03-14
How about some error checking !  All sorts of ways that bash script is going to create havoc.  Consider what happens to this poor guy's mp3 files such as "my poor old dog.mp3", or if the files to be renamed are "a b.mp3", "a.mp3" and "b.mp3".  (assume the above files are in uppercase).

MrC

---

### Post by grte on 2007-03-14
Alright, thanks for the help, guys.

And don't worry, MrC.  I only use underscores in filenames, and haven't got any one character song names, so I seem to be safe.

---

### Post by silhouette on 2007-03-14
[quote="Mr. C"]How about some error checking ! All sorts of ways that bash script is going to create havoc.[/quote]
Sorry, I haven't tested it as I'm not at a Linux machine right now - this was off the top of my head. I'm pretty sure it should work though, whether or not filenames have spaces in them, or the filenames are already lowercase, or whatever. Of course, use at your own risk, and modify as necessary.

---

### Post by Mr. C. on 2007-03-14
Right, understood, but let's be careful.  If this guy doesn't realize this or know about such problems, and uses it and losses his files...

The script has serious problems:

```
./goo.sh: line 4: rename_recursive: command not found
```

Once that's fixed, then:

```
./goo.sh a
mv a/* a/*
$ ls a*
a:
A\ B.mp3  A.mp3  B.mp3  a/
$ cd a
$ ../goo.sh *
../goo.sh: line 5: cd: A: No such file or directory
mv A/* a/*
../goo.sh: line 5: cd: B.mp3: Not a directory
mv B.mp3/* b.mp3/*
../goo.sh: line 5: cd: A.mp3: Not a directory
mv A.mp3/* a.mp3/*
../goo.sh: line 5: cd: B.mp3: Not a directory
mv B.mp3/* b.mp3/*
mv a/* a/*
```

Please test such code first.

MrC

---

### Post by silhouette on 2007-03-14
Very well, try something like this:

```
#!/bin/bash

rename_recursive()
{
   for file in "$1"/*; do
      if [ -d "$file" ]; then
         rename_recursive "$file"
      else
         dirname=`dirname "$file"`
         basename=`basename "$file"`
         newfile="$dirname/`echo $basename | tr A-Z a-z`"
         if [[ "$file" != "$newfile" && ! -f "$newfile" ]]; then
            echo "Renaming '$file' to '$newfile'..."
            mv "$file" "$newfile"
         fi
      fi  
   done
}

for dir in $@; do
   dirpath="$PWD/$dir"
   if [ -d "$dirpath" ]; then
      echo "Dir: $dirpath"
      rename_recursive "$dirpath"
   fi
done
```

Edit: yup, it's been tested

---

### Post by Mr. C. on 2007-03-14
Nope; care for another round ?

```

$ ls -l
total 12
drwxr-xr-x 2 mrc mrc 4096 Mar 14 20:44 a
drwxr-xr-x 2 mrc mrc 4096 Mar 14 20:44 a b
drwxr-xr-x 2 mrc mrc 4096 Mar 14 20:44 b

$ rename.sh *
$
```

Nothing.  Nada.  Zilch.

---

### Post by silhouette on 2007-03-16
Hmm, that's strange, it works for me. I did update it a bit but it probably won't fix anything on your end. You're not using something other than bash, are you? Either * should automatically expand to a list of filenames before the script takes over, or $@ should expand to a list of filenames within the for statement, but either way, the script should get a list of filenames to loop through.

Well, the OP seemed like they were able to figure it out. If they need a Perl script I can whip up one real quick.

---

### Post by Mr. C. on 2007-03-16
There are two problems with your script:
```

../doit.sh *
Dir: /tmp/test/a
Renaming '/tmp/test/a/*' to '/tmp/test/a/a a b b'...
Dir: /tmp/test/a
Renaming '/tmp/test/a/*' to '/tmp/test/a/a a b b'...
Dir: /tmp/test/b
Renaming '/tmp/test/b/*' to '/tmp/test/b/a a b b'...
Dir: /tmp/test/b
Renaming '/tmp/test/b/*' to '/tmp/test/b/a a b b'...
```

1) $@ isn't doing what you think it is.  You need "$@".
2) When a directory is empty, "$1"/* turns into the literal "emtpydir/*"

There may be other problems.

Lesson learned?  Handling quotes and recursive shell scripts with quotes is very, very tricky.

Lots of scripting lessons and explanations here: [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

---

### Post by bruenig on 2007-03-17
Everything here seems so complex, seems to me you can do it using a simple find command. cd into the directory with all the subdirectories that you are wanting to recursively rename and do:
```
find . -exec rename 'y/A-Z/a-z' {} \;
```

---

### Post by silhouette on 2007-03-17
Ah. Ingenious, those GNU people.

---

### Post by Mr. C. on 2007-03-17
> **bruenig said:**
> Everything here seems so complex, seems to me you can do it using a simple find command. cd into the directory with all the subdirectories that you are wanting to recursively rename and do:
```
find . -exec rename 'y/A-Z/a-z' {} \;
```

This would be a much better approach of course, if it worked.

* The terminating / on the end of transliteration is missing.
* *[ incorrect interpretation removed ]*
* It renames directories; the OP wanted files only (use -type f)
* It complains about empty directories

Traditional Unix did not have such a utility, so sometimes multi-platform solutions are required.  The solution also requires one to know about perl and its transliteration operation.

MrC

---

### Post by bruenig on 2007-03-17
> **Mr. C. said:**
> This would be a much better approach of course, if it worked.

* The terminating / on the end of transliteration is missing.
* This fails on path/file names containing spaces.
* It renames directories; the OP wanted files only (use -type f)

Traditional Unix did not have such a utility, so sometimes multi-platform solutions are required.  The solution also requires one to know about perl and its transliteration operation.

MrC

* The missing / is an oversight/typo, whatever you want to call it. 

* This does not fail on path/file names containing spaces.

* It does rename directories, but that can be fixed as you said with -type f  (I didn't read closely enough what he wanted).

Here is a revised  command that works per his specifications.
```
find . -type f -execdir rename 'y/A-Z/a-z/' {} \;
```
I did notice in testing this that the execdir is necessary with capitalized directories (again didn't read that he wanted to preserve capitalized directories).

---

### Post by Mr. C. on 2007-03-17
You're right about spaces- my error in going too quickly.

This is what I mistakenly thought was a spaces issue.  It is really an empty directory issue.

```
find . -exec rename 'y/A-Z/a-z/' {} \;
find: ./A: No such file or directory
find: ./B: No such file or directory
find: ./A B: No such file or directory
```

These types of errors are alarming to new users, as they don't know what they mean, and well written programs should not produce such output.

Your new version works fine.

MrC

---

### Post by bruenig on 2007-03-17
that is what 2> /dev/null is for
```
find . -type f -execdir rename 'y/A-Z/a-z/' {} 2> /dev/null \;
```

---

### Post by Mr. C. on 2007-03-18
Rather than deal with the errors, the errors are being tossed into the bit bucket.

You will never see errors when they occur, such as those generated when files cannot be renamed, or when other failures occur.  If you are going to use the find approach, don't add 2> /dev/null.

MrC

---

