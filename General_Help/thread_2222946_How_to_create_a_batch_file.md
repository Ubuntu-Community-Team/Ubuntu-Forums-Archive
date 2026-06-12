---
title: "How to create a batch file?"
date: 2014-05-08
forum: General Help
---

### Post by goghvv on 2014-05-08
Hi.
I currently have 5 c source files I've been working on, and every time I'm making a change in one (or more) of them, I have to recompile and run again.
This is very exhausting.
Is there a way to create some kind of batch file with shell commands in it, that can be executed one after the other?

To be more clear about what I'm trying to achieve here:
I have these 5 files:
```
backup.c
ex3.c
ex3_input.c
ex3_update.c
test.c
test2.c
```
sitting in the same folder.
I'm frequently making changes in them, and every time I have to recompile:
```
gcc ex3.c
gcc -o input.out ex3_input.c
gcc -o update.out ex3_update.c
gcc -o test.out test.c
gcc -o test2.out test2.c

```
(not all of them every time, sometime I only make changes in some of them, and therefore compiling some of them)
and run:
```
./a.out
```

What I'm trying to achive is putting all the above commands in one file that can be run with one command.
Can it be done?

Regards,
goghvv


BTW, does anyone know why Ubuntu creates file copies with ~?
for example, every time I'm making some change in the 'backup.c' file, running 'ls -l' shows this:

```
-rw-rw-r-- 1 **** backup.c
-rw-rw-r-- 1 **** backup.c~
-rw-rw-r-- 1 **** ex3.c
-rw-rw-r-- 1 **** ex3_input.c
-rw-rw-r-- 1 **** ex3_update.c
-rw-rw-r-- 1 **** test2.c
-rw-rw-r-- 1 **** test.c
```

What is this backup.c~ file, why is it creating it, and how can this be prevented?

---

### Post by oldos2er on 2014-05-08
On Linux they're called [shell scripts]("http://linuxcommand.org/writing_shell_scripts.php").

Some text editors automatically create a backup file of whatever you're editing, which is the backup.c~ file you see. Check the preferences of the program you're using if you want to disable this; personally I find it useful.

---

### Post by goghvv on 2014-05-08
Wonderful.
That was very useful.
Thanks a lot.

---

### Post by steeldriver on 2014-05-08
Although a simple shell script might be enough in this case, if you're getting into C programming you should consider getting to grips with the `make` program (and makefiles) - they have lots of advantages especially as the project gets more complicated. In your case you could just type

```

make all

```

and it would automatically track which source files have changed and just recompile those. I'm not too good at them myself tbh but something like this should work

```

CC = gcc

all: a.out input.out update.out test.out test2.out

a.out: ex3.c
    $(CC) -o $@ $<

input.out: ex3_input.c
    $(CC) -o $@ $<

update.out: ex3_update.c
    $(CC) -o $@ $<

test.out: test.c
    $(CC) -o $@ $<

test2.out: test2.c
    $(CC) -o $@ $<

```

NB the indents in the above MUST be tabs not spaces

IIRC member *dwhitney67* has posted some nice makefile examples on this forum in the past - a good start would be to check those out.

---

