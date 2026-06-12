---
title: "Chown with wildcard"
date: 2017-12-26
forum: General Help
---

### Post by raleigh3 on 2017-12-26
How would I use chown with wildcard with this ->12-26-2017-13-img ?

Files will have different names but will all end in -img.

I want andy to be owner.

---

### Post by #&amp;thj^% on 2017-12-26
From chown --help:

```
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.

[...]

  -R, --recursive        operate on files and directories recursively

[...]
```

So you need to run (with sudo):

```
chown -R USERNAME:GROUPNAME /PATH/TO/FILE
```

Or, if the group shall be the specified user's primary group (usually same name), **you can also omit the GROUPNAME and just give the USERNAME**: with a colon (no space before it!). It will be set implicitly:

```
chown -R USERNAME: /PATH/TO/FILE
```

To only change the user and leave the group as it is, just specify USERNAME and no group name and no colon:

```
chown -R USERNAME /PATH/TO/FILE
```

To only change the group and leave the owner user as it is, just specify :GROUPNAME with a leading colon:

```
chown -R :GROUPNAME /PATH/TO/FILE
```



**echo .* **is a good way of trying out the expansion. It'll show you exactly what the shell sees. ls .* can be a bit more confusing, as it'll go down directories (ls -d .* might be better, but might as well just use echo .*
This from man echo:
```
NAME
       echo - display a line of text

SYNOPSIS
       echo [SHORT-OPTION]... [STRING]...
       echo LONG-OPTION

DESCRIPTION
       Echo the STRING(s) to standard output.

       -n     do not output the trailing newline

       -e     enable interpretation of backslash escapes

       -E     disable interpretation of backslash escapes (default)

       --help display this help and exit

       --version
              output version information and exit

       If -e is in effect, the following sequences are recognized:

       \\     backslash

       \a     alert (BEL)

       \b     backspace

       \c     produce no further output

       \e     escape

       \f     form feed

       \n     new line

       \r     carriage return

       \t     horizontal tab

       \v     vertical tab

       \0NNN  byte with octal value NNN (1 to 3 digits)

       \xHH   byte with hexadecimal value HH (1 to 2 digits)

       NOTE: your shell may have its own version of echo, which usually super&#8208;
       sedes the version described here.  Please refer to your  shell's  docu&#8208;
       mentation for details about the options it supports.

```

---

### Post by steeldriver on 2017-12-26
A shell glob matching all non-hidden files in the current directory ending in -img would simply be

```

*-img

```

So

```

chown andy -- *-img

```

There's no need for recursion unless you need to change ownership of files in subdirectories. The above will leave the files' group untouched - if you want to change the group to match andy's login group as well you can use

```

chown andy:  -- *-img

```

---

### Post by #&amp;thj^% on 2017-12-26
[QUOTE=steeldriver;13724414

There's no need for recursion unless you need to change ownership of files in subdirectories.The above will leave the files' group untouched - if you want to change the group to match andy's login group as well you can use

```

chown andy:  -- *-img

```[/QUOTE]

Good point I should have mentioned that in my post.
Thanks steeldriver.;)

---

### Post by raleigh3 on 2017-12-26
Thanks guys.

---

