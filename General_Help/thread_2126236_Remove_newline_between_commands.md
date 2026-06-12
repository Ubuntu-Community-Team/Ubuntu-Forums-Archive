---
title: "Remove newline between commands"
date: 2013-03-16
forum: General Help
---

### Post by terminator14 on 2013-03-16
If I have a file called testfile with the following contents:

```
one two three
```

and I want to combine reading a part of the file with echo to make stdout look like:

```
one five
```

I might try something like:

```
echo -n $(cat testfile | grep -o 'one'); echo ' five'
```

the 'echo -n' being necessary to prevent the newline. The problem with doing it this way is that if I wanted to only have "echo ' five'" run if the "cat testfile" section has an exit code of zero,  it can't be done (as far as I can tell). 

Is there a better way of suppressing a newline between commands? Basically the equivalent of "echo -n" but for all commands? Like maybe temporarily telling bash to disable newlines between commands?

---

### Post by prodigy_ on 2013-03-16
```
awk '/one/ { print "one five" }' testfile 2>/dev/null
```

---

### Post by papibe on 2013-03-16
Hi terminator14.

You can use the variable $? to access the exit code of the last command. In order to use it in your example, you would have to separate your commands a little bit. For example:
```
tmp=$(grep -o 'one' testfile); if [ $? = 0 ]; then echo 'one five'; else echo 'five'; fi
```
Does that help?
Regards.

---

### Post by schragge on 2013-03-16
> **terminator14 said:**
> The problem with doing it this way is that if I wanted to only have "echo ' five'" run if the "cat testfile" section has an exit code of zero,  it can't be done (as far as I can tell).From the [POSIX standard]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_01"):> If there is no command name, but the command contained a command  substitution, the command shall complete with the exit status of the last command substitution performed.So, this one should work, too.
```
tmp=`grep -o one testfile` && echo $tmp five
```

---

### Post by terminator14 on 2013-03-16
> **papibe said:**
> Hi terminator14.

You can use the variable $? to access the exit code of the last command. In order to use it in your example, you would have to separate your commands a little bit. For example:
```
tmp=$(grep -o 'one' testfile); if [ $? = 0 ]; then echo 'one five'; else echo 'five'; fi
```
Does that help?
Regards.

Thanks, but while the example I gave of cat stdout being piped to grep can be combined into a single command, the purpose of doing it as 2 commands was because the real problem I face (which I have greatly simplified in this thread) cannot have commands combined into a single one. While something like:

```
test@pc$ tmp=$(false)
test@pc$ echo $?
1
```

with a single command works great, something with 2 commands does not:

```
test@pc$ tmp=$(false | true)
test@pc$ echo ${PIPESTATUS[0]}
0
```

It outputs the error code of the last command run - in this case the command 'true', not the first command run (false).

> **prodigy_ said:**
> ```
awk '/one/ { print "one five" }' testfile 2>/dev/null
```

I haven't had much occasion to use awk, but as far as I can tell, this finds the word 'one' in the file testfile and if successful, prints "one five". I appreciate the effort, but this appears to have nothing to do with combining the output of 2 programs with no newline.

> **schragge said:**
> From the [POSIX standard]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_01"):So, this one should work, too.
```
tmp=`grep -o one testfile` && echo $tmp five
```

Same as the first example, && only handles the last command's exit code, and setting a variable to a command's output appears to remove all exit codes except the last one.

You guys are focusing too much on how many different ways a file can be read (with grep, with awk) and missing the point. Let me try a different example:

```
ls -1 | head -1; [[ ${PIPESTATUS[0]} -eq 0 ]] && echo ' <-- this is a file or dir'
```

This will print '' <-- this is a file or dir'' ONLY IF the ls command (not the head command) is successful. The only problem is that the output is on 2 different lines because a newline is created at ";". I need the output to be on the same line.

---

### Post by prodigy_ on 2013-03-16
> **terminator14 said:**
> combining the output of 2 programs with no newline
```
#!/bin/bash
a=$(command 1)
if [ "$?" == "0" ]; then
    b=$(command 2)
    echo $a $b | tr '\n' ' '
fi
```

---

### Post by terminator14 on 2013-03-16
The only working solution I've found is to run the original command twice:

```
tmp=$(ls -1 2>&1 | head -1); echo -n $tmp; ls -1 | head -1 &>/dev/null; [[ ${PIPESTATUS[0]} -eq 0 ]] && echo ' <-- this is a file or dir'
```

But not only is it running the command twice (which is dumb), it's also needlessly complicated and ugly.

---

### Post by terminator14 on 2013-03-16
> **prodigy_ said:**
> ```
#!/bin/sh
a=$(command 1)
b=$(command 2)
echo $a $b | tr '\n' ' '
echo
```

```

a=$(ls -1 | head -1)
b=$(echo ' <-- this is a file or dir')
echo $a $b
```

This does in fact work, but the

```
a=$(ls -1 | head -1)
```

part doesn't allow the exit code of the first part of the pipe (ls -1) to be viewed. So:

```

a=$(ls -1 | head -1)
EXIT_CODE=${PIPESTATUS[0]}
b=$(echo ' <-- this is a file or dir')
echo $a $b
echo $EXIT_CODE
```

will always produce an EXIT_CODE variable of 0, no matter if 'ls -1' exited with an exit code of 0 or not.

---

### Post by schragge on 2013-03-16
```
lsout=`ls -1`; lsstat=$?; headout=`head -1 <<<"$lsout"`; ((lsstat))||echo "$headout <-- this is a file or dir"
```

---

### Post by prodigy_ on 2013-03-16
First, $PIPESTATUS doesn't work the way you think it works. Second, if you want to check the exist status of a command, you should run the command, (optionally) assign its output to a variable and check $?. Any post-processing you can do on the contents of the variable. See my previous post.

---

### Post by papibe on 2013-03-16
What about this:
```
ls -1 | head -1 | xargs echo -n ; echo ${PIPESTATUS[*]}
```
You'll have both the result of the pipe with no newline, and access to all status from the pipe:
```
**somedir**0 0 0
```
Regards/.

---

### Post by terminator14 on 2013-03-16
> **schragge said:**
> ```
lsout=`ls -1`; lsstat=$?; headout=`head -1 <<<"$lsout"; ((lsstat))||echo "$headout <-- this is a file or dir"
```

I don't fully understand it, but it does work! Cool - thanks.

> **prodigy_ said:**
> First, $PIPESTATUS doesn't work the way you think it works. Second, if you want to check the exist status of a command, you should run the command, (optionally) assign its output to a variable and check $?. Any post-processing you can do on the contents of the variable. See my previous post.

I just got this to work as well:

```
a=$(ls -1)
EXIT_CODE=$?
a=$(echo "$a" | head -1)
b=$(echo ' <-- this is a file or dir')
[[ $EXIT_CODE -eq 0 ]] && echo $a $b
```

Seems pretty simple. Thanks.

[QUOTE=tldp.org/LDP/abs/html/internalvariables.html]$PIPESTATUS

    Array variable holding exit status(es) of last executed foreground pipe.[/QUOTE]

Which is exactly the way I think it works. How do you think it works?

---

### Post by prodigy_ on 2013-03-16
> **terminator14 said:**
> Which is exactly the way I think it works. How do you think it works?
Sorry for not being clear. :) What I mean is $PIPESTATUS can be rather unpredictable, so I wouldn't use it except for debugging and even then only with care.

Using your example:
```
$ set -x
$ a=$(ls -1 /root | head -1); echo ${PIPESTATUS[*]}                            
++ ls --color=auto -1 /root
ls: ++ head -1
cannot open directory /root: Permission denied
+ a=
+ echo 0
0
```

However:
```
$ set -x
$ a=$(ls -1 /root); echo ${PIPESTATUS[*]}
++ ls --color=auto -1 /root
ls: cannot open directory /root: Permission denied
+ a=
+ echo 2
2
```

---

### Post by terminator14 on 2013-03-16
> **prodigy_ said:**
> Sorry for not being clear. :) What I mean is $PIPESTATUS can be rather unpredictable, so I wouldn't use it except for debugging and even then only with care.

Using your example:
```
$ set -x
$ a=$(ls -1 /root | head -1); echo ${PIPESTATUS[*]}                            
++ ls --color=auto -1 /root
ls: ++ head -1
cannot open directory /root: Permission denied
+ a=
+ echo 0
0
```

However:
```
$ set -x
$ a=$(ls -1 /root); echo ${PIPESTATUS[*]}
++ ls --color=auto -1 /root
ls: cannot open directory /root: Permission denied
+ a=
+ echo 2
2
```

That was my point from the beginning. PIPESTATUS doesn't work in this case. As far as I know, that's because anything inside $( ) is executed in a shell with a different environment than anything outside of it, so PIPESTATUS has no clue what commands were run in that shell. The shell environment exists with the same exit code as the last command that ran in it did, but you can't get exit codes of individual commands within a pipe. So:

```
VAR=$( false | true ); echo ${PIPESTATUS[0]}
```

returns the exit code of the shell created within $(), which returns the same exit code as the last command run in it (true). Unless I'm still mistaken, it works exactly like I think it does.

Anyway - with your help I got the problem worked out. Thanks guys.

---

### Post by schragge on 2013-03-21
FYI, there's a command [mispipe]("http://manpages.ubuntu.com/manpages/precise/en/man1/mispipe.1.html") in the package *moreutils*.
[highlight]Update[/highlight]
Just found a workaround in the source of */usr/sbin/mkinitramfs*. It uses the solution from [comp.unix.shell FAQ]("https://groups.google.com/d/msg/comp.unix.shell/UHX-bBndq7k/KWoxBv7fCHoJ"). Basically, it distills to
```
{ ls_status=`{ { ls; echo $? >&3 3>&-;}|head -1 >&4 4>&-;} 3>&1`;} 4>&1
```

---

