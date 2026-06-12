---
title: "How to use the output of one command as parameter of another command?"
date: 2007-08-20
forum: General Help
---

### Post by Nuld on 2007-08-20
I was wondering if what I'm doing in two lines can be done in just one line. Let's take the following as example:
I'm trying to get the total size of several files returned by "find" with "du -hsc". I can do it in two lines by copying/pasting the output of the first line to the end of the second line, but is there a way to do it in just one line?

This is how it works with two lines:
find . -iregex 'my pattern' | sed ':repeat;$!{$!N;b repeat};s/\n/ /g'
du -hsc <paste the output of the previous line here>

Thanks :)

---

### Post by strabes on 2007-08-20
I think it involves using >> in between the commands. Maybe someone more knowledgeable can help you out.

---

### Post by meatpan on 2007-08-20
There are several solutions.  You can use command substitution via backtics (`), or the $(command) syntax.  Also, the 'xargs' program can be useful for supplying output info to another program.  

Since you are already using the 'find' command, I recommend adding the '-exec' argument.  This arg is very useful, because it allows you to apply a command to each file returned via find.  Example  syntax: 'find [... regular find args] -exec [command arg1 arg2] {} \;'

The {} is replaced by each 'found' file.  -exec must be terminated with ';'.  Escape the ';' so your shell doesn't interpret it prior to passing it to find.

---

### Post by OrganicPanda on 2007-08-20
I'm not feeling up to decoding your code and giving you a working example but you could simply load the output to a variable then pass the variable, like so:

```

variable_name=`uname -a`
my_script $variable_name

```

notice the uname -a command is encapsulated within --> ` <-- sorry i don't know what they are called, but it's the key left of the 1 key and above tab on my GB keyboard, so in theory you could just   put the whole first line in to a variable then pass that variable to the du -hsc command like:

```

variable_name=`find . -iregex 'my pattern' | sed ':repeat;$!{$!N;b repeat};s/\n/ /g'`
du -hsc $variable_name

```

note: this may not work with your code, I haven't checked it

Hope this helps.

---

### Post by Nuld on 2007-08-20
> **meatpan said:**
> 
Since you are already using the 'find' command, I recommend adding the '-exec' argument.  This arg is very useful, because it allows you to apply a command to each file returned via find.  Example  syntax: 'find [... regular find args] -exec [command arg1 arg2] {} \;'

The {} is replaced by each 'found' file.  -exec must be terminated with ';'.  Escape the ';' so your shell doesn't interpret it prior to passing it to find.

I know the -exec argument, but I don't see how it could help me in this case, because it would execute the "du" command for each of the files returned by "find" and I wouldn't get the total size of all the files combined.

---

### Post by Nuld on 2007-08-20
> **OrganicPanda said:**
> I'm not feeling up to decoding your code and giving you a working example but you could simply load the output to a variable then pass the variable, like so:

```

variable_name=`uname -a`
my_script $variable_name

```

notice the uname -a command is encapsulated within --> ` <-- sorry i don't know what they are called, but it's the key left of the 1 key and above tab on my GB keyboard, so in theory you could just   put the whole first line in to a variable then pass that variable to the du -hsc command like:

```

variable_name=`find . -iregex 'my pattern' | sed ':repeat;$!{$!N;b repeat};s/\n/ /g'`
du -hsc $variable_name

```

note: this may not work with your code, I haven't checked it

Hope this helps.

Thanks, that works:

myvar=`find . -iregex 'pattern' | sed ':repeat;$!{$!N;b repeat};s/\n/ /g'`;du -hcs $myvar

Technically, it's still two lines though (because of the ; ). But now I don't have to do the manual copy/paste anymore :)

[Edit] Ah now I see how the command substitution mentioned by meatpan works. Good to know. Thanks!

---

