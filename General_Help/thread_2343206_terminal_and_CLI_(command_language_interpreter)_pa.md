---
title: "terminal and CLI (command language interpreter) parsing and logic"
date: 2016-11-14
forum: General Help
---

### Post by jony123 on 2016-11-14
Hey ppl,

I have a question on the logic of the terminal.
How terminal parses the text that the user types and sends it to the right program?
How it knows which word is the option and which one is not?
Some words can be commands and other are options. each program has its own options.
Sometime commands are not performed by typing order (like '>')
A few commands can be in the same line (with "|")
Is it based on abstract syntax tree(AST)? or something similar? where can I find it?

thanks,

Jony

---

### Post by ian-weisser on 2016-11-14
Shell operands come first, read from left to right...but then executed in logical order. Written order is not the same as logical order (think '<' or $() ).

Each operand usually refers to a single application. Anything additional before the next operand is generally assumed to be an option or flag. Paths to available applications are listed in the $PATH env variable.

Each application is responsible for parsing it's own options and emitting it's own errors. Most applications try to create uniform output, safely assuming that the output will be promptly consumed by another application. Errors are reported to the shell and terminate the chain of applications.

The whole system is flexible, extendable, and maintainable....However, it's not smart, and can easily be outwitted.

---

### Post by Impavidus on 2016-11-14
The shell processes all shell operands and may start subshells in the process. It decides which programs to run and how to link inputs and outputs together using pipes, ordinary files, standard input/output/error and whatnot.

All options and arguments are passed to the application in the form of strings. If I run, for example, **sudo -k apt install -f**, then the shell will start the program **sudo**, giving it the strings "sudo", "-k", "apt", "install" and "-f". sudo interprets the parts it recognises as meant for sudo and will check my identity without updating my cached credentials. Then sudo will run **apt** with root as effective user ID, giving it the strings "apt", "install" and "-f". apt will process its list of arguments and will attempt to fix the package system.

---

### Post by jony123 on 2016-11-15
Thank you!

Do you have any idea if there is a parser or a code of the parser that I can get my hands on?(the one that is responsible on the logic order)

---

### Post by steeldriver on 2016-11-15
To what end? if you're trying to implement your own shell, there seem to be a good number of tutorials around (google something like "simple shell in c" or "implement simple shell") since it appears to be a quite common CS assignment 

If you're just interested in how programs parse their options and arguments, then I suggest starting with the documentation for the GNU getopt function

```

man 3 getopt

```

Of course you can download and browse the source code of any of the open source shell implementations

---

### Post by ian-weisser on 2016-11-15
Of course you are free to browse the source. It's open. Have fun.

The source code for the dash shell is at [http://git.kernel.org/cgit/utils/dash/dash.git](http://git.kernel.org/cgit/utils/dash/dash.git)

---

### Post by jony123 on 2016-11-17
hi,

Thank you for your reply.
it's not an assignment in uni.
I want to create a tool that will show for each command- which options are available.
I looked on the getopt() function and tried to understand where from the "optstring" is delivered but without luck.
I downloaded the source code of the gnome-terminal (an older version though) and looked for getopt() but also without luck.
Maybe I can look for "switch case" on each command implementation.
I know that I can get all the commands with one command but not the options.

Any help will be really appreciated!


(p.s-I just graduated from uni. so everything is new to me.)

---

### Post by ian-weisser on 2016-11-17
> **jony123 said:**
> I want to create a tool that will show for each command- which options are available.

Most people use manpages for that purpose.

Since an application (command) might be a shell script, or a perl script, or a python script, or a binary blob, or something else, scanning each application looking for how each developer chose to consume option strings in their own special way seems like quite a monumental task.

---

### Post by Impavidus on 2016-11-17
Some programs use getops(). Some programs use```

    while(--argc>0 && (*++argv)[0]=='-')
    {
        while(c=*++argv[0])
        {
            switch(c)
            {
                case 'h':
                    /* ... */
```
Some programs use something heavily obfuscated just for the fun of it (although I don't expect those in the Ubuntu repos). And that's even ignoring that every programming language has a different way of processing options.

The best way to learn the options of any particular program is reading its manual:```
man command
```
Most commands have -h or --help as standard option to print a help text, printing all other options they accept. Or at least the important ones.```
command -h
command --help
```

---

