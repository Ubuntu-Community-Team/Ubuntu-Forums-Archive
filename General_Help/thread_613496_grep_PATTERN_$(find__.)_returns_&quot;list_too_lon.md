---
title: "grep PATTERN $(find * ./) returns &quot;list too long&quot;, 'grep PATTERN ($find * /) doesn't"
date: 2007-11-15
forum: General Help
---

### Post by mrpeenut24 on 2007-11-15
Whenever I use the command:

```
grep PATTERN $(find * ./)
```

I get the error "Argument list too long".  However, when I use the command

```
grep PATTERN $(find * /)
```

it returns no such error, and does it's search.  How is this possible?!?  I know it's a kernel error, but the return of the second command is EASILY much longer than the first...right?


I seem to remember this working less than a week or so ago, although it might have been on a different system.

---

### Post by cwaldbieser on 2007-11-15
> **mrpeenut24 said:**
> Whenever I use the command:

```
grep PATTERN $(find * ./)
```

I get the error "Argument list too long".  However, when I use the command

```
grep PATTERN $(find * /)
```

it returns no such error, and does it's search.  How is this possible?!?  I know it's a kernel error, but the return of the second command is EASILY much longer than the first...right?


I seem to remember this working less than a week or so ago, although it might have been on a different system.

It could depend on what directory you are in when you issue the command.  The shell is expanding the "*" into the files in the current directory.  If one command is run in a directory with many files, and the other command is run in a directory with few files, only the first might give you an error.

---

### Post by mrpeenut24 on 2007-11-15
The first directory has about 25 directories/files in its immediate directory.  The root directory has about 23.  I can't see that 'find' would have a problem with 25 files...  And since the second 'find' is searching the *root* directory, that would obviously *contain* the directory I'm trying (and failing) to search.

---

