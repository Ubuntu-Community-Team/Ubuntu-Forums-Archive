---
title: "a Quick bit of perl help please"
date: 2008-05-24
forum: General Help
---

### Post by |{urse on 2008-05-24
Hi there, i was just wondering how one does switches in programs using the system() command in perl?

system(program -f) 

How do i escape that white-space before the -f switch?

---

### Post by HalPomeranz on 2008-05-24
Use quotes:

```
system("program -f")
```

---

### Post by |{urse on 2008-05-24
In particular im trying to do things with zenity listboxes

---

### Post by |{urse on 2008-05-24
ah! silly i didn't try that tyvm man.

---

### Post by |{urse on 2008-05-24
okay now what if i wanted to use that method but system($x) instead?

like

```

my $x = '';
print "enter command to run";
chomp ($x=<STDIN>);
system($x);
```

but at runtime i get this

> 
enter command to run: "program -f"
sh: program -f: not found

but if i remove quotes like this

> enter command to run: program -f

 it works fine? Anyone splain why this works quoteless in a variable and only quoted in the code?

---

### Post by jpkotta on 2008-05-24
When you add the quotes, they are added to the value of the variable $x.  $x is exactly what you type.  Now the way system() works is it sends it's arguement to the shell for execution.  The shell normally uses spaces to separate it's arguments, i.e. ```
ls -l
```
is 2 arguements, the first one "ls", the second "-l".  The first one is always a command to run.  So when you type
```
"ls -l"
```
it is *one arguement* and the shell tries to run the command with the name "ls -l" (with the space and -l).  If you made an executable file named "ls -l" and put it in the PATH, this would work, but obviously that is not what you want.

Short answer: don't type the quotes.

---

### Post by |{urse on 2008-05-25
also, and this is just an example:

```
system("xmessage -center "hello, `whoami`" -buttons "Hey There":0")
```

> Bareword found where operator expected at ./lol line 4, near ""xmessage -center "hello"
        (Missing operator before hello?)
String found where operator expected at ./lol line 4, near "`whoami`" -buttons ""
        (Missing operator before " -buttons "?)
Bareword found where operator expected at ./lol line 4, near "" -buttons "Hey"
        (Missing operator before Hey?)
syntax error at ./lol line 4, near ""xmessage -center "hello"
syntax error at ./lol line 28, near "exit
}"
Execution of ./lol aborted due to compilation errors.


now why on earth? lol

---

### Post by HalPomeranz on 2008-05-25
> **|{urse said:**
> 
```
system("xmessage -center "hello, `whoami`" -buttons "Hey There":0")
```


The nested quotes are screwing you up.  Perl parses the above string as:

"xmessage -center "
hello, `whoami`
" -buttons "
Hey There
":0"

This is, of course, non-sensical.  It would work if you did:

```
system('xmessage -center "hello, `whoami`" -buttons "Hey There":0')
```

But beware that if you tried to include a variable in that string the single quotes would prevent that variable from being interpolated.  In other words, this WOULD NOT work:

```
system('xmessage -center "$message" -buttons "$buttons"')
```

---

### Post by |{urse on 2008-05-25
thanks and thanks again. An immense help.

---

