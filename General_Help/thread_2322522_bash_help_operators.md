---
title: "bash help operators"
date: 2016-04-28
forum: General Help
---

### Post by eugene25 on 2016-04-28
Hi,

I want to be able to see all the options of if for example via command line like this:
[TABLE="class: CALSTABLE"]
[TR]
[TH]Primary[/TH]
[TH]Meaning
[/TH]
[/TR]
[TR]
[TD][ -a FILE ][/TD]
[TD]True if FILE exists.
[/TD]
[/TR]
[TR]
[TD][ -b FILE ][/TD]
[TD]True if FILE exists and is a block-special file.
[/TD]
[/TR]
[TR]
[TD][ -c FILE ][/TD]
[TD]True if FILE exists and is a character-special file.
[/TD]
[/TR]
[TR]
[TD][ -d FILE ][/TD]
[TD]True if FILE exists and is a directory.
[/TD]
[/TR]
[TR]
[TD][ -e FILE ][/TD]
[TD]True if FILE exists.[/TD]
[/TR]
[/TABLE]

I could save it somewhere, but I was wondering if there is already a saved help page somewhere about it.
Sometimes I work on servers with no internet connection and it would be of great help if there is something.

Thank you
Eugene

---

### Post by nerdtron on 2016-04-28
Hi Eugene,

Welcome to the forums.

These are used by the "test" command which is in turn can be used by other commands like "if, then, else" statements. You can view the "help" page of test to see them on the command-line.  Most commands also have a "help" page on how to use them, so always keep in mind, if you need help, just use the help command :)

```
[root@goddard ~]# **help test**
test: test [expr]
    Evaluate conditional expression.

    Exits with a status of 0 (true) or 1 (false) depending on
    the evaluation of EXPR.  Expressions may be unary or binary.  Unary
    expressions are often used to examine the status of a file.  There
    are string operators and numeric comparison operators as well.

    The behavior of test depends on the number of arguments.  Read the
    bash manual page for the complete specification.

    File operators:

      -a FILE        True if file exists.
      -b FILE        True if file is block special.
      -c FILE        True if file is character special.
      -d FILE        True if file is a directory.
      -e FILE        True if file exists.
      -f FILE        True if file exists and is a regular file.
      -g FILE        True if file is set-group-id.
      -h FILE        True if file is a symbolic link.
      -L FILE        True if file is a symbolic link.
      -k FILE        True if file has its `sticky' bit set.
      -p FILE        True if file is a named pipe.
      -r FILE        True if file is readable by you.
      -s FILE        True if file exists and is not empty.
      -S FILE        True if file is a socket.
      -t FD          True if FD is opened on a terminal.
      -u FILE        True if the file is set-user-id.
      -w FILE        True if the file is writable by you.
      -x FILE        True if the file is executable by you.
      -O FILE        True if the file is effectively owned by you.
      -G FILE        True if the file is effectively owned by your group.
      -N FILE        True if the file has been modified since it was last read.

      FILE1 -nt FILE2  True if file1 is newer than file2 (according to
                       modification date).

      FILE1 -ot FILE2  True if file1 is older than file2.

      FILE1 -ef FILE2  True if file1 is a hard link to file2.

    String operators:

      -z STRING      True if string is empty.

      -n STRING
         STRING      True if string is not empty.

      STRING1 = STRING2
                     True if the strings are equal.
      STRING1 != STRING2
                     True if the strings are not equal.
      STRING1 < STRING2
                     True if STRING1 sorts before STRING2 lexicographically.
      STRING1 > STRING2
                     True if STRING1 sorts after STRING2 lexicographically.

    Other operators:

      -o OPTION      True if the shell option OPTION is enabled.
      -v VAR     True if the shell variable VAR is set
      ! EXPR         True if expr is false.
      EXPR1 -a EXPR2 True if both expr1 AND expr2 are true.
      EXPR1 -o EXPR2 True if either expr1 OR expr2 is true.

      arg1 OP arg2   Arithmetic tests.  OP is one of -eq, -ne,
                     -lt, -le, -gt, or -ge.

    Arithmetic binary operators return true if ARG1 is equal, not-equal,
    less-than, less-than-or-equal, greater-than, or greater-than-or-equal
    than ARG2.

    Exit Status:
    Returns success if EXPR evaluates to true; fails if EXPR evaluates to
    false or an invalid argument is given.

```

---

### Post by eugene25 on 2016-04-28
Thank you very much
Eugene

---

