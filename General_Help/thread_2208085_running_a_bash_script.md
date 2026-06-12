---
title: "running a bash script"
date: 2014-02-26
forum: General Help
---

### Post by meanmrmustard on 2014-02-26
I've got a small bash script that will change underscores to spaces I'd like to run on my music directory.

I've made it executable and placed it in /usr/bin.
If I understand running a script, I cd to the music directory and say:
./nameofscript.sh
or
bash nameofscript.sh

I'm obviously doing something wrong - maybe more than one thing - but I'm not sure what it/they might be.
I also tried putting the files in ~/Documents and placing a link to the script in /usr/bin - which is in my PATH.

When I tried ./nameofscript.sh CLI returned "No such file or directory"
Trying sh nameofscript.sh it returns "sh: 0: Can't open nameofscript.sh"

So what am I missing?
Thanks

---

### Post by xeonix on 2014-02-26
As the file is already in the PATH, you don't need a prefix like, "**./**" or "**bash**" or "**sh**".
Just simply use/type
```

nameofscript.sh

```

---

### Post by buzzingrobot on 2014-02-26
The './' construction tells the shell (Bash) to look in the current directory for the file.

---

### Post by meanmrmustard on 2014-02-26
Thanks to both of you for the tips.

Running the script as nameofscript.sh returns
nameofscript.sh: command not found.

I'm still missing something.

More accurately, there are many lines reading:

/usr/bin/renametunes.sh: 3: /usr/bin/renametunes.sh: [[: not found

---

### Post by Vaphell on 2014-02-26
FYI, in ubuntu if you create bin directory in your home (~/bin), it should be picked up on next login and automatically added to $PATH so anything that you put there should be available even without specifying its location.
User made toys have no place in system directories like /usr/bin, ~/bin is for these.

That said it looks like you might be running your script with sh not bash (bash is not the default for shell scripts, sh/dash is). Bash offers some enhancements over barebone shells and [[ ]] conditionals are one of these things. Bash understands it, but other shells think it's some kind of external command and look for it, unsuccessfully - hence *[[: not found*.

Did you specify the hashbang line?
```
#!/bin/bash
```

---

### Post by meanmrmustard on 2014-02-26
Yes, it's at the first line of the script.

---

### Post by Vaphell on 2014-02-26
can you post its code and the terminal output (highlight-select/middleclick-paste or ctrl+shift+c to copy text in terminal) and wrap them in [noparse]```

```[/noparse] tags?

---

### Post by meanmrmustard on 2014-02-26
> **Vaphell said:**
> can you post its code and the terminal output (highlight-select/middleclick-paste or ctrl+shift+c to copy text in terminal) and wrap them in [noparse]```

```[/noparse] tags?

```
#!/bin/sh
for i in ./* ; do
        if [[ `echo "$i" | grep -r '_' | grep -v 'm3u'` ]]
        then
        #       mv "$i" "`echo "$i" | sed 's/_/\ /g' | perl -p -e 's/(\\w+)/\\u\\L$1/g;' | sed 's/Mp3/mp3/g'`";
                echo "`echo "$i" | sed 's/_/\ /g' | perl -p -e 's/(\\w+)/\\u\\L$1/g;' | sed 's/Mp3/mp3/g'`";
        fi
done
```

```
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found
/home/curt/bin/renametunes.sh: 3: /home/curt/bin/renametunes.sh: [[: not found

```

---

### Post by Vaphell on 2014-02-26
```
#!/bin/[COLOR="#FF0000"]sh[/COLOR]
```
ok, what does it say, sh or bash? :P

the code itself is really really hacky and can be replaced with something like this
```
rename -[COLOR="#0000FF"]n[/COLOR]v 's/(\w+)/\u\L$1/g; s/Mp3$/mp3/' *_*.[mM][pP]3
```

if you want a loop with pure bash and no external commands (rename, grep, sed, perl, ...)
```
for f in ./*_*.[mM][pP]3
do
  fn=${f%.mp3}; fn=${fn//_/ }; fn=${fn,,}; fn=${fn~}.mp3 
  [COLOR="#0000FF"]echo[/COLOR] mv "$f" "$fn"
done
```

remove blue parts to actually perform the operation (-n/ echo make it a dry run to test the outcome)

***_*** glob will select only files that have at least 1 underscore, so all that testing you did becomes unnecessary right off the bat

---

### Post by meanmrmustard on 2014-02-26
> **Vaphell said:**
> ```
#!/bin/[COLOR="#FF0000"]sh[/COLOR]
```
ok, what does it say, sh or bash? :P



Doh!:-&

> 
the code itself is really really hacky and can be replaced with something like this
```
rename -[COLOR="#0000FF"]n[/COLOR]v 's/(\w+)/\u\L$1/g; s/Mp3$/mp3/' *_*.[mM][pP]3
```

if you want a loop with pure bash and no external commands (rename, grep, sed, perl, ...)
```
for f in ./*_*.[mM][pP]3
do
  fn=${f%.mp3}; fn=${fn//_/ }; fn=${fn,,}; fn=${fn~}.mp3 
  [COLOR="#0000FF"]echo[/COLOR] mv "$f" "$fn"
done
```

remove blue parts to actually perform the operation (-n/ echo make it a dry run to test the outcome)

***_*** glob will select only files that have at least 1 underscore, so all that testing you did becomes unnecessary right off the bat

Actually the code I found was from a search trying to find a way to replace underscores in track names with spaces.
There are several formats - mp3, vorbis, m4a, shn, wav etc.
So really, I don't know what I need, and I have only the most vague understanding of bash, dash or sh or anything else.

---

### Post by Weedy101 on 2014-02-26
If your interested in the subject of scripting then I recommend starting with this tutorial [http://linuxtutorial.todolistme.net/scripting.php](http://linuxtutorial.todolistme.net/scripting.php), at the end of that quick starter there is some useful links and advice on where to go take things.

> rename -[COLOR=#0000FF]n[/COLOR]v 's/(\w+)/\u\L$1/g; s/Mp3$/mp3/' *_*.[mM][pP]3

I would be tempted to use ls and pipe the output through the rename. Using a filter to select the other file types instead of just mp3. (My egrep and expressions are not up to much but that's the theory I'd apply to this problem.

Then once you have the command line working and achieving the intended results simply place it into a text file with the 'shebang' of #!/bin/bash and a comment or two to help you remember exactly what it is doing and how.

---

### Post by Vaphell on 2014-02-26
i suspected that it's supposed to be generic, but the mp3 extension was explicitly mentioned so i went with that.

try this
```
#!/bin/bash

music=( "$HOME/Music" "$HOME/some/other/music" )
ext=( mp3 m4a wav ogg )


printf -v regex '%s|' "${ext[@]}"
regex=".*/[^/]*_[^/]*[.](${regex%?})$"

while read -rd $'\0' f
do
  dr=${f%/*}
  nm=${f##*/}; nm=${nm%.*}; nm=${nm,,}; nm=${nm//_/ }; nm=${nm~}
  xt=${f##*.}; xt=${xt,,}
  printf "'%s' -> '%s'\n" "$f" "$dr/$nm.$xt"
  # mv -- "$f" "$dr/$nm.$xt"
done < <( find "${music[@]}" -regextype posix-extended -iregex "$regex" -type f -print0 )

```

it's recursive (find command) so it should scan whole directory trees under dirs defined at the top. Affected extensions go next.
Actual mv that renames files is commented out. Test it on the side first on some dummy files, i'd hate to mess things up.


> I would be tempted to **[COLOR="#FF0000"]use ls and pipe the output[/COLOR]** through the rename. Using a filter to select the other file types instead of just mp3. (My egrep and expressions are not up to much but that's the theory I'd apply to this problem.

that's a big fat no. LS should never be used in scripts in any kind of automation, it's for human eyes only because it doesn't guarantee correctness of data, eg it mangles unprintable chars that are otherwise legit in filenames (only \0 and / are off limits) and solutions based on parsing ls blow up on whitespace related issues.
Long story short: if you embed ls, you are doing it wrong. If you pipe ls, you are doing it wrong.

What you want to really achieve is done by using more globs, without the ls/any kind of pipe intermediary.

```
rename '.....' *_*.mp3 *_*.m4a *_*.ogg
```
or more compact
```
rename '....' *_*.{mp3,m4a,ogg}
```

---

### Post by Weedy101 on 2014-02-27
> **Vaphell said:**
> that's a big fat no. LS should never be used in scripts in any kind of automation, it's for human eyes only because it doesn't guarantee correctness of data, eg it mangles unprintable chars that are otherwise legit in filenames (only \0 and / are off limits) and solutions based on parsing ls blow up on whitespace related issues.
Long story short: if you embed ls, you are doing it wrong. If you pipe ls, you are doing it wrong.

What you want to really achieve is done by using more globs, without the ls/any kind of pipe intermediary.

```
rename '.....' *_*.mp3 *_*.m4a *_*.ogg
```
or more compact
```
rename '....' *_*.{mp3,m4a,ogg}
```

Sorry I was not aware of this, most Ubuntu/Linux tutorials neglect to mention they are 'Using a dirty trick' to demonstrate a point.

I have a few scripts to re-write now #-o

---

### Post by Vaphell on 2014-02-27
yeah, that's a pain because when people start learning bash they land on websites offering questionable solutions and then perpetuate the problem themselves. Given there is so much bad code in google, it's pretty much impossible to eradicate.

from my signature check out
'bash pitfalls' for most common mistakes and why they are bad
'bash faqs' for how to solve common problems
you can also run your scripts through shellcheck.net, it points out common bash errors.



When it comes to file/dir names you should use (in order)
1. globs
native, rock solid, zero overhead
2. find -print0 + while read -d $'\0'
rock solid, piping of find results allowed through commands supporting null delimiter in order to preserve null-delimited format till the end (grep -Z, sort -z, uniq -z, ... )
2a. find -print0 + xargs -0, the same deal but with xargs replacing the native bash loop.
.
.
.
666. dirty hacks with ls, grep and pipes and stuff

1 and 2 are 100% safe. **Find -print0** setup works because it uses null to separate elements on the list and null is illegal in filenames so there is no risk of collision. Newline is not enough, why?
```
$ touch $'abc\ndef'
$ ls
abc
def
```now try to delete this file that has newline in its name via ls/grep/or whatever. Good luck. Your script using ls and pipes won't be able to distinguish between newline as part of name and newline as separator and will see 2 files: 'abc' and 'def'.
Yes, newline is good enough in 99.9% of cases but let's say you screw things up and produce a bunch of malformed files with funky names, you won't be ever able to clean them up. Given that the proper approach is only a dozen chars more, there is no reason not to eliminate dangers once and for all.

consider this a boilerplate for all scripts where you'd want something that's too complicated for globs, eg selecting a subset of files/dirs recursively, where you'd want to plug pipes in.
```
while read -rd $'\0' f
do
    something_fancy_with "$f"
done < <( find ... -print0 )
```

---

### Post by meanmrmustard on 2014-02-28
Thanks.
I really appreciate your effort/input and especially for the link to BashGuide.
I'm going to start reading and see if I can learn to decipher what you wrote in the post - most of it might as well be Greek right now for me.

I haven't tried the script you wrote yet but plan to later today or tomorrow.

---

### Post by Vaphell on 2014-02-28
you mean that null-delimiter and stuff?

Hacky solutions risk mangling names and are notoriously prone to whitespace issues (space, tab, carriage return, newline)
Native globs don't use a plain string representation to store lists, so there is no risk of a file name being mangled. File name stays intact no matter what, that's why they should be used as often as possible, no whitespace problems, no overhead, just smooth sailing.

Other ways of filename manipulation using external commands (anything non-glob) involve interpretation of plaintext. Bunch of text is passed around and you need to figure out how to slice that text block in order to get proper names. That means you need marker characters to indicate where the name boundaries are.
```
file 1.txt[COLOR="#0000FF"]N[/COLOR]file 2.avi[COLOR="#0000FF"]N[/COLOR]wut.jpg[COLOR="#0000FF"]N[/COLOR]
```
[COLOR="#0000FF"]N[/COLOR]=newline. If you have such a list you take it, assume [COLOR="#0000FF"]N[/COLOR] as delimiter and then proceed to extract individual file names to process.
The problem is newline is legit in filenames and if you assume [COLOR="#0000FF"]N[/COLOR] as delimiter, you can't distinguish between
```
'abc' 'def' 'ghi'
'abc[COLOR="#0000FF"]N[/COLOR]def[COLOR="#0000FF"]N[/COLOR]ghi'
'abc[COLOR="#0000FF"]N[/COLOR]def' 'ghi'
```
because all these variants are listed with the same string
```
abc[COLOR="#0000FF"]N[/COLOR]def[COLOR="#0000FF"]N[/COLOR]ghi[COLOR="#0000FF"]N[/COLOR]
```

solution to that ambiguosity is null char \0. It can't be used in names => if you find it, you cut there.
```
abc[COLOR="#0000FF"]N[/COLOR]def[COLOR="#0000FF"]0[/COLOR]ghi => 'abc[COLOR="#0000FF"]N[/COLOR]def' 'ghi'
```
**Find [COLOR="#0000FF"]-print0[/COLOR]** produces such a list, so combined with **read [COLOR="#0000FF"]-d $'\0'[/COLOR]** you get a rock solid solution. Whenever you need to pipe the find output for whatever reason, you need tools understanding \0 so they don't destroy the format accidentally. Just look for 0/null/\0 in their --help section.
Grep -z/-Z also supports nulls so it can be a source of legit file lists too.

quick showcase
```
$ touch $'abc\ndef' 'ghi' # create 2 files
$ printf "[%s]\n" *   # glob, names preserved
[COLOR="#0000FF"][abc
def]
[ghi][/COLOR]
$ printf "[%s]\n" $( ls )  # embedded ls, fail, ls output cut on every whitespace
[COLOR="#FF0000"][abc]
[def]
[ghi][/COLOR]
$ printf "[%s]\n" "$( ls )"  # quoted embedded ls, fail, quoted = one big string
[COLOR="#FF0000"][abc
def
ghi][/COLOR]
$ while read -rd $'\0' f; do printf "[%s]\n" "$f"; done < <( find -type f -print0 ) # null delim, names preserved
[COLOR="#0000FF"][./ghi]
[./abc
def][/COLOR]
```

---

