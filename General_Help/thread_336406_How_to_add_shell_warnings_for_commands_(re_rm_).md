---
title: "How to add shell warnings for commands? (re: rm *)"
date: 2007-01-11
forum: General Help
---

### Post by standards on 2007-01-11
I don't know how often this happens to everyone else, but seems like on a monthly basis (and you guessed it-- just now) I will accidentally delete the contents of a directory I was working in by typing

`rm velocity *` 

instead of 

`rm velocity*`

when I had hundreds of velocity# files to clean up. Is there anyway to make the shell prompt for a confirmation on this? It seems logical to me for there to be warning by default; if you're going to delete a directory you'd do it from it's parent, not by erasing everything inside first.

I'm sure all it takes is a few lines in my .bashrc, but I am terrible at figuring that kind of stuff out. Anyone want to do me a HUGE favor?? Aliasing ala `rm -i` is too simplistic, it's only a goof when the asterisk gets loose. 

Thanks!

---

### Post by bodhi.zazen on 2007-01-11
In ~/.bashrc:

> # Confirm
alias mv='mv -i'
alias cp='cp -i'
alias rm='rm -i'

# No colbber 
set -o noclobber # Override >|

---

### Post by koenn on 2007-01-11
aliasing ala 'rm -i' is meant exactly this type of situations. I don't really understand how you can otherwise instruct a computer to "only ask confirmation when i made a mistake - don't ask confirmation if I know what i'm doing". How's the poor thing gonna make the distinction ? 

There's a saying in unix circles that "Unix does not prevent you from doing something stupid, because it does not want to prevent you from doing something really smart". 
There are situations where a rather unorthodox command line could be a simple and elegant sollution - so it would be bad if the os or the shell refuses to execute it because it assumes you made a mistake. 

Also, unix commands (so linux commands usually too) are by default "quiet" - they do what you ask them to do and only report back if something went wrong. This is excelent for use in scripts and "pipes", i.e. commands chained together, with the output of one command given to the next command for further processing. This is a very powerfull tool, but it wouldnit work with noisy commands that produce irrelevant output or require additional confirmation from a user (such as : are you sure you want to do this ? Are you really sure ? If you do this then ... will happen, is that what you want ? ... )
The assumption is that you know what you're doing and are aware of the consequences, and that you only need to be informed if the command **failed** to do what you resuested.

---

### Post by standards on 2007-01-11
Seems to me the distinction is obvious- if there's a loose clobber or if there isn't. Very easy to tell apart. Don't warn me every time I use rm, but do warn me whenever I'm rm-ing a loose clobber. 

Personally, executing `rm *` is 99% of the time is a costly mistake. I'll go out on a limb and say it probably is for most people too, or at least with the people I work with. Regardless, rare enough and dangerous enough to warrant a confirmation, at least optionally. And even if it came by default, I've never run across a script or makefile that executed `rm *` and for the life of me I can't imagine a scenario when that would be wise or appropriate.  

Anyway, thanks bodhi.

---

### Post by rioghal on 2007-01-11
> **standards said:**
> I don't know how often this happens to everyone else, but seems like on a monthly basis (and you guessed it-- just now) I will accidentally delete the contents of a directory I was working in by typing

`rm velocity *` 

instead of 

`rm velocity*`


'rm velocity*' wouldn't have worked either, unless you had velocity1, velocity2, velocityother directories. I think what you meant was 'rm velocity/*  (with a "/"). As hard as it may be to hear, I recommend paying attention to what you're typing.. no offense intended.

---

### Post by ~LoKe on 2007-01-11
> **rioghal said:**
> 'rm velocity*' wouldn't have worked either, unless you had velocity1, velocity2, velocityother directories. I think what you meant was 'rm velocity/*  (with a "/"). As hard as it may be to hear, I recommend paying attention to what you're typing.. no offense intended.

> when I had hundreds of velocity# files to clean up
I recommend you pay attention to what you're reading.

---

### Post by rioghal on 2007-01-11
> **~LoKe said:**
> I recommend you pay attention to what you're reading.

Ohh, I"m so scared.

---

