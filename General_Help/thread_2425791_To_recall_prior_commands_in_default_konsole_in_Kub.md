---
title: "To recall prior commands in default konsole in Kubuntu 18"
date: 2019-08-30
forum: General Help
---

### Post by petrogromovo on 2019-08-30
Hello,
Using default konsole in Kubuntu 18.04 many ofter I push “<-” key to recall last commands in console to run it.
Sometimes it is boring and I want to ask if there is a way to check/open/view/see by eyes my last say 30 
commands(filtered without repeated commands)?
1) Some additive plugins? Maybe replacement of default konsole ?
2) Also in I know that is in default konsole I run some command which has leading space, it is not not recalled by pushing “<-” key
Is the is a way to fix it?

Thanks!

---

### Post by CatKiller on 2019-08-30
Your shell history is stored in .bash_history. You can view it with the history command.

Personally, I've edited my inputrc to search backwards and forwards through the history with Page Up and Page Down; that way I just type the first couple of letters and then hit Page Up to complete the line.

---

### Post by TheFu on 2019-08-30
This is controlled by the history and shell, usually bash.  There are many commands around history.  The manpage goes into most. There are many techniques that experts use to speed up solutions in a shell using a mix of command line editing and history.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) has some.  There are "Unix/Linux Power Users" books which show many more. 

I use history so often that I've aliased it as:
```
alias h='history'
```

and use it as second nature.  I also don't store any commands less than 4 characters into it and prevent longer commands I specifically don't want saved (like anything with a password) from being saved at all by starting the line with a space.

```
h|grep foo 
```
will show only the commands in the history with 'foo' in them.

If I know the last command that began with a 'z' is the one I want, then 
```
!z
```
will run it.
If I know I want to run a cmd from 3 steps ago, again
```
!-3
```
will run it.
When looking at the history list, there are numbers to the left of every line.  If line 283 has the command I want
```
!283
```
will run it.

You get the idea.  Those are the easiest.  You can reverse-search the history using <cntl>-r

So for your specific question, 
```
h| tail -n30 |unique
```
will get you close.  You'd need to remove the number in the 1st column after the **tail** using **cut**, but before the **unique**.  I'd make it an alias, like h30.  Sorry, I don't use cut enough to know it off the top of my head.

---

### Post by SeijiSensei on 2019-08-30
I just use the up and down arrows to navigate through my history in Konsole.

```
history | tail -n 30
```

will show the last thirty lines of your history.

---

### Post by petrogromovo on 2019-08-31
That 
```

~# h| tail -n30 |unique
Usage: unique OUTPUT-FILE
h: command not found

```

does not work. Please, clarify.

---

### Post by CatKiller on 2019-08-31
> **petrogromovo said:**
> That 
```

~# h| tail -n30 |unique
Usage: unique OUTPUT-FILE
h: command not found

```

does not work. Please, clarify.
. 
> **TheFu said:**
>  I use history so often that I've aliased it as:
```
alias h='history'
``` 

---

### Post by TheFu on 2019-08-31
> **petrogromovo said:**
> That 
```

~# h| tail -n30 |unique
Usage: unique OUTPUT-FILE
h: command not found

```

does not work. Please, clarify.
alias h as shown above. Thanks CK.

The unique is worthless above, since every line will have different number.  OTOH, removing the numbers will make the lines harder to use, so that won't be good either.

BTW, while you can run as root, that isn't the Ubuntu way and in the hands of someone really new, it is a good way to cause all sorts of trouble.

---

### Post by petrogromovo on 2019-09-01
Thanks!, but I got error on :
```

alias h='history'
$ h| tail -n30 |unique
Command 'unique' not found, but can be installed with:
sudo apt install john

```
I tried to install  john app, not it looks different. Misspelling?

---

### Post by SeijiSensei on 2019-09-01
Should be uniq. But none of the lines will be unique since they are numbered. You could filter them with sed, but why bother?

```
history | tail -n30 | sed 's/^[0-9]+//g' | uniq
```

Also I think you have to use the sort filter before uniq. On my phone at the moment so I don't have a terminal to experiment with.

---

### Post by TheFu on 2019-09-01
> **SeijiSensei said:**
> Should be uniq. But none of the lines will be unique since they are numbered. You could filter them with sed, but why bother?

```
history | tail -n30 | sed 's/^[0-9]+//g' | uniq
```

Also I think you have to use the sort filter before uniq. On my phone at the moment so I don't have a terminal to experiment with.

Ooops. Sorry.  s/unique/uniq/ throughout the stuff above.  
**sort** and **uniq** are old commands from the beginning Unix days, but some times those commands sneak in a new option that we don't see.  I think sort -u exists now, which would save an extra pipe and process.```

       -u, --unique
              with -c, check for strict ordering; without -c, output only  the
              first of an equal run
```
is from the sort manpage.
```
history | tail -n30 | sed 's#^[0-9]+##g' | sort -u
```
Whether sed or cut is used is personal preference.  Sed is probably heavier than cut.  I use sed 1000x more than cut, because it is so flexible.

But I think after all this, you'll find it really isn't very useful. ;(

Don't forget to limit the stuff that gets put into the history list, so you don't end up with 10 lines of 'ls' so you only get 20 lines of output. Do you see why that could happen?

---

### Post by SeijiSensei on 2019-09-01
Actually, try as I might, I can't get rid of the line numbers with sed. For one thing, there's a leading space before the numbers, but even using 

```
sed 's/^[[:space:]+][0-9]+//g'
```

didn't work. The [history man page]("https://linux.die.net/man/3/history") offers some possibilities, but all of this just doesn't seem worth it to me.

---

### Post by TheFu on 2019-09-01
sed was harder than I thought.  Never got it working here either and don't know why!

Try
```
$ history | tail -n30 | cut -d' ' -f 4-20   | sort -u
```

If you limit how many things are stored in the history, the '4' can be a '5' and more predictable.  It is a hack.

---

### Post by mc4man on 2019-09-01
This works here , with or without the | sort -u
```

history | tail -n30 | sed 's/^ *[0-9]* *//'
```

---

### Post by CatKiller on 2019-09-01
The numbers are put in by the history command itself; they aren't stored. You don't need to put numbers on and then try to finagle your way to removing them again.

You can use something like ```
cat $HISTFILE
``` if you want the contents of your history listed without numbers, or ```
tac $HISTFILE
``` if you want it reversed and without numbers.

There are a bunch of people playing around with ways to remove duplicates [here](https://unix.stackexchange.com/questions/48713/how-can-i-remove-duplicates-in-my-bash-history-preserving-order) and elsewhere. The shell history can remove consecutive duplicates automatically, it's the non-consecutive ones that can be tricky.

---

