---
title: "Bash prompt breaks with newline character"
date: 2013-11-06
forum: General Help
---

### Post by drmrgd on 2013-11-06
The data analysis server that I work with tends to have very long directory and file names, and often as I'm crunching through the data, it gets a bit hard to see where I'm at.  To combat this, I've colorized my bash prompt.  I also added a newline character at the beginning of the prompt so that I get a little whitespace in there to help.  This works great except in cases where the path is so long that it has to wrap.  In that case, it partially wraps, then breaks and continues on a new line:

```

[ user@Host:~/this.this.going.to.be.one.long/director.that.I.need.to.see/if.i.can.fit.into.the.prompt/test/test/test/te
st/te
st/another/long/dir/structure/to/add/to/the/prompt ] $

```

the PS1 format I'm using is as follows:

```

PS1='\n\[\033[01;31m\]$(statstring)\[\033[00m\][ ${debian_chroot:+($debian_chroot)}\[\033[01;96m\]\u@\h\[\033[00m\]:\[\033[01;93m\]\w\[\033[00m\] ] \$ '

```

If I remove the newline at the beginning, I don't have any wrapping problems, but I've really grown to like this prompt as it definitely helps reading.  

Any suggestions as to what I might be doing wrong, and / or any suggestions as to how I can get a newline so that output looks more like:

```

[ user@Host:~ ] $ ls
Downloads       miscProgs      perl_source              Public                          Videos


[ user@Host:~ ] $

```

---

### Post by jamesisin on 2013-11-06
First let me say that I don't understand most of what your PS1 is doing.  Ok, that being said...

In mine if I were going to include a newline just prior to my new prompt I think it would something like this:

```
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}**\n**\u@\h:\w\$
```

Perhaps merely placing your new line later in the variable is the right solution.

---

### Post by drmrgd on 2013-11-06
> **jamesisin said:**
> First let me say that I don't understand most of what your PS1 is doing.  Ok, that being said...

In mine if I were going to include a newline just prior to my new prompt I think it would something like this:

```
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}**\n**\u@\h:\w\$
```

Perhaps merely placing your new line later in the variable is the right solution.

Thanks for the suggestion.  I think that if I add a newline character there, though, it would line break the prompt in a different place than I intend.  

Most of the prompt is color formatting (which I want to convert with tput to make a little more readable...one of these days!).  The '$(statstring)' bit is a call to a function that will display the return code of the last command, if it didn't exit with 0.   After all's said and done, it looks like the attachment.  Kind of humble still, but a lot easier to find when I've got too much going on in the terminal!

---

### Post by jamesisin on 2013-11-06
Do you need quotes around your variable (your function)?

```
\n\[\033[01;31m\]$(**"statstring"**)\[\033[00m\][ ${debian_chroot:+($debian_chroot)}\[\033[01;96m\]\u@\h\[\033[00m\]:\[\033[01;93m\]\w\[\033[00m\] ] \$ 
```

---

### Post by drmrgd on 2013-11-06
> **jamesisin said:**
> Do you need quotes around your variable (your function)?

```
\n\[\033[01;31m\]$(**"statstring"**)\[\033[00m\][ ${debian_chroot:+($debian_chroot)}\[\033[01;96m\]\u@\h\[\033[00m\]:\[\033[01;93m\]\w\[\033[00m\] ] \$ 
```

Hmmm...no, I don't think that should matter.  I can't come up with a reason to quote a function, and the function has always worked well unquoted.  Gave it a shot, though, just for the heck of it, and found that locally on this terminal (the OP was from an SSH session), the color doesn't reset on one of these broken multilines either (see the attachment).  When the line isn't broken, the color resets just fine and, in fact, everything works completely fine.  It's just when the prompt gets long enough to have to wrap is when I have issues with the newline character.  

[ATTACH=CONFIG]247620[/ATTACH]

I might have to just live with it or go without.  Lots of Googling around, seems that there's a lot you can do with the prompt, but it can be a bit flaky and buggy at times.

---

### Post by jamesisin on 2013-11-07
Maybe the whole thing needs a quote so it doesn't get broken when the line breaks (when it gets too long)?

---

### Post by drmrgd on 2013-11-07
> **jamesisin said:**
> Maybe the whole thing needs a quote so it doesn't get broken when the line breaks (when it gets too long)?

It's already quoted with a single quote.  But from your idea, I thought to try double-quotes instead (although I can't come up with a reason why that should matter here).  Anyway, no dice.

I played around for a little tonight and learned:

Changing to tput color codes does not fix the problem.  Still get the same exact results, and given I had to basically retype the whole thing, the chance of me making the same syntax / typo twice is pretty slim (I hope!).

I can change just about any component of the PS1 definition without having any affect. However, if I modify anything after the the '\w' part, that's when I see a real change.  Normally, I'm resetting the format right after the '\w' escape.  However, if I remove that reset, the line wrap is correct, but of course the color is not.  

Looking around it seems that sometimes I see '\e[00m' as the ANSI reset, and sometimes it's like this (which is what I used) '\[\033[00m]'.  Which is correct?  I do see some difference depending on which I use, but the former doesn't always seem to work right.

I have a hunch that there's something that's not resetting correctly and I have to play a bit more.  I think I'm either close to a solution or close to insanity on this one!

---

### Post by tgalati4 on 2013-11-08
Would it be easier to use symbolic links to shorten the directory length to something reasonable?

Also is the line-wrapping behavior the same in different xterms?  There are several terminal emulators, try different ones to see if it is emulator-dependent.

---

### Post by drmrgd on 2013-11-08
> **tgalati4 said:**
> Would it be easier to use symbolic links to shorten the directory length to something reasonable?

Also is the line-wrapping behavior the same in different xterms?  There are several terminal emulators, try different ones to see if it is emulator-dependent.

Yeah, I was trying to avoid path shortening.  But, at this point I've read about as much as I care to about ANSI and tput controls (honestly, this stuff is complete black magic!), and any change I make that fixes the wrapping issue breaks something else.  So, I think I'll just use the directory shortening variable available to Bash v4.0+ (which pretty much all of the machines I work on are running), to trim up the prompt.  Playing with different term emulators is another very good idea.  But, I'm not sure it's worth the hassle.  

Anyway, for any one interested, here's where I ended up.  Seems decent enough for now

 ```

# TPUT term codes
tblack=$(tput setaf 0)
tred=$(tput setaf 1)
tgreen=$(tput setaf 2)
tyellow=$(tput setaf 3)
tblue=$(tput setaf 4)
tmagenta=$(tput setaf 5)
tcyan=$(tput setaf 6)
twhite=$(tput setaf 7)


# 255 colors
tblue27=$(tput setaf 27)


treset=$(tput sgr0)
tbold=$(tput bold)


# Get return code of last command
function statstring {
return_code=$?
  if [ "0" != $return_code ]; then
      #printf "[$return_code] "
      echo -e "$tbold$tred[$return_code]$treset "
  fi
}


PROMPT_DIRTRIM=5
        
if [ "$color_prompt" = yes ]; then
    if [ "$USER" = root ]; then
        PS1='\n$(statstring)\[$tbold\][ \[$tred\]\u@\h: \[$tyellow\]\w\[$twhite\] ] \$\[$treset\] '


    else
        PS1='\n$(statstring)\[$tbold\][ \[$tblue27\]\u@\h: \[$tyellow\]\w\[$twhite\] ] \$\[$treset\] '
    
    fi
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

```

[ATTACH=CONFIG]247673[/ATTACH]

Thanks for all of the help and suggestions guys!

---

### Post by jamesisin on 2013-11-08
Some times good enough is just that.

---

