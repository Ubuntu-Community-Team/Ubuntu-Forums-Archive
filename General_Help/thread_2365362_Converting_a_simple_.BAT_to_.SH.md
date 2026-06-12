---
title: "Converting a simple .BAT to .SH"
date: 2017-07-06
forum: General Help
---

### Post by impulse6662 on 2017-07-06
[COLOR=#242729][FONT=Arial]So I have this .BAT file:[/FONT][/COLOR]
```
[COLOR=#7D2727][FONT=inherit]@echo[/FONT][/COLOR][COLOR=#303336][FONT=inherit] on
start [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"<MyAppTitle>"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]MyAppLocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]command[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]parameter[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial]I'm wondering what would be the Linux equivalent. The more I look into it the more confused I get...[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I've been playing with gnome-terminal as I'm on Ubuntu right now, but I can't get it to work. Any help please?[/FONT][/COLOR]

---

### Post by raleigh3 on 2017-07-06
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by vocx on 2017-07-06
> **impulse6662 said:**
> [COLOR=#242729][FONT=Arial]So I have this .BAT file:[/FONT][/COLOR]
```
[COLOR=#7D2727][FONT=inherit]@echo[/FONT][/COLOR][COLOR=#303336][FONT=inherit] on
start [/FONT][/COLOR][COLOR=#7D2727][FONT=inherit]"<MyAppTitle>"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]MyAppLocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]command[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#303336][FONT=inherit]parameter[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial]I'm wondering what would be the Linux equivalent. The more I look into it the more confused I get...[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I've been playing with gnome-terminal as I'm on Ubuntu right now, but I can't get it to work. Any help please?[/FONT][/COLOR]
This totally depends on what you want to do. Is "start" a program? Or just part of the required syntax in Windows?

A .sh file is a Bash file, which is a complete programming language, although it is mainly used for automating small, repetitive tasks, typical of an operating system.

In Bash, commands are basically lists of words separated by white space (spaces). The first word is the name of the program, the following words are arguments for that program. For example,
```

program argument1 argument2 argument3

```

This will run "program" with the three options "argument1", "argument2", "argument3". The name of the program can be given as a single word (in which case it should be in a special folder in your system where most executables reside), or the full path should be given. The options can be single words, or it can also be symbols, or other things enclosed in double or single quotes.
```

/usr/bin/program +argument1 --long-option "parameters with spaces"

```

The code is equivalent to the first example. It has one program, and three arguments
```

program = /usr/bin/program
arg1 = +argument1
arg2 = --long-option
arg3 = parameters with spaces

```

The third argument is enclosed in double quotes so it remains a single unit, instead of breaking into three arguments, as it would without the quotes.

This are the basics. There are many programs consisting of a single word, and the rest is just reading the manuals of the specific programs. The program "man" shows the manual of any other program given as argument.
```

man ls
ls
man cd
cd Downloads
touch somefile.txt
rm somefile.txt
cd
/my/app/location/program parameter

```

This is probably the equivalent to what you want, but without knowing further details of what you want to do it may or may not work for your case.
```

/my/app/location/program parameter

```

To learn Bash well, you need to understand two things: syntax, and the programs themselves. The syntax is the special way Bash interprets the characters in your command. For example, the parentheses and brackets mean something special, so they should be treated with care. The programs themselves each of them has options that only apply to that particular program, so if you use a particular option with a different program it will not automatically work.
```

for i in Downloads/*
do
    echo "$i"
done

```
This is a special construct of Bash to do a for loop on a list of files. The basic program is just
```

echo "$i"

```

Which can be understood as
```

program = echo
arg1 = $i

```

So, the for loop is part of the syntax of Bash, while the program is pretty simple in this case.

---

