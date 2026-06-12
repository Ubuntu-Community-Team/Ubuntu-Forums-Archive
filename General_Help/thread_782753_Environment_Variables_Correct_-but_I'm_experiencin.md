---
title: "Environment Variables Correct -but I'm experiencing a really trivial problem!"
date: 2008-05-05
forum: General Help
---

### Post by _Azrael_ on 2008-05-05
Hi -I'm trying to get the Qt framework I've compiled and installed from source to work but the old packaged version has been interfering.

I've successfully installed Qt 4.3.4 and removed the old packaged libraries. My environment variables are set correctly. Everything should work now but I'm experiencing a trivial problem because of my inexperience (with Linux, life, death etc.8-[ ).

The main problem is that despite the environment variables being correct, the system doesn't respond to the respective commands. The PATH variable is as follows:
```
PATH=$/usr/local/Trolltech/Qt-4.3.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
yet the following occurs when I try to run a few Qt commands:
```
azrael@Incinerator:~$ which qmake
azrael@Incinerator:~$ qmake -v
The program 'qmake' can be found in the following packages:
 * libqt4-dev
 * qt3-dev-tools
Try: sudo apt-get install <selected package>
bash: qmake: command not found

```
But if I try a few commands from within the PATH directory itself I can get the desired result:
```

undesired result:
azrael@Incinerator:/usr/local/Trolltech/Qt-4.3.4/bin$ qmake -v
The program 'qmake' can be found in the following packages:
 * libqt4-dev
 * qt3-dev-tools
Try: sudo apt-get install <selected package>
bash: qmake: command not found

desired result:
azrael@Incinerator:/usr/local/Trolltech/Qt-4.3.4/bin$ ./qmake -v
QMake version 2.01a
Using Qt version 4.3.4 in /usr/local/Trolltech/Qt-4.3.4/lib
azrael@Incinerator:/usr/local/Trolltech/Qt-4.3.4/bin$ 

```
Why does the desired function occur when I run the command with ./prefixed? How is this triviality causing a system wide affect? Any help will be *much* appreciated as this is related to a deadline driven task](*,).

---

### Post by joshsmith on 2008-05-05
hey
i hope i can explain for you
./ seems odd, but what it really means is "in this directory"
"." means current directory
so when you run ./qmake you are running the file qmake in this directory
which is the same as if you ran the whole path in terminal ie
/usr/local/Trolltech/Qt-4.3.4/bin/qmake
(which you could run from anywhere)

the point is, if the program isnt in your path, you need to give the full path to the program to run it, 
"." is just a shortcut if you are already in the directory, the same as if you ran
../bin/qmake
as .. means the directory above.

hope that helps

as a question for you, how did you get the system to list your path.
ie give you
PATH=$/usr/local/Trolltech/Qt-4.3.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

ps, i guess you just have a $ sign where it is not needed, but the above explanation is more important

---

### Post by wirelessmonkey on 2008-05-05
It's odd that make install didn't insert the new files into /usr/sbin /usr/bin

---

### Post by _Azrael_ on 2008-05-05
My apologies for the delayed reply (was at the ol' dead end job).

Many thanks for the explanation johnsmith. All makes sense now. You were of course right about the extra $. Without the variable being correct... enough said I guess. 

@wireless monkey - I think those directories were ignored as I went with the default configuration for the install. The configure script sets up a Trolltech directory unless another is specified explicitly.

In any case, problem solved and thanks again! ):P

---

### Post by joshsmith on 2008-05-05
glad i could help, 
but could you tell me, what command do you run to get the output:
PATH=$/usr/local/Trolltech/Qt-4.3.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
?

---

### Post by wirelessmonkey on 2008-05-05
$: echo $PATH
will give you your path ;)

---

