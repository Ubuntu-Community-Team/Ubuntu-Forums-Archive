---
title: "Problem creating alias"
date: 2015-07-15
forum: General Help
---

### Post by peter1897 on 2015-07-15
I am trying to create this alias: **alias cd/='cd /'**. But when i restart bash i get this error: **bash: alias: `cd/': invalid alias name**

Why it doesn't want to create the alias?

---

### Post by steeldriver on 2015-07-15
From man bash

```

ALIASES
       Aliases allow a string to be substituted for a word when it is used as the first word of a simple command.  The shell maintains a list of aliases that may be  set  and
       unset  with the alias and unalias builtin commands (see SHELL BUILTIN COMMANDS below).  The first word of each simple command, if unquoted, is checked to see if it has
       an alias.  If so, that word is replaced by the text of the alias.  [B]The characters /, $, `, and = and any of the shell metacharacters or quoting characters listed above
       may  not  appear  in an alias name.[/B]  The replacement text may contain any valid shell input, including shell metacharacters.  The first word of the replacement text is
       tested for aliases, but a word that is identical to an alias being expanded is not expanded a second time.  This means that one may alias ls to ls  -F,  for  instance,
       and  bash does not try to recursively expand the replacement text.  If the last character of the alias value is a blank, then the next command word following the alias
       is also checked for alias expansion.

```

---

### Post by sudodus on 2015-07-15
I think you cannot have a slash in the alias name.

Maybe cdr (for cd root) would be OK?

```
alias cdr='cd /'
```

Using [noparse]```
tags
```[/noparse] makes it easier to read command line input and output.

---

### Post by slickymaster on 2015-07-15
**/** and **\** are among the characters which cannot appear in a Bash alias name. From **man bash**:```
The characters /, $, `, and = and any of the shell metacharacters or quoting characters listed above may not appear in an alias name.
```

---

### Post by matt_symes on 2015-07-15
Hi

> **peter1897 said:**
> I am trying to create this alias: **alias cd/='cd /'**. But when i restart bash i get this error: **bash: alias: `cd/': invalid alias name**

Why it doesn't want to create the alias?

Because it's an invalid bash alias character.

From 

```
man bash
```
> 

...

ALIASES                                                                                                                       
       Aliases allow a string to be substituted for a word when it is used as the first word of  a  simple  command.   The
       shell  maintains a list of aliases that may be set and unset with the alias and unalias builtin commands (see SHELL
       BUILTIN COMMANDS below).  The first word of each simple command, if unquoted, is checked to see if it has an alias.
       If  so,  that  word  is  replaced  by  the  text  of the alias.  [B]The characters /, $, `, and = and any of the shell    
       metacharacters or quoting characters listed above may not appear in an alias name.[/B]

...



Works fine in zsh though.
```

matthew-laptop:/home/matthew/mainline_kernels:6 % echo $0
/bin/zsh
matthew-laptop:/home/matthew/mainline_kernels:6 % alias cd/='cd /'
matthew-laptop:/home/matthew/mainline_kernels:6 % cd/
matthew-laptop:/:6 % cd -
~/mainline_kernels
matthew-laptop:/home/matthew/mainline_kernels:6 % unalias cd/
matthew-laptop:/home/matthew/mainline_kernels:6 % 
```

You could always switch shells :)

EDIT:

Blimey. Three replies in the time it took me to type mine. Now that's service for you :D

Kind regards

---

### Post by peter1897 on 2015-07-15
Ok, thanks.
Is it possible to create alias that will allow me to use only **cd** command and then a root directory name? Something like this:
```
alias cd *='cd /*'
```  or wildcard signs are also not allowed? I want to avoid typing the **/** sign.

---

### Post by steeldriver on 2015-07-15
You could use a bash *shell function *
```

function cda() { cd "/$1" ; }

```
*('cd**a**' for 'cd**absolute**')*

---

### Post by matt_symes on 2015-07-15
Hi

> **peter1897 said:**
> Ok, thanks.
Is it possible to create alias that will allow me to use only **cd** command and then a root directory name? Something like this:
```
alias cd *='cd /*'
```  or wildcard signs are also not allowed? I want to avoid typing the **/** sign.

You can use a function.

Using the previous cdr example but extended to a function...

```

matthew-laptop:/home/matthew/Videos/15_07_2015:4 % bash
matthew@matthew-laptop:~/Videos/15_07_2015$ function cdr { cd /"$1"; }
matthew@matthew-laptop:~/Videos/15_07_2015$ cdr bin
matthew@matthew-laptop:/bin$ cd -
/home/matthew/Videos/15_07_2015
matthew@matthew-laptop:~/Videos/15_07_2015$
```

EDIT:

Ninja'd again :D

Kind regards

---

### Post by peter1897 on 2015-07-15
How to use the function? Do i have to put the function code in .bash_aliases or create a new file and insert it there? I am a noob in scripting.

---

### Post by matt_symes on 2015-07-15
Hi

> **peter1897 said:**
> How to use the function? Do i have to put the function code in .bash_aliases or create a new file and insert it there? I am a noob in scripting.

Put it in the file

```
~/.bashrc
```

You can create a seperate file (or files) and that is what i do but i do that only to help me organise my environment.

You'll need to logout and log back in for all your shells to use the new function.

You could re-source your ~/.bashrc file in each shell but logging out and back in is a sure fire way.

Kind regards

---

### Post by peter1897 on 2015-07-15
I put the line: **function cdr() { cd "/$1" ; }** in the end of .bashrc file and now if i type **cdr etc**, for example, it switches to /etc directory.

If i want to put the function in a separate file how should i proceed?

---

### Post by matt_symes on 2015-07-15
NHi

Create a new file in your home directory. Call it something like

```
.functions
```

Notice it's a dot file so will be hidden. This is a convention but only a convention.

At the top of the file write

```
#!/bin/bash
```

Add the function underneath the above text.

In the file ~/.bashrc, replace the function with the text

```
source ~/.functions
```

Add any new functions to that file.

As the file is being sourced, you should not have to make it executable.

Kind regards

---

### Post by matt_symes on 2015-07-15
Hi

I thought I would mention that I keep all my function and alias files in a directory called bin in my home directory. I then symlink them to my home folder. This makes for easy backup.

I have also set up my system so that when I edit and save any of my function or aliases files they get automatically sourced in all open shells so I don't have to do it manually or log back in.

I do this using inotifytools and traps. If you're interested I'll post the technique for you.

Kind regards

---

### Post by peter1897 on 2015-07-16
Thanks. I created the .functions file and put the code there and it is working.

If i understand correctly .bashrc is a file that is read on startup, on user logon, and it must contain links to other existing scripts in order for the scripts to work, correct?

---

### Post by matt_symes on 2015-07-16
Hi

> **peter1897 said:**
> Thanks. I created the .functions file and put the code there and it is working.

If i understand correctly .bashrc is a file that is read on startup, on user logon, and it must contain links to other existing scripts in order for the scripts to work, correct?

Yes. That's the basic idea.

If you read the first couple of paragraphs of the bash man page you'll get a really good description of the configuration files and when they are called. It's a better explanation than I could give you although, if you have any questions after reading it, we may be able to clarify it for you.

Kind regards

---

