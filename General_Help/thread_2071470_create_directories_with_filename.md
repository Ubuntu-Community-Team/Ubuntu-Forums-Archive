---
title: "create directories with filename?"
date: 2012-10-15
forum: General Help
---

### Post by sohlinux on 2012-10-15
I have a folder of 100 videos, they are all have various names for example

tom in usa.avi 
bill in uk.avi
fred.avi
jack_home.avi
fred_bill.avi

the question is how can I automatically create 100 new folders with the name of the video and move the video into that folder?

so for example the result will be a new folder called tom in usa containing the video tom in usa.avi

thanks

---

### Post by TheFu on 2012-10-15
There are lots of ways to do this.  First, if you remove the spaces in the filenames, your life will be much easier.  Perl includes a batch tool for that called "rename". It works on regular expressions, regex, for short.
**$ rename 's/ /_/g' ***
If there are name collisions, I think the old file will be gone.

Back to the first issue. I will not write a script for you.  Let's think about it a little in a step-by-step method.  A bash script can easily do what you need. 

First, a list of all the files you'd like to handle. There are many ways to do this, here's one: **FILES=`ls -1 *avi *mp4 *mkv *flv *mpg *wmv`**

2nd, you want to loop over each file and do "something" ... looping in bash can be accomplished with a for-loop: **for file in $FILES ; do**

3rd, you need to strip off the extension to create the directory name. There are many ways to do this too - **sed** could be used, but bash has a built-in way that is easier.  You can look that up in any **bash scripting howto**.

4th, you want to create the directory - **mkdir **and 5th, you want to move the file into that newly created directory - something like **mv $file $newdir** should handle it.

Then you just need to close the for-loop with an **done** statement.

Simple.

If you choose to leave spaces in the file names, you'll want to quote every variable throughout the script. That isn't hard, but if the filenames have other special characters like a quote or single-quote or others, it can get complicated.

Enjoy.  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) is the best bash scripting guide filled with examples that I know.

---

### Post by sohlinux on 2012-10-15
> **TheFu said:**
> There are lots of ways to do this.  

thanks for the info

is there a real simple way?, just a one liner, I have already renamed all the files so all spaces are now underscores and there are no other characters other than a to z and 0 to 9 and _

I dont mind if the extension is stripped off the folder name, it doesnt matter 

so basically john_usa.avi 

mkdir john_usa.avi 

mv john_usa.avi john_asu.avi

but that way it says mkdir: cannot create directory `john_usa.avi': File exists

so maybe add _video to the end of each folder name?

thanks

---

### Post by sohlinux on 2012-10-15
got it!

for f in *.*; do d="${f%.*}"; mkdir "$d" && mv "$f" "$d/"; done

---

### Post by papibe on 2012-10-15
Hi sohlinux.

Try this:
```
find -maxdepth 1 -type f \( -iname '*.avi' -o -iname '*.mp4' \) -exec bash -c 'dir=${1%.*}; echo mkdir "$dir"; echo mv -v "$1" "$dir"' _ '{}' \;
```
Where:
[INDENT]'**-maxdepth 1**' will only go 1 level in the directory tree.
'**-type f**' will get only files.
'**\( -iname '*.avi' -o -iname '*.mp4' \)**' will get avi, and mp4 files. Add more file types if you need them.
'**-exec**' will execute the next code for each file found.
'**${var%.*}**' is a bash parameter substitution to get rid off the extension.
'**bash -c '...' _ parameter**' will execute a bash script with 'parameter' as parameter.
[/INDENT]
NOTE: this code DO NOT create dirs and move directories, but it echoes the commands. When you feel it is doing what you want, remove the 'echo' commands.

Let us know how it goes.
Regards.

EDIT: with this method you won't need to change spaces or other characters in the files' names.

---

### Post by TheFu on 2012-10-15
> **sohlinux said:**
> got it!

for f in *.*; do d="${f%.*}"; mkdir "$d" && mv "$f" "$d/"; done

That isn't a one-liner. It is a 5 liner, in my book. ;) Still, if you don't need to be clear, putting this into an alias could be handy.  My script is a little more complex and does other things like creating 10% parity files (actually, they get added to a batch queue request) after moving each video file into their own directories.

I didn't look too closely at your commands, but wanted to point out that the *.* doesn't work the same way in UNIX as in MS-DOS.  

* matches any number of characters, including zero.
. matches any single character.
* matches any number of characters, including zero.
so you've matched any filename with at least 1 character.  Extensions are seldom anything important in UNIX like they are in Windows.

In short, "*" alone without quotes would accomplish the same thing for almost every UNIX shell.  BTW, this is called file globbing.  I didn't want to assume that every file in the directory was only a video, hence the way I globbed specific file extensions. Actually, there's a better way to do that too, so that the filenames are case insensitive.

The solution using **find** is interesting too.  I'd caution that **find** can be extremely dangerous.  I've completely wiped out entire operating systems using it before.  That said, it is worth using where it fits** AND** where you've verified there aren't any undesired side effects.

If you open up the solution set to python, perl, ruby, ... whatever, then there are lots of other ways too and special characters in the filenames can be gracefully handled using normal logic.

Anyway, enjoy.

---

### Post by sohlinux on 2012-10-15
thanks guys, I marked this as solved ;)

---

