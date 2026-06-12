---
title: "script to pass extra options in front of 'ordinary' options of a program."
date: 2014-02-06
forum: General Help
---

### Post by krafczyk-matthew on 2014-02-06
Hi, I'm wondering how I can pass a set of extra options in front of 'ordinary' user passed options for a given command.

Initially I tried something like this:

if foo is the original command, then I'd make a script called foo to replace it. lets say foo resides in /usr/bin/foo.
Then I'd move the original foo to /usr/bin/foo.original and then have the new script be in /usr/bin/foo. Then the
content of the script would be:

```
#!/bin/bash
/usr/bin/foo.original --extra-argument-1 --extra-argument-2="string_2" $@
```

Now this style works fine for most user passed arguments.

HOWEVER, If an argument you pass is some sort of string with a space in it, you're screwed. like if I tried to do

```
foo --test-option-1
```

it would be fine. But if I try to do 

```
foo --test-option-2="This is a string"
```

everything is screwed up.

Is there another way to accomplish what I'm trying to do here? I feel like this would work, but whenever you enter foo <arguments> on the command line, your shell ruins the user passed arguments. If there was a way to turn off this behaviour for the duration of the command, then that would do it I think. However I don't know any command to bash which does this..

---

### Post by Impavidus on 2014-02-06
Instead of a script you could use an alias:```
alias foo='foo --extra-option-1 --extra-option-2'
foo arg1 arg2
#Gives the effect of foo --extra-option-1 --extra-option-2 arg1 arg2
foo "argument with spaces"
#Gives the effect of foo --extra-option-1 --extra-option-2 "argument with spaces"
```
You can define the alias in your .bashrc.
This doesn't work if the extra options are variable.

If you use a script instead of an alias, best place it in /usr/local/bin. This automatically takes precedence over the one in /usr/bin and won't be overwritten in case of an automatic system update. The original /usr/bin/foo will still be present at the same location, but will require the full path instead of just the command name.

---

### Post by Vaphell on 2014-02-06
you shouldn't pollute system directories with your own inventions, you got $HOME/bin for that

and if you wrapped $@ in double quotes it would work just fine

```
$ set -- --p1=param1 --p2=param2 --p3="this is string" 
$ printf "[%s]\n" [COLOR="#FF0000"]$@[/COLOR]
[--p1=param1]
[--p2=param2]
[COLOR="#FF0000"][--p3=this]
[is]
[string][/COLOR]
$ printf "[%s]\n" [COLOR="#0000FF"]"$@"[/COLOR]
[--p1=param1]
[--p2=param2]
[COLOR="#0000FF"][--p3=this is string][/COLOR]
```

example of what you want to achieve using functions
```
$ show_params() { printf "[%s]\n" "$@"; }
$ wrapper() { show_params --p1=1 --p2=2 "$@"; }
$ wrapper --p3="this is string"
[--p1=1]
[--p2=2]
[--p3=this is string]
```

---

### Post by krafczyk-matthew on 2014-02-06
Thanks for your replies Impavidus, and Vaphell

Impavidus will work for most commands, however in particular I'm interested in using this with gcc and g++. And in this case, there are a lot of configure scripts and makefiles which refer directly to /usr/bin/gcc or /usr/bin/g++. I'll try this and see if I can get it to work, but I recall doing something like this in the past, and the alias winds up not being able to work somehow.

I will need to try Vaphell's Let's see if I can make it work.

---

### Post by krafczyk-matthew on 2014-02-07
Vaphell,

Your solution seems to be working. Thanks a lot!

I'll mark the thread as solved.

---

