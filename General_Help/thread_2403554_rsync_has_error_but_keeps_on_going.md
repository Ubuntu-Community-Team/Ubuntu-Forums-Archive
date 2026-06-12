---
title: "rsync has error but keeps on going"
date: 2018-10-13
forum: General Help
---

### Post by Skaperen on 2018-10-13
i tried to use what i thought should be valid, thinking the shell would expand ~ for me, but it didn't and rsync got a bad path.  rsync did output error messages but did not stop. it tried (and failed) to copy every file, reported the number of files another stats as if the files were copied and exited with a status of 23.  scripts properly checking the exit status would see that it failed.  the command i did looked like this:

```
rsync --stats -aW --temp-dir=~ source/. target
```

of course the error was mine.  but i remember this kind of thing working at other times with other stuff added on.  it work fine when standalone:

```
echo ~
```

it would be nice if bash or rsync could handle it and do the expansion.

it would be nice if rsync would abort if an error like this causes the write to fail.

---

### Post by TheFu on 2018-10-13
I don't know, but I think expansion of ~ requires leading whitespace, which fails where an '=' is required.  You can use $HOME instead.

Shouldn't be hard to check the whitespace requirement.  Ok ... I tested it and **I'm completely wrong!**  <rbg>.  No idea why it didn't work.  Have you tried quoting it?  The examples in the rsync manpage show using ~ with quotes.

---

