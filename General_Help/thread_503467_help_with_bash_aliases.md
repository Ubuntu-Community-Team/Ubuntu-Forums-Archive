---
title: "help with bash aliases"
date: 2007-07-17
forum: General Help
---

### Post by d3dtn01 on 2007-07-17
I'm having trouble saving a bash alias. I have all my aliases in a single file (which is referenced by .bashrc). I wanted to add an alias for the following command:

```
for x in *.ogg ; do lame $x `echo $x|awk -F . '{print $1 ".mp3"}'`; done
```

Since the command has both single and double quotes within it, what do I use to surround the command. Normally I would create an alias like this:

alias aliasname='alias command'

I tried using the single quotes to surround the command but bash doesn't seem to like that.

Anyone have suggestions?

---

### Post by 5-HT on 2007-07-18
Barring modifying the alias itself, what about replacing your current single quotes with triple quotes, and use single quotes for the whole alias (haven't tried it out, if not I need to brush up on my BASH)?
cheers,

---

### Post by Mr. C. on 2007-07-18
Anything but trivial aliases should use a function instead:

```
function myfunc {
   for x in *.ogg ; do
      lame $x `echo $x | awk -F . '{print $1 ".mp3"}'`
    done
}

```
You can avoid the backtick by using the $( ) syntax, as in:

```
function myfunc {
   for x in *.ogg ; do
      lame $x $(echo $x | awk -F . '{print $1 .mp3}')
    done
}
```

No need to double quote the .mp3 - there's nothing special about that string.

Perhaps the **basename** function is what you really want instead of the echo | awk pipeline.

MrC

---

