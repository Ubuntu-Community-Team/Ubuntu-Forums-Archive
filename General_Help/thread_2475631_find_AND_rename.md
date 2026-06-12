---
title: "find AND rename"
date: 2022-06-02
forum: General Help
---

### Post by tbarents on 2022-06-02
Hello,
I've got a lot of files that are stored like:
name1_name2_01_2020.pdf
name1_name2_02_2020.pdf
name1_name2_03_2020.pdf
name1_name2_04_2020.pdf
...
The thing is that the underline between ...01_2020.pdf has to become a dot:   ...01.2020.pdf. The other stuff  name1_name2_ has to stay.

with the mv command I can change only one file - so that will take 'till next millenium.
then I tried:     find . -type f -name "*_2020.pdf" -exec mv {} "*.2020.pdf"  \; or     find . -type f -name "*_2020.pdf" -exec mv {} *_2020.pdf *.2020.pdf \;      and various other options 

then I also tried the rename command.
I'm looking and testing for hours now but I mostly get the response that there is not such directory. I created another directory to move the modified file in - even if I think it's not required.

But with one file and the mv command this problem doesn't exist. 

An explanation would be good - a solution even better. Thx in advance. I'm desperate...

---

### Post by Holger_Gehrke on 2022-06-02
```

rename 's/_2020/.2020/' *[01][0-9]_2020.pdf

```
'rename' - being a perl script - expects a perl expression with a perl-style regular expression for the changes it is supposed to make to the filenames. The 's' stands for substitute, the characters between the first slash and second slash describe what to look for and the characters between the second and third slash is the substitute to replace the found string with. Small warning: rename takes the first match it finds and replaces it. If there's a match for '_2020' somewhere in the 'name1_name2' part of a filename that will be replaced instead of the '_2020' at the end of the name. You could make the expression more specific, but it would get more complicated; something like 's/_([0-9]{2})_2020\./_$1.2020./'.

As for why the 'find ... -exec mv \{\} variant doesn't work: the wildcards get substituted by the shell before find (or mv) ever gets started. That's just how wildcards work in the shell. So instead of '*_2020.pdf' 'mv' gets the whole list of all the files which match that wildcard and then of course expects the last argument to be a directory, which it is not. 'mv' is for moving multiple files to a different directory or single files from one name to another. Mass renaming is not a job that mv does ; you could do something like 
```

for i in *_[01][0-9]_2020.pdf ; do
  mv "$i" "${i/_2020/.2020}"
done

```
That's a loop in which the variable i takes the filenames matching the pattern one by one and then mv is run with the value of i as the first parameter and a parameter expansion doing a pattern substitution ('.2020' gets substituted for '_2020' in the value of i) as the second parameter.

Holger

---

### Post by TheFu on 2022-06-02
+1 for using rename.

If you want a visual way to do it, use qmv and vim as the editor, then you can use a column selection and either 'r'eplace for 1 column or 'c'hange to replace the entire selection with whatever you type.  It is just vim, so any vim plugins will work or basic vi commands.

---

### Post by tbarents on 2022-06-03
Hello 'TheFu' - thanks for your answer but a visual way wasn't the solution I'm looking for, 'cause I want to learn of and with the terminal.

But I appreciate the answer of Holger_Gehrke a lot, which code for the terminal by using rename just worked fine.
The little script I will look deeper into it at weekend. 
Therefor the explanation why find/mv isn't the solution for multiple changes hasn't opened my eyes yet - I thought that the find cmd picks one file and gives it to -exec 
because of mv {}....\;
So that will be something I have to explain myself either.

---

### Post by Impavidus on 2022-06-03
qmv (in the renameutils package) and vim run in the terminal, so if you want a terminal solution, it qualifies. You can't put it in a script though.

---

### Post by Holger_Gehrke on 2022-06-03
> Therefor the explanation why find/mv isn't the solution for multiple   changes hasn't opened my eyes yet - I thought that the find cmd picks   one file and gives it to -exec 
because of mv {}....\; 
			 		 	 Before find ever gets to see the various things you put on the command line the shell does it's magic.
Your lines
```

find . -type f -name "*_2020.pdf" -exec mv {} "*.2020.pdf"  \;
or
find . -type f -name "*_2020.pdf" -exec mv {} *_2020.pdf *.2020.pdf  \;

```

have a few critical problems. The braces have a special meaning to  the shell. Search the bash manual for 'brace expansion'. So unless they  are quoted or escaped the braces in your command get removed by the  shell (the find manual page mentions this in the description of  '-exec'). As a consequence of this there's only one parameter for the  'mv' command ("*.2020.pdf" - the wildcard '*' doesn't get expanded since  it's in quotes) and 'mv' needs at least two parameters. But even if you  do escape the braces, 'mv' doesn't know how to handle wildcards (or  globs) - that's all done by the shell. So 'mv \{\} "*.2020.pdf"' would  try to give a literal '*' as the first character of the new name and all  the files would be moved to that name with the second move overwriting  the first and the third overwriting the second and ...

The second  variant is even more fun. You have unquoted wildcards in there. Before  find gets even called the shell replaces all the wildcards with lists of  the filenames which match the wildcards. So again the unquoted braces  are removed and then '*_2020.pdf' gets replaced with all the filenames  which end in '_2020.pdf' and if you already have some files which end in  '.2020.pdf' those are put in there,too. So you'll have something like  'mv name1_name2_01_2020.pdf name1_name2_02_2020.pdf  name1_name2_03_2020.pdf name1_name2_04_2020.pdf name1_name2_05.2020.pdf  name1_name2_06.2020.pdf'. Since that has more than two parameters, mv  expects the last parameter to be a directory to move all the files into.  It isn't and you get an error message. 	  	 	 	 		   Holger

---

### Post by The Cog on 2022-06-03
> Therefor the explanation why find/mv isn't the solution for multiple changes hasn't opened my eyes yet - I thought that the find cmd picks one file and gives it to -exec
because of mv {}....\;
I'm not sure this is your problem, but I have learned to always put the {} in single quotes  '{}' to prevent shell expansion from mangling it. It can help understanding if you echo the command that find is putting together - you can see what's happening, example using one of your posts above (star expansion will be your main issue here, as has already been mentioned):
```
find . -type f -name "*_2020.pdf" -exec echo mv {} *_2020.pdf *.2020.pdf \;
```
As already mentioned, rename is better for this work because you don't have to fight shell expansion of the command you are constructing. But if you need to use find, the echo trick can really help figure out what's wrong.

---

### Post by tbarents on 2022-06-03
Hello Holger,
well, as I already told, the first cmdline works fine and I modified it into 
rename 's/_2020/.2020/' *[1-9]_2020.pdf
the result for this problem in particular was solved as well: will I get problems in other cases?

then  I tried the "if...do..." solution and I got a prompt ">" without  further working. Well, it isn't that important by now but still I wonder  why...

---

### Post by tbarents on 2022-06-03
ok. ok. ok.
because of this thread I will never forget that 'mv' is a  cmd for moving files into directories and can't be used for renaming  multiple files....

---

### Post by TheFu on 2022-06-03
> **tbarents said:**
> ok. ok. ok.
because of this thread I will never forget that 'mv' is a  cmd for moving files into directories and can't be used for renaming  multiple files....

It is a common wish from everyone, but the way that lots of these commands work is they can accept multiple input names, but only 1 output name.  If you want to rename 500 files into 1 file, effectively deleting 499 files, mv is the way .... or at least it was decades ago. I think the code knows to check for that now and errors.  Not every tool will.

Filename expansion happens BEFORE the command being run, by whatever shell is being used. On Linux, that is usually bash, but not always.

OTOH, if you want to do commands one-at-a-time, then find and/or xargs can be used.  But the target file must be exactly specified.  Often, I'll use a 2-step process ... using a temporary name for the output in the first step, then mv'ing the file to the final desired name in step 2.

**But I completely agree that rename is the tool for this task.** Where find comes in is if multiple directories are necessary, since rename works cleanest inside a single directory from a conceptual standpoint (or perhaps that's just me).  Plus, knowing perl regex can do all sorts of amazing things, including grouping for different parts in the source name to be substituted into the target name.  And when perl regex gets long, it can be written on multiple lines with comments to explain what is being matched in each part.  I haven't seen that any other regex tool supports that in-the-middle-of-a-regex expression.

qmv is just another tool in the toolbox.  I'd not heard of it before someone here suggested it for something like this. I spent the time to learn it and found it very useful when I'd normally use an editor to create a script to work on lots of filenames.  This is usually when the filenames arrive with some sort of sequence number/letter and I need to merge or expand those files for some reason, so renaming them in a predictable, ordered, way is handy.  Vim has methods to make specific columns into a sequence easily.  That sequence can be 01, 02, 03, or Jan, Feb, Mar, Apr, ... or A, B, C, ... or mixes of those.  Also, reversed sequences.  The right tool, for the right job. Being efficient is important, but sometimes brute force methods are necessary too. ;)
At least we have these different options to pick from on Unix systems.

---

