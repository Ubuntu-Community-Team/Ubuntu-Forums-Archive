---
title: "Grep ."
date: 2020-05-23
forum: General Help
---

### Post by yegnal on 2020-05-23
With some effort I was able to find a reference to the "." in the following:   grep . /sys/bus/usb/devices/*/power/wakeup
as being a sort of wildcard to include hidden files or directories.

My confusion is that nothing is hidden in that path, but if I exclude the "." the output is nothing.

In other words grep /sys/bus/usb/devices/*/power/wakeup returns no result
but grep . /sys/bus/usb/devices/*/power/wakeup does in fact return results.

Can't find anything that explains what role the "." plays in that search.

---

### Post by TheFu on 2020-05-23
```
$ man grep
```

grep has 2 or more arguments.  Something like
```
$ grep <options> <regex>  <file-globbing patter to search>
```

The '.' is a valid regex. It matches any character.  There are slightly different regex languages from a simple one to the full perl regex.

**grep -E** will get the full perl-regex.  Also, **egrep** is an alias for that.

So ... if you want to understand how grep works, you'll need to learn regex. Start there.

The <file globbing patter to search> is interpreted by your shell, typically bash, to provide a list of input files to grep/egrep to be searched. Different shells handle that differently and have different limitations for expansion. For example, if the globbing matches more than 20 files, that could easily overfill what the bash buffer limit allows.  There are ways around that, using another tool - **xargs**.

Some commands are best learned by seeing examples.  egrep and find are 2 I think work best that way.  Search for *grep examples*.

Be certain you know the difference in how your shell deals with "" and '' groupings too.  I usually use '' around my regex patterns to prevent the shell from doing odd things.  A common one I use weekly is 
```
$ egrep -i 'warn|erro' /var/log/*log
```
This searches all current log files for error or warnings in a line.  Journalctl supports regex searches too, so eventually, I won't need that egrep.

The main reason the person use grep at all in that example, was to condense the contents of some very specific files into 1 line for each file, while having the filename output too. Nothing more.  They could have used 
$ less /sys/bus/usb/devices/*/power/wakeup
or
$ more /sys/bus/usb/devices/*/power/wakeup
or
$ cat /sys/bus/usb/devices/*/power/wakeup

Each isn't a condensed and clear as the **grep .  /sys/bus/usb/devices/*/power/wakeup** command.  Try each of them. See the differences?

---

### Post by SeijiSensei on 2020-05-23
To search for a character with special meaning in a regex like the period, you need to "escape" the character with a backslash like this:
```
grep \. SomeTextOrFileWithA.InIt
```

Like TheFu I usually enclose any regex search string in single quotes. That convention is used throughout the shell to have it treat the string inside the quotes literally.  So the command above could also be written:
```
grep '.' SomeTextOrFileWithA.InIt
```

The shell distinguishes between single and double quotes. With double quotes, bash first replaces any references to "environment variables" with their assigned values before interpreting the string.  So 
```
echo "Show me my $HOME"
```
would return
```
Show me my /home/seijisensei
```
with my actual home directory substituted for $HOME.  If instead I used the command
```
echo 'Show me my $HOME'
```
it would return
```
Show me my $HOME
```

There are a lot of good guides to regular expressions on the Web. Just search Google for "regular expression".

---

### Post by yegnal on 2020-05-23
Thanks so much.

I found nothing in man grep, but what your saying makes sense..   Thanks for the time and effort to respond.

---

### Post by sisco311 on 2020-05-23
Don't give up on man pages, just make your time to learn the jargon. 

```
man grep | less "+/REGULAR EXPRESSIONS"
man grep | less "+/^.+The period"
```

---

### Post by TheFu on 2020-05-23
Manpages completely rock!  

Almost all the knowledge of the Unix world is held inside those files.  Some are better than others.  The ssh and sshd_config manpages are works of art.  So is the rsync one.  Freakin' amazing.  

Grep's manpage isn't bad, assuming you already understand regex. Without understanding regex, it seems like a high-paid consultant - everything said is true, but not what you need to know, now.

---

### Post by yegnal on 2020-05-26
I looked first at 'man grep' in the terminal window, and searched for the pattern "grep . " and got nothing.  I'll take another look, but is the terminal window the best place to look, or is there a more definitive resource for manual pages ?

---

### Post by The Cog on 2020-05-26
The man pages are _the_ resource for manuals. But there are plenty of tutorials you can find with Google - the man pages can be rather terse at time

Similar to what TheFu said, ```
grep <options> <regex>  <list of files to search>
```
Options always start with a minus sign - there weren't any in your command
Regex is the search string (regular expression). Google for tutorials on this subject. In your case, the search term was "." which matches any character, so will find all non-blank lines
List of files in your case is whatever filenames "/sys/bus/usb/devices/*/power/wakeup" expands to.

In your case, it appears that this will print every line from every file in that list, which looks to me like a list of usb devices with wakeup features. These files almost certainly only contain one line each.

---

### Post by TheFu on 2020-05-26
> **yegnal said:**
> I looked first at 'man grep' in the terminal window, and searched for the pattern "grep . " and got nothing.  I'll take another look, but is the terminal window the best place to look, or is there a more definitive resource for manual pages ?

There's a difference between having a manual and having every possible combination of example.  grep and the language of regex is just too complex to even attempt every possible example in any document.  Plus, grep USES regex. It isn't a reference for REGEX.  Regex is a language unto itself, used by many, many, tools on all computers around the world.

a) Yes, the manpage IS the best place to learn to use a command.

b) Yes, certain commands are _best initially learned by seeing 50 examples._  Google 'regex examples' or 'grep examples'.  There are just so many uses.

c) Yes, regex needs to be learned **to a basic level** if you intend to be a shell guru.

d) There are slightly different versions of the regex language. Some have a much smaller vocabulary and can be implemented much easier.  OTOH, the full, extended regex can be used to match any possible UTF8, Unicode, ASCII pattern that I've ever imagined.  At one job, we'd use regex to create hyperlinks from documents ToC into the correct pages, figures, tables, AND from the Index back into the correct pages.  That level of use is pretty seldom.  Usually we just want to match a few, specific filenames.  

e) Bash supports a limited regex, sometimes called file-globbing.  <-- That's the real term.

f) There are lots of regex pattern engines online. Many have tutorials.

g) On your system, right now, you can ask the man system about regex.  **man -k regex** On my 20.04 system, 13 results came back.  **man regex**  is for the C function.  **man -s 7 regex** is to explain a little about POSIX.2 regex.

---

