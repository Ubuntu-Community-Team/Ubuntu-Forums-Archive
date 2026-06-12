---
title: "alias for &quot;cd&quot; command using tcsh shell"
date: 2016-07-31
forum: General Help
---

### Post by c_xy on 2016-07-31
Hello,

We are using Ubuntu 14.04 and tcsh shell.

Typically when you type the command "cd" in a terminal:

```
% cd
```

It changes directory to your $HOME directory.

We want to change this behavior by creating an alias to change to a directory other than $HOME.

I've tried using commands in the .chsrc file such as:

```
alias cd 'cd /different/directory/ 
```

Given the setup we are working with, we can't change the $HOME directory nor use bash. 

Since we are using tcsh, we are restricted to using aliases and not functions.

Is this possible? Again, we just want to change to "/different/directory" only when the command "cd" is used with no arguments/path specified. We want it to behave as usual if a path is specified with the "cd" command.

Any input/help is appreciated.

Thank you.

c.

---

### Post by Keith_Helms on 2016-08-01
I think putting a default directory name in the alias is going to screw up when you specify an actual directory.  You say you can't use functions in tcsh (I don't use it), but you can use scripts.

Try writing a script to do what you want and then alias cd to the name of the script.

My hack at what the script might look like:
```
#!/usr/bin/tcsh

if ($#argv == 0 ) then
   c\d "/default_directory"
else
   c\d "$argv"
endif
exit
```

then:
```
alias cd 'source scriptname'
```

By the way, this would have been MUCH easier in bash!!!

---

### Post by banceu_sergiu_ione on 2016-08-01
Does [CDPATH]("http://www.theunixschool.com/2012/04/what-is-cdpath.html") do your case?

---

### Post by c_xy on 2016-08-01
Thanks Keith for your response:

I tried your code:

```


if ($#argv == 0 ) then
   cd "/data"
 
else
   cd "$argv"
    


endif
exit



```

And added the line below in my .cshrc file

```
 alias cd  'source /directory/location/scriptname' 
```


However, every time I try to change to a directory:

```
cd /destination/folder 
```

I always end up back to the $HOME directory. I doesn't matter if I type only "cd" or "cd /different/location/folder", I always end up back to the $HOME directory.  For the $argv part of the script, how is that value assigned? Do I explicitly assign it or is it assigned after the cd command executes?


[COLOR=#000000]banceu_sergiu_ione,

[/COLOR]> [COLOR=#000000]Does [/COLOR][CDPATH]("http://www.theunixschool.com/2012/04/what-is-cdpath.html")[COLOR=#000000] do your case?[/COLOR][COLOR=#000000]

[/COLOR]I've never used CDPATH in the past. I tried with little success.  From my understanding, you would still need an argument after the cd, no? In my case, I would want to just type "cd" by itself. And then it would go to the designated directory configured under an alias.


c

---

### Post by Keith_Helms on 2016-08-01
> I tried your code:

     Code:
     if ($#argv == 0 ) then
   cd "/data"
 
else
   cd "$argv"
    


endif
exit 
And added the line below in my .cshrc file

     Code:
      alias cd  'source /directory/location/scriptname' 

However, every time I try to change to a directory:


Did you put the slash in the middle of the cd commands in the script?
```
c\d "$argv"
```

That WASN'T a typo.  I found it necessary to avoid recursively invoking the cd alias.  I installed tcsh on my system and the script and alias did work for me.

---

### Post by c_xy on 2016-08-02
> **Keith_Helms said:**
> Did you put the slash in the middle of the cd commands in the script?
```
c\d "$argv"
```

That WASN'T a typo.  I found it necessary to avoid recursively invoking the cd alias.  I installed tcsh on my system and the script and alias did work for me.

Keith, thank you very much. That was it! I changed to:

```
c\d "$argv"
```

Just like you suggested at the onset.

Now it works! Thanks. This was really a big help.


c

---

