---
title: "Modify bash to get rid of some annoyances"
date: 2007-11-25
forum: General Help
---

### Post by rich.bradshaw on 2007-11-25
Just blogged about a few tips and tricks to make bash more useful - most of you probably know about this, but beginners might find this of use!

[http://richbradshaw.wordpress.com/2007/11/25/bash-tips-and-tricks/](http://richbradshaw.wordpress.com/2007/11/25/bash-tips-and-tricks/)

Any problems/suggestions/comments, post them here or in my comments!

---

### Post by mojoman on 2007-11-25
Hmm, seem like a really good idea but when I start up bash I get 
```

bash: -a’: command not found
```

It's referring to the append history and I have it exactly as posted in the blogg:
```

shopt -s histappend
PROMPT_COMMAND=’history -a’
```

Any ideas on why?

EDIT: Nevermind. I shouldn't be so quick and certainly not so lazy. I just copied and pasted the text and therefore the quotation marks were not correct (don't see why though). When I replaced ’ with ' it works just fine.

EDIT2: And thanks for the tips! That lack of common history has been bugging me.:)

---

### Post by rich.bradshaw on 2007-11-25
OK, I mentioned on the blog that that might happen - think it's the blog template messing it up...

Thanks for your feedback!

---

### Post by Subban on 2007-11-25
Thanks a heap for posting this, its something thats been bugging me for a while, but hadn't got around to sorting it out (or even if it could be)

Someone give that man a beer :]

---

### Post by rich.bradshaw on 2007-11-27
OK - I fixed that by making sure the apostrophes are proper ones, not curly ones.

---

### Post by oscarsfriend on 2007-11-27
Hi, thanks for that.  The history thing was annoying me (I usually keep two or more tabs open in konsole).

I wonder if you know a fix for this annoying problem in bash.  Tab completion seems to have been made "clever".  For example: create a dummy text file like this "touch test.txt", then type "mplayer " (for example) then "te" then tab.  It will not show the file, and the terminal will beep at you!  Now try "nano te[tab]" or "gedit te[tab]" and it will complete the line as "nano test.txt"!  The problem is that not all file extensions are recognised for all commands.  E.g. run "touch movie.iso", then "kaffeine mo[tab]" or "mplayer mo[tab]" -- again, it will not see the file!  Run "k3b mo[tab]" and it will.  

Anyone know of a way to fix this?  Either to disable it, or add more file types?

---

### Post by rich.bradshaw on 2007-11-29
If you can see

source /etc/bash_completion

in ~/.bashrc , then remove that line. Otherwise, you can add

complete -r cd

to you ~/.bashrc

this will stop it being clever for cd. You could therefore add

complete -r kaffeine
complete -r mplayer

to stop that particular problem.

---

### Post by oscarsfriend on 2007-11-30
Thanks!  That worked perfectly!  (I removed the line from .bachrc.)

EDIT: Now I can see how it works, I think I'm going to have a go at hacking together my own version of /etc/bash_completion (I'll copy it to my home directory rather than mess with the original).

---

### Post by oscarsfriend on 2007-11-30
Here is another little tip.  When I had Fedora I used to be able to use the page up and down keys in bash.  They would take me to the top (not very useful) and bottom of the history.  They didn't work when I installed Ubuntu.  I sorted this by adding these lines to /etc/inputrc:

```

# PageDown moves to bottom of history
"\e[6~": end-of-history
# PageUp searches for keywords through history
"\e[5~": reverse-search-history

```

The only catch is that the reverse history search only works once, unlike using ctrl+r, where multiple presses takes you to previous matches.

Also, you can add things like this to your .bashrc:

```

alias cp="cp -iv"
alias mv="mv -iv"
alias rm="rm -vi"

```

These are especially good for bash noobs as they make it more difficult to overwrite files by accident, and can always be overridden with the -f switch.

---

