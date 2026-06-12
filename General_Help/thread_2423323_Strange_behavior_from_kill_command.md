---
title: "Strange behavior from kill command"
date: 2019-07-21
forum: General Help
---

### Post by COKEDUDE on 2019-07-21
I am getting some strange behavior from the kill command. When I run the which command it says it points to /usr/bin/kill. When I look at my PATH I have /usr/bin in it. So why does running kill or /usr/bin/kill produce different outputs?

```
ghost ~
$ which kill
/usr/bin/kill

ghost ~
$ kill
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

ghost ~
$ /usr/bin/kill
Usage: kill [-f] [-signal] [-s signal] pid1 [pid2 ...]
       kill -l [signal]

Send signals to processes

 -f, --force     force, using win32 interface if necessary
 -l, --list      print a list of signal names
 -s, --signal    send signal (use kill --list for a list)
 -h, --help      output usage information and exit
 -V, --version   output version information and exit


```

---

### Post by again? on 2019-07-21
Probably because kill exists as a standalone utility as well as a shell built-in.
```
**type** --help
Options:
      -a	display all locations containing an executable named NAME;
    		[COLOR="#FF0000"]includes aliases, builtins, and functions[/COLOR], if and only if
    		the `-p' option is not also used
```

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] type -a kill**
kill is a shell builtin
kill is /bin/kill
```


```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] which kill**
/bin/kill
```

---

