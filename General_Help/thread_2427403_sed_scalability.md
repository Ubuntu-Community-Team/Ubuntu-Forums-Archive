---
title: "sed scalability"
date: 2019-09-21
forum: General Help
---

### Post by Langstracht on 2019-09-21
The command:

```
sed -i "/text/d"
```

works just fine to delete the line containing "text" in a NAMED FILE.

i.e.:

```
sed -i "/text/d" filenam,ext
```

Alas, I have over a thousand files in hundreds of folders that I need to "correct".

Can anyone help to convert the "one file sed" to, well, more?

TIA

---

### Post by TheFu on 2019-09-21
To do many files, **find** and **xargs** is the common way.  
I would use **grep -v** instead, if sed performance was an issue. fgrep works with fixed strings, not regex, which should be faster. 
```
find {path to top level dir} -name "*.txt" -print0 | xargs -0 grep -v "abc"
```
 Google "xargs examples" if more examples are needed.
If that wasn't fast enough, then I'd write a tiny perl script.  For stuff like this, perl is often faster than native C programs.
Really sed, grep -v and perl should all be pretty close in performance. Call it personal preference for which should be used.

There are also lots of other methods than xargs.  gnu-parallel, for example. Just depends what you really need.

---

### Post by Skaperen on 2019-09-21
xargs is buggy, especially with funny file names.  to get around that you can run a bash loop.
```

find ... -print | while read x ; do grep -v "abc" "$x" ; done

```
and i find this to be more flexible.  i can code ifs and loops in there, too.

---

### Post by norobro on 2019-09-21
Using find and sed:```
[FONT=monospace][COLOR=#000000]find "path" -name "..." -exec sed -i '/text/d' {} \;[/COLOR]
[/FONT]
```Untested.

---

### Post by sisco311 on 2019-09-21
> **TheFu said:**
> To do many files, **find** and **xargs** is the common way.  
I would use **grep -v** instead, if sed performance was an issue. fgrep works with fixed strings, not regex, which should be faster. 
```
find {path to top level dir} -name "*.txt" -print0 | xargs -0 grep -v "abc"
```
 Google "xargs examples" if more examples are needed.
If that wasn't fast enough, then I'd write a tiny perl script.  For stuff like this, perl is often faster than native C programs.
Really sed, grep -v and perl should all be pretty close in performance. Call it personal preference for which should be used.

There are also lots of other methods than xargs.  gnu-parallel, for example. Just depends what you really need.

The OP uses *sed -i* to edit the file(s) in place. 

> **Skaperen said:**
> xargs is buggy, especially with funny file names.  

That is why GNU find and xarg has a -print0 and -0 (minus zero) option. 

@OP See: [https://mywiki.wooledge.org/UsingFind](https://mywiki.wooledge.org/UsingFind)


> **norobro said:**
> Using find and sed:```
[FONT=monospace][COLOR=#000000]find "path" -name "..." -exec sed -i '/text/d' {} \;[/COLOR]
[/FONT]
```Untested.

I would use the `-exec command {} +` 
```
man find | less +/"^.*-exec command {} \+"
```

@OP
sed is a stream editor. Some people claim that ed is faster than `sed -i` in file editing.
[https://wiki-dev.bash-hackers.org/howto/edit-ed](https://wiki-dev.bash-hackers.org/howto/edit-ed)

And to answer your question :)

You can pass multiple file names to sed/ed/grep...

```
sed -i "whatever" file1 file2 file3
```
and you can use a glob to match multiple files:
```
sed -i "blah blah" *.txt
```
since bash 4 you can match files recursively:
```
sed -i "D\'oh\!" **/*.txt
```

[https://mywiki.wooledge.org/glob](https://mywiki.wooledge.org/glob)

---

### Post by Langstracht on 2019-09-22
Thanks to all who responded to this post.

The commands suggested were:

```
find {path to top level dir} -name "*.txt" -print0 | xargs -0 grep -v "abc"

find ... -print | while read x ; do grep -v "abc" "$x" ; done

find "path" -name "..." -exec sed -i '/text/d' {} \;

find {path to top level dir} -name "*.txt" -print0 | xargs -0 grep -v "abc"

man find | less +/"^.*-exec command {} \+"
```

The text I want to eliminate is "Global", the file type containing the offending text is *.html and the to level folder is "Scott Project".  Causing me to change the commands to;

```
find ~/Desktop/'Scott Project' -name "*.html" -print0 | xargs -0 grep -v "Global"

find "~/Desktop/'Scott Project'" -name "*.html" -exec sed -i '/Global/d' {} \;

find {~/Desktop/'Scott Project} -name "*.html" -print0 | xargs -0 grep -v "Global"

```

I didn't know how to change numbers 2 and 5.

So!  Three commands.  And, sorry to say, none of them worked.

I think the first did - based on the file contents as they went whizzing by .... but the "change" was not saved to the file.

I have little doubt that the lack of success has been due to making the mods incorrectly.  REALLY appreciate someone pointing out what I did incorrectly.

Thanks again and even more TIA

---

### Post by The Cog on 2019-09-22
Grep prints the files, does not re-write them. Not suitable for your purpose

The exec on find is a bit peculiar, the {} that it replaces with the filename has special meaning to bash, so it need quoting to prevent bash trying to interpret it. Put single quotes round it like this.
Also, the single-quotes inside double-quotes seems wrong - they become part of the file name. In general, don't put spaces in filenames - they cause trouble
Try this::
```
find ~/Desktop/'Scott Project' -name "*.html" -exec sed -i '/Global/d' '{}' \;
```


Most of the answers you have seen were treating "scalability" as a problem with the time taken rather than a problem doing more than one file at all, so I think people were focusing on the wrong issue.
Un-tested, but this might fix both issues: Firstly, I do the find bit and let it print the commands that I need to execute to the screen where I can look at them to see that I've got this part right
```
find "~/Desktop/'Scott Project'" -name "*.html" -exec echo sed -i '/Global/d' "'{}'" \;
```
Then for a simple but slower fix, re-run the above with "echo" removed so it runs the command rather than printing it.
To go faster, instead of removing the echo command, pipe the commands into parallel (may have to install: sudo apt install parallel) to run them in parallel:
```
find "~/Desktop/'Scott Project'" -name "*.html" -exec echo sed -i '/Global/d' "'{}'" \; | parallel
```

---

### Post by TheFu on 2019-09-22
> Most of the answers you have seen were treating "scalability" as a problem with the time taken rather than a problem doing more than one file at all, so I think people were focusing on the wrong issue. 
True.  Nominally, someone showing up using **sed** has a level of expertise, especially with file redirection.

I don't like replacing files 'in-place'.  Find my stomach can't take the fear of total data loss.  I've completely wiped OSes with a bad **find** command previously.   The grep -v option was an option specifically to avoid overwriting existing files, but it definitely was NOT a complete answer.  Sorry for the confusion it caused.

The find manpage explains some important considerations mentioned above:```

       -exec command ;
              Execute command; true if 0 status is returned.  All following arguments  to  find  are
              taken  to  be  arguments to the command until an argument consisting of `;' is encounâ
              tered.  The string `{}' is replaced by the current file name  being  processed  everyâ
              where  it  occurs  in  the arguments to the command, not just in arguments where it is
              alone, as in some versions of find.  Both of these  constructions  might  need  to  be
              escaped  (with  a `\') or quoted to protect them from expansion by the shell.  See the
              EXAMPLES section for examples of the use of the -exec option.  The  specified  command
              is run once for each matched file.  The command is executed in the starting directory.
              There are unavoidable security problems surrounding  use  of  the  -exec  action;  you
              should use the -execdir option instead.

       -exec command {} +
              This variant of the -exec action runs the specified command on the selected files, but
              the command line is built by appending each selected file name at the end;  the  total
              number  of  invocations  of  the  command will be much less than the number of matched
              files.  The command line is built in much the same way that xargs builds  its  command
              lines.   Only one instance of `{}' is allowed within the command.  The command is exeâ
              cuted in the starting directory.  If find encounters  an  error,  this  can  sometimes
              cause an immediate exit, so some pending commands may not be run at all.  This variant
              of -exec always returns true.
```
For thousands of files matching the 'find', I doubt the* -exec .... + *will work, if it works as described. There is a buffer/line/character limit to arguments  that can be passed. Think it is 4K, which would easily be hit with thousands of files.

I don't allow funky filenames on my systems, which prevents a bunch of problems. Not all admins have that capability, if they have to allow end-users access to the systems.  No punctuation. No spaces. No shift-numbers or any sorts of parentheses allowed. I do encourage the use of ':' characters, however.  Anything to freak out Windows people. ;)

Please make a backup of any files that cannot be lost before attempting any of these commands.  I would copy about 20 of them somewhere else for testing first.

```
find "~/Desktop/Scott Project" -iname \*.html   -exec echo "sed -i '/Global/d' '{}' " \; | parallel
```
Looks like that would cause 3 different processes, if I'm counting correctly. More process count means slower, generally, though the overhead of a process on Unix is tiny compared to Windows.  
I find the different ways we each quote things interesting. Different experiences. Been burned by different things, I suppose.  Plus, I'm not up on newer bash version capabilities.  I've never quoted the {} and never had problems.

Another option is to make a list of all the files using find, then using the other commands to read that file for inputs.

---

### Post by Langstracht on 2019-09-22
Thanks for your reply TheCog.

I haven't checked your 2nd and 3rd suggestions.  In fact, I can't.  Because the 1st worked flawlessly ... and I now have no files needin' fixin'.

How quickly the command ran was not an issue for me - I'd have been happy to let it run overnight.  In fact it took a few minutes.

There are far too many files for me to check them all, but the ones I have checked are exactly what I was looking for.  I assume the others to be the same.

I prove to myself, on a regular basis how unable my ageing brain is to deal with linux syntax.  Thank goodness there are folks like yourself to whom the syntax is second nature and that are willing to share their expertise.

Thanks again, SO MUCH.

---

### Post by The Cog on 2019-09-23
Glad that helped. Please read #8 from TheFu. Like him, the idea of doing in-place edits makes me nervous, proportional to the square of the number of files to edit in one go. 

I would always echo the command and try a sample before removing the echo and doing it for real. 
Copying a sample and experimenting on them makes a huge amount of sense. One misplaced quote on the real data could lead to a LOT of regret.

---

