---
title: "Add directory to path but can not run scripts from other directories"
date: 2022-10-08
forum: General Help
---

### Post by raleigh3 on 2022-10-08
I added this to .bashrc so I can run pythons scripts from any dir.

```
export PATH="/home/andy/Python/:$PATH"
```

My pythons scripts are in /home/andy/Python.

```
echo $PATH
[FONT=Arial Black]/home/andy/Python/:[/FONT]/home/andy/.local/bin:/home/andy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```

But I get this when I run python3.6 hello.py
```
python3.6: can't open file 'hello.py': [Errno 2] No such file or directory
```

I put a bash script in my python directory and then tried to run it from another directory not in the path.

It ran ok ?

---

### Post by &amp;KyT$0P# on 2022-10-09
[FONT=Courier New]$PATH[/FONT] is irrelevant to that usage.  You're explicitly telling Python3.6 to run the file named "hello.py" located in the current working directory.

If you want to run the Python script [FONT=Courier New]hello.py[/FONT] from any directory by placing it in [FONT=Courier New]$PATH[/FONT] -

1) Make it executable
```
chmod +x hello.py
```

2) Add a line like this as the very first line in [FONT=Courier New]hello.py[/FONT], so that the system knows what program to use to run it -
```
#!/usr/bin/env python3.6
```
(Here I assume you have a reason to use python3.6 specifically instead of just python3)

Now you just run [FONT=Courier New]hello.py[/FONT] directly, by itself, like you would any other program -
```
$ hello.py [COLOR="#FF0000"]<arguments to hello.py, if any...>[/COLOR]
```

---

### Post by TheFu on 2022-10-09
a) is the execute permissions set for the userid trying to run the script?
b) is the mount point for the directory mounted with the noexec option?
c) the first line of the file points to a valid interpreter and is followed by 1 empty line?  This is about the "she-bang" line.
d) the updated PATH must be exported ... only subshells inherit that updated setting, until either a logout/login cycle or full reboot.  systemd has broke a few things related to startup.  Check the PATH using 'echo $PATH'

BTW, it is smart to check the PATH doesn't already have the directory in it.   There is a length limit for the PATH. It is a kernel parameter - in the 1990s, it was 256 characters, but I think is was changed to be 4Kb long ago, so nobody really should run into it.

---

