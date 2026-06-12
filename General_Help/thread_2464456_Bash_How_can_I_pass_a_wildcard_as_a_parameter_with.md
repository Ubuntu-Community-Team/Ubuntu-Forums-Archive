---
title: "Bash: How can I pass a wildcard as a parameter within a script?"
date: 2021-07-02
forum: General Help
---

### Post by Paddy Landau on 2021-07-02
In a Bash script:

I need to pass an exclude option with a wildcard to rsync. The twist is that sometimes the wildcard needs to be omitted.

Without a wildcard, this is easy:
```
if *some_condition*; then EXCLUDE="--exclude='/data/'"; else EXCLUDE=''; fi
rsync ... ${EXCLUDE} ...
```
If *some_condition* is true, rsync gets [COLOR=#0000cd]--exclude='/data/'[/COLOR], otherwise there's no exclude option.

When it comes to wildcards, it's more complicated. You need to turn off globbing as follows otherwise Bash expands it.
```
if *some_condition*; then EXCLUDE="--exclude='/*'"; else EXCLUDE=''; fi
set -o noglob
rsync ... ${EXCLUDE} ...
set +o noglob
```
I would have thought that this would work. However, when I run this in real life, rsync always acts as if EXCLUDE='' even when *some_condition* is true.

I have checked that EXCLUDE has been correctly set.

If I hard-code --exclude='/*' instead of using ${EXCLUDE}, then rsync works correctly.

What am I doing wrong?

---

### Post by dinkidonk on 2021-07-02
Have you tried to use "$EXCLUDE" instead of "${EXCLUDE}"?

In your example, the "*" makes little sense. Would have made sense if you would want to exclude all files with a specific extension, like "*.txt" or something.

---

### Post by sudodus on 2021-07-02
1. I did not check ,but did you try "${EXCLUDE}" (to double-quote it)?

2. Otherwise, why not 'hard-code' it in the script? You know already that it works that way (I mean to have the rsync command inside the if statement).

---

### Post by scorp123 on 2021-07-02
Why not work with regular expressions instead so the exclude stays the same and files thus get selected based on whether or not they match the regular expression?
Or what exactly is that mysterious *"some_condition"* that you are setting?

Alternative idea:  **"for"** loop with a **"find"** that uses negative file selection?

```

for interestingfile in `find /path/to/my/files -type f \( -iname \*.stuff -o iname \*.morestuff -o -iname \*.otherstuff \) -not -path "/path/to/stuff/that/is/not/interesting/*" `
do
  if file -i $interestingfile | grep -q text
  then
    echo $interestingfile": is a text file"
    rsync -avz --progress $interestingfile remoteuser@remotesystem:/path/where/textfiles/go
  else
    echo $interestingfile": is a binary"
    rsync -avz --progress $interestingfile remoteuser@remotesystem:/path/where/binary/stuff/goes
  fi
done

```

---

### Post by Paddy Landau on 2021-07-02
> **dinkidonk said:**
> Have you tried to use "$EXCLUDE" instead of "${EXCLUDE}"?
In Bash, using or not using curly brackets is identical, unless there is an ambiguous situation, in which curly brackets are required. (This is an unambiguous situation, so either way would work.)
> **dinkidonk said:**
> In your example, the "*" makes little sense. Would have made sense if you would want to exclude all files with a specific extension, like "*.txt" or something.
It makes perfect sense; the rsync command has been thoroughly tested. The exclusions "/" and "/*" are not the same. There are several other includes and excludes given to rsync, to give a little context.

---

### Post by Paddy Landau on 2021-07-02
> **sudodus said:**
> 1. I did not check ,but did you try "${EXCLUDE}" (to double-quote it)?
Yes. It makes no difference.
> **sudodus said:**
> 2. Otherwise, why not 'hard-code' it in the script? You know already that it works that way (I mean to have the rsync command inside the if statement).
Because it's a complex rsync with several other options, and I wish to avoid duplication (that's one way that bugs creep in over time).

---

### Post by Paddy Landau on 2021-07-02
> **scorp123 said:**
> Why not work with regular expressions instead&#8230;
Sorry, I'm not entirely sure what you are suggesting. The rsync transfers a large amount of data in quite a deep level of folders. The condition determines which folders to transfer, and while most of the options are the same in all cases, there are just a few that differ.

Does that answer your question?

EDIT: Multiple calls will cause a lot of overhead on the server, which is quite slow. So, a single rsync call is preferred.

---

### Post by Paddy Landau on 2021-07-02
I've figured out a workaround: Use --exclude-from.

I create a temporary file, and either leave it empty or write "/*" to it depending on what's needed.

So…
```
EXCLUDE_FILE=$( mktemp --tmpdir=${XDG_RUNTIME_DIR} z-XXXXXXXXXX )
trap "rm --force '${EXCLUDE_FILE}'" RETURN

*some_condition* && printf '/*\n' >"${EXCLUDE_FILE}"

rsync ... -exclude-from="${EXCLUDE_FILE}" ...
```
Thanks for your help and ideas.

---

### Post by sudodus on 2021-07-02
Sometimes, when it is hard to control where the wild-card is expanded, you can work around the problem by writing to a temporary file, in this case for example a 'one-liner' command with rsync, and let the main shellscript call this one-liner.

Edit: after posting I found that you have already found a[nother] workaround :-)

---

### Post by Paddy Landau on 2021-07-02
> **sudodus said:**
> Sometimes, when it is hard to control where the wild-card is expanded, you can work around the problem by writing to a temporary file, in this case for example a 'one-liner' command with rsync, and let the main shellscript call this one-liner.

Edit: after posting I found that you have already found a[nother] workaround :-)
Yes, thank you, that would have been a good idea had there not been another workaround. There's always a chance of a catastrophic problem with such an approach, of course, but sometimes you don't have a choice!

---

### Post by dragonfly41 on 2021-07-02
There is one approach I use sometimes to test rsync syntax.
I first run grsync (GUI) session and do a test (dry) run.
When it works you can then grab the validated command from
File > Rsync Command Line.

---

### Post by Paddy Landau on 2021-07-02
> **dragonfly41 said:**
> There is one approach I use sometimes to test rsync syntax.
I first run grsync (GUI) session and do a test (dry) run.
When it works you can then grab the validated command from
File > Rsync Command Line.
That's a good tip, thanks, but my rsync has been thoroughly tested, and I know that it works.

---

### Post by philhughes on 2021-07-02
I think this is probably an example of BashFAQ/050:

[https://mywiki.wooledge.org/BashFAQ/050](https://mywiki.wooledge.org/BashFAQ/050)

---

### Post by Paddy Landau on 2021-07-02
> **philhughes said:**
> I think this is probably an example of BashFAQ/050:
[https://mywiki.wooledge.org/BashFAQ/050](https://mywiki.wooledge.org/BashFAQ/050)
That makes interesting reading, thank you!

I'm going to print it out and experiment.

---

### Post by philhughes on 2021-07-02
I think that effectively you are telling rsync to exclude a file literally called '/*', and since you probably don't have one, the effect is it is not trying to exclude anything. If you leave out the single quotes, in my testing it works, but that might cause problems with more complex patterns.

---

### Post by Paddy Landau on 2021-07-02
> **philhughes said:**
> I think that effectively you are telling rsync to exclude a file literally called '/*', and since you probably don't have one, the effect is it is not trying to exclude anything. If you leave out the single quotes, in my testing it works, but that might cause problems with more complex patterns.
No, you misunderstand. It's not a file literally called '/*'.

This is a parameter that's passed to rsync, which (in my case) passes it to the remote server. The remote server expands it there.

Expanding it on my computer will give entirely the wrong results.

That's why the parameter must be passed, unexpanded, to rsync.

---

### Post by philhughes on 2021-07-02
Yes, I know, but qouting from the BashFAQ: "...because the single quotes inside the variable are literal, not syntactical."

So what I mean is that when the parameter is passed to rsync, rsync sees the single quotation marks literally as part of name of the file to be excluded

---

### Post by Paddy Landau on 2021-07-03
> **philhughes said:**
> … when the parameter is passed to rsync, rsync sees the single quotation marks literally as part of name of the file to be excluded
That would indeed happen if I were to quote the variable:
```
rsync ... "${EXCLUDE}" ...
```
But I don't quote the variable:
```
rsync ... ${EXCLUDE} ...
```
Anyway, I did test both with and without. The results are identical:
```
EXCLUDE="--exclude='/*'"
EXCLUDE="--exclude=/*"
```

---

### Post by philhughes on 2021-07-03
You are quoting the variable when you set it.

When using:
```

rsync -av ${EXCLUDE} ...
```

The behaviour I see is:

EXCLUDE=--exclude=/* - files are excluded as expected
EXCLUDE=--exclude='/*' - files are excluded as expected
EXCLUDE="--exclude=/*" - files are excluded as expected
EXCLUDE="--exclude='/*'" - files are not excluded

Obviously I am not replicating your exact set up, so I don't know why we are seeing different behaviour. It would be interesting to ask on stackoverflow!

---

### Post by Paddy Landau on 2021-07-04
> **philhughes said:**
> EXCLUDE=--exclude=/* - files are excluded as expected
EXCLUDE=--exclude='/*' - files are excluded as expected
EXCLUDE="--exclude=/*" - files are excluded as expected
That's what I expected, but don't get.
> **philhughes said:**
> EXCLUDE="--exclude='/*'" - files are not excluded
I am baffled as to why that's different for you, but not for me!

I wonder if there's some Bash setting that you and I have different?

---

### Post by philhughes on 2021-07-04
No idea. There's a load of settings loaded from who knows where that may or may not have an effect, but I've included the output of "shopt" below.

```
autocd         	off
assoc_expand_once	off
cdable_vars    	off
cdspell        	off
checkhash      	off
checkjobs      	off
checkwinsize   	on
cmdhist        	on
compat31       	off
compat32       	off
compat40       	off
compat41       	off
compat42       	off
compat43       	off
compat44       	off
complete_fullquote	on
direxpand      	off
dirspell       	off
dotglob        	off
execfail       	off
expand_aliases 	on
extdebug       	off
extglob        	on
extquote       	on
failglob       	off
force_fignore  	on
globasciiranges	on
globstar       	off
gnu_errfmt     	off
histappend     	on
histreedit     	off
histverify     	off
hostcomplete   	off
huponexit      	off
inherit_errexit	off
interactive_comments	on
lastpipe       	off
lithist        	off
localvar_inherit	off
localvar_unset 	off
login_shell    	off
mailwarn       	off
no_empty_cmd_completion	off
nocaseglob     	off
nocasematch    	off
nullglob       	off
progcomp       	on
progcomp_alias 	off
promptvars     	on
restricted_shell	off
shift_verbose  	off
sourcepath     	on
xpg_echo       	off
```

---

### Post by erind on 2021-07-09
You could pass the EXCLUDE variable to the rsync command by using ***bash arrays*** for the EXCLUDE string value. Array values do not suffer from the shell's unwanted expansions. Something like:

***EXCLUDE=( /* ) ***

and referencing it in the rsync script with** ${EXCLUDE[0]}** for the first element.

[B][I]rsync ... "${EXCLUDE[0]}" ...

[/I][/B]
Take a look at this:

[https://unix.stackexchange.com/questions/512148/bash-array-with-folder-paths-and-wildcards](https://unix.stackexchange.com/questions/512148/bash-array-with-folder-paths-and-wildcards)

---

### Post by Paddy Landau on 2021-07-10
> **philhughes said:**
> No idea. There's a load of settings loaded from who knows where that may or may not have an effect, but I've included the output of "shopt" below.
Sorry for the late reply — Ubuntu Forums frequently doesn't send me notifications.

My shopt and yours are identical, so it remains a mystery!

---

### Post by Paddy Landau on 2021-07-10
> **erind said:**
> You could pass the EXCLUDE variable to the rsync command by using ***bash arrays*** …
I've already tried this, but it doesn't work.

I've found that whenever I include wildcards or quotation marks, it causes failure. I have no clue why, though.

I ended up using the format that the link [from @philhughes gave]("https://ubuntuforums.org/showthread.php?t=2464456&p=14046800&viewfull=1#post14046800").
```
if some_condition; then EXCLUDE='/*'; else EXCLUDE=''; fi
rsync ... ${EXCLUDE:+--exclude="${EXCLUDE}"} ...
```
This is better than my previous workaround, because it eliminates the need for a temporary file. Why does this work and not any of the other suggestions? I don't know :confused:

---

### Post by erind on 2021-07-10
> **Paddy Landau said:**
> I've already tried this, but it doesn't work.

I've found that whenever I include wildcards or quotation marks, it causes failure. I have no clue why, though.

[...]


It should work. Arrays are the conventional way to pass wildcards to the scripts in these special cases. One advice though, when you declare the arrays you don't quote the wildcards, only the strings with whitespaces in them.

In other similar cases I used to use ***eval*** too and it would work great. But nowadays ***eval*** has some security issues and that's why it's deprecated in favor of the arrays, which are considered superior.

However, I'm glad you found a solution.

---

### Post by dinkidonk on 2021-07-10
Are you 100% sure that you condition works as it should?

```

EXCLUDE=""
if [ some_condition ]; then EXCLUDE="--exclude=/*"; fi
# Debug print to verify condition
print ${EXCLUDE}
# Proceed...

```

---

### Post by Paddy Landau on 2021-07-10
> **erind said:**
> It should work.
What can I say? It doesn't!
> **erind said:**
> … when you declare the arrays you don't quote the wildcards, only the strings with whitespaces in them.
I tried both with and without the quotation marks.

---

### Post by Paddy Landau on 2021-07-10
> **dinkidonk said:**
> Are you 100% sure that you condition works as it should?
Yes, I have tested it thoroughly.

---

### Post by erind on 2021-07-10
> **Paddy Landau said:**
> What can I say? It doesn't!

I tried both with and without the quotation marks.

It works fine on my end. Here it is a proof of concept case:

```
$ ll
total 24
drwxrwxr-x 2 miri miri 4096 Jul 10 20:12  **d1**
drwxrwxr-x 2 miri miri 4096 Jul 10 20:35  **d2**
drwxrwxr-x 2 miri miri 4096 Jul 10 20:28 'dir 1'
drwxrwxr-x 3 miri miri 4096 Jul 10 20:31 'dir 2'
-rwxr-x--- 1 miri miri  190 Jul 10 20:30  rs
-rwxr-x--- 1 miri miri  211 Jul 10 20:31  rs_1
miri@miri-IdeaPad-3:~/Temporary$ 
miri@miri-IdeaPad-3:~/Temporary$ 
miri@miri-IdeaPad-3:~/Temporary$** ll d1**
total 0
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_1
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_2
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_3
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_4
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_5
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 b_1
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 b_2
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 b_3
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 b_4
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 b_5
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 c_1
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 c_2
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 c_3
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 c_4
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 c_5
miri@miri-IdeaPad-3:~/Temporary$ 
miri@miri-IdeaPad-3:~/Temporary$ ll d2
total 0
miri@miri-IdeaPad-3:~/Temporary$ 
```

Script below:

```
#!/bin/bash
set -x

if true 
then
 **EXCLUDE=( --exclude=d1/b_* --exclude=d1/c_* ) **
else 
 EXCLUDE='' 
fi

rsync -avz **"${EXCLUDE[@]}"** d1 d2

## Or with the array values spelled out:
# rsync -avz "${EXCLUDE[0]}" "${EXCLUDE[1]}" d1 d2


```

After running the above script:

```
$ ./rs
+ true
+ EXCLUDE=(--exclude=d1/b_* --exclude=d1/c_*)
+ rsync -avz '--exclude=d1/b_*' '--exclude=d1/c_*' d1 d2
sending incremental file list
d1/
d1/a_1
d1/a_2
d1/a_3
d1/a_4
d1/a_5

sent 324 bytes  received 115 bytes  878.00 bytes/sec
total size is 0  speedup is 0.00
miri@miri-IdeaPad-3:~/Temporary$ 
miri@miri-IdeaPad-3:~/Temporary$ ll d2/d1/
total 0
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_1
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_2
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_3
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_4
-rw-rw-r-- 1 miri miri 0 Jul 10 20:08 a_5
miri@miri-IdeaPad-3:~/Temporary$ 


```

If the directories' names contain whitespaces quote them like so:

```
#!/bin/bash
set -x

if true 
then
 EXCLUDE=( --exclude=**"dir 1"/**b_* --exclude=**"dir 1"/**c_* ) 
else 
 EXCLUDE='' 
fi

**rsync -avz "${EXCLUDE[@]}" "dir 1" "dir 2" **

```

This is just a simple test to prove that arrays are the way to go. For your needs modify the rsync and EXCLUDE command in the script.

---

### Post by Paddy Landau on 2021-07-11
> **erind said:**
> It works fine on my end. Here it is a proof of concept case:
I believe you. It just doesn't work for me. I've done exactly as you describe, but it doesn't work.

Somehow, we must have different settings somewhere.

---

