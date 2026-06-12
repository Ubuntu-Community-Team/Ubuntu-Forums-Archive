---
title: "Bash and \n"
date: 2014-04-11
forum: General Help
---

### Post by Ralph L on 2014-04-11
I am trying to learn bash scripting and am trying to understand how the system works.  Any help would be appreciated.

ralph@Lat1:~$ echo -n '\n' |xxd
0000000: 5c6e                                     \n
The value 5c6e is what I expected.

ralph@Lat1:~$ ABC='\n'
ralph@Lat1:~$ echo -n $ABC |xxd
0000000: 20                                        
I did not expect the value of 20.  That is hex for a blank, not for \n.  Can anybody explain this?

I want to be able to set some thing to "newline".  I thought I could use \n, but this is what happened.
ralph@Lat1:~$ echo -n \n |xxd
0000000: 6e                                       n
Only the "n" was set, not "0a", which is the hex for newline.  Can anybody explain how to set something to newline?

ralph@Lat1:~$ ABC=\n
ralph@Lat1:~$ echo -n $ABC |xxd
Apparently ABC is now set to nothing.  How does that happen?

ralph@Lat1:~$

---

### Post by steeldriver on 2014-04-11
It should work if you either quote or double-escape the \n e.g.

```

$ ABC=**'\n'**
$ echo -n $ABC |xxd
0000000: 5c6e                                     \n
$ echo -en $ABC |xxd
0000000: 0a                                       .
$
$ ABC=**\\n**
$ echo -n $ABC |xxd
0000000: 5c6e                                     \n
$ echo -en $ABC |xxd
0000000: 0a                                       .

```

(note the use of echo **-e**n to interpret the \ as an escape character rather than a literal backslash). I can't explain why you got 0x20 however in general it's recommended to avoid all uppercase names for your variables - they are reserved for system variables which *may* cause unpredictable behavior (although I don't think that's what's happening here).

---

### Post by btindie on 2014-04-11
You need to use echo with the -e option to "enable interpretation of backslash escapes".

No idea why you got 0x20 - SPACE with
```
$ ABC='\n'
$ echo -n $ABC | xxd
0000000: 5c6e                                     \n
```
Might depend on what shell you're using.

Trying putting it in double quotes
```
$ ABC='\n'
$ echo -n "$ABC" | xxd
```

Or when you do the assignment of \n to the variable you can do it slightly different so the \n gets converted into 0x0A.
```
$ ABC=$'\n'
$ echo -n "$ABC" | xxd
0000000: 0a                                       .
```

---

### Post by Ralph L on 2014-04-12
Thank you for your responses.  They help a lot.  But another question.  Consider this example:

ralph@Lat1:~$ abc="\n"
ralph@Lat1:~$ echo -n $abc |xxd
0000000: 5c6e                                     \n

The bash manual I have states:
"Using double quotes the literal value of all characters enclosed is preserved, except for the dollar sign, the
backticks (backward single quotes, ``) and the backslash.
The dollar sign and the backticks retain their special meaning within the double quotes.
The backslash retains its meaning only when followed by dollar, backtick, double quote, backslash or
newline. Within double quotes, the backslashes are removed from the input stream when followed by one of
these characters. Backslashes preceding characters that don't have a special meaning are left unmodified for
processing by the shell interpreter."

Apparently "n" is not a special character following "\", so the "\n" is printed literally.  However, the manual states that "newline" is a special character.  How do I specify a "newline" following the "\".  "\n" would be the obvious way, but I don't know how to enter it in this case.
Any help appreciated.

---

### Post by Vaphell on 2014-04-12
you are learning largely useless things here.
given it's bash you can use printf and/or $'' strings and leave the legacy cruft behind.

never leave your variables unquoted, especially when they are filled with whitespace. Unquoted strings are mangled by word splitting, original whitespace is replaced with 1 space (or should i say first char in $IFS) or with nothing if it's on boundaries.

```
$ n=$'\na\na\n\n'
$ echo "$n" | od -c
0000000  \n   a  \n   a  \n  \n  \n
0000007
$ echo $n | od -c
0000000   a       a  \n
0000004
```

---

