---
title: "How to run program from other directory with short commands?"
date: 2015-04-17
forum: General Help
---

### Post by flaymond on 2015-04-17
Hello! I still can't figure this out, of how can I export path as variable or alias that I can simply access with ./example or just by example. It's sometimes annoying, because you have to access a program using the full path like /home/user/that/my/program/path. 

In my situation -

The program is in /home/user/.test/dir/program.

How can I access the 'program' with just a single command like 'python' or 'sudo'.

I want to access the program with this name - jon or ./jon

Is there anyway I can do this?

Any help is very appreciated.

---

### Post by Lars Noodén on 2015-04-17
If you put it in ~/bin, the next time you log in, it will be available to run as a single name rather than providing the whole path.  Otherwise, you have to modify your bash profile (~/.profile) to add the unusual directory to your $PATH environment variable.

---

### Post by btindie on 2015-04-17
What's already in your path?
```
echo $PATH
```
Usually if you've got a bin directory in your home directory that will automatically be added to your PATH. So you could create a symlink in there pointing to the program you want.
```
ln -sf /home/user/.test/dir/program ~/bin/program
```

Or you could manually add that directory to your PATH variable with
```
 export PATH=/home/user/.test/dir:$PATH
```
Though that will be lost when you log out, but you could create an alias with that command to make it quick to set
```
 alias pathadd='export PATH=/srv/bin:$PATH'
```

Or if it's just a single program that you want access to, you could just define an alias for it
```
 alias myprog=/home/user/.test/dir/program
```

That'll be lost when you end your session but you can make it persistent by adding it to the ~/.bash_aliases file.

Plenty of options to choose from.

---

### Post by flaymond on 2015-04-17
[QUOTE=Lars Nooden]If you put it in ~/bin, the next time you log in, it will be available to run as a single name rather than providing the whole path.  Otherwise, you have to modify your bash profile (~/.profile) to add the unusual directory to your $PATH environment variable.[/QUOTE]

Unfortunately, this program is depending on 3rd party libraries. If I moved the executable into /bin, error will come out because not found any depends. Should I move the whole .test directory to the /bin or can I try the exporting the variable stuff? I tried ```
 export PATH=$PATH:/home/user/.test/dir/program
```. I also tried to execute it with program or ./program, but the execution commands give 'not found' error. How can I access the program from home without execute the whole path?

---

### Post by flaymond on 2015-04-17
[QUOTE=btindie]Or if it's just a single program that you want access to, you could just define an alias for it
    Code:
     alias myprog=/home/user/.test/dir/program
That'll be lost when you end your session but you can may it persistent by adding it to the file ~/.bash_aliases[/QUOTE]

Thanks! That's worked just like I want!!! Thanks btindie and Lars Nooden for helping me out! I appreciate it! :D

---

### Post by oldos2er on 2015-04-17
> **InterProg said:**
> Unfortunately, this program is depending on 3rd party libraries. If I moved the executable into /bin, error will come out because not found any depends. Should I move the whole .test directory to the /bin or can I try the exporting the variable stuff? 

I know you have this problem solved, but I just wanted to point out that the suggestion you were given was to move the file to ~/bin and not /bin. The tilde "~" is a short way of writing "/home/user/" which you can use in terminal commands, for example ```
mkdir ~/bin/
``` will create a "bin" folder in your home folder.

/bin is a system folder that you as a user shouldn't need to write to directly.

---

