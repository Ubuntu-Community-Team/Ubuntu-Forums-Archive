---
title: "Question(s) about using the tar command with options"
date: 2017-04-29
forum: General Help
---

### Post by John_Patrick_Mason on 2017-04-29
I'm trying to learn the command line with the help of William E. Shotts' *The Linux Command Line*. I have a directory called playground with a bunch of subdirectories and files in it. The book calls for creating an archive with the tar command. I'd like to know what the f option does in each of these cases. What happens if I omit it?

```

tar cf playground.tar playground

```

```

mkdir foo
cd foo
tar xf ../playground.tar

```

Also, I need to know what the first dash after cf does in the following command, what the --files-from option does, and what is the equals sign and dash after the option for:

```

find playground -name 'file-A' | tar cf - --files-from=- | gzip > playground.tgz

```

---

### Post by papibe on 2017-04-29
Hi John_Patrick_Mason.

f is for the name of the archive, or tar, file.

```

tar cf playground.tar playground

```
the playground directory will be archive in the file 'playground.tar'.

```

mkdir foo
cd foo
tar xf ../playground.tar

```
extract from the archive file 'playground.tar'

```

find playground -name 'file-A' | tar cf - --files-from=- | gzip > playground.tgz

```
--files-from=- means that the list of file names that will be archive comes from the standard **input**. In this example, from the output of the command 'find'.

when the archive file is a dash, '-', it means use the standard **output**, instead of an actual file. In the example, the archive will be pass to the next command in the pipe: gzip.

Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by John_Patrick_Mason on 2017-04-29
> 
--files-from=- means that the list of file names that will be archive  comes from the standard output. In this example, from the output of the  command 'find'.

when the archive file is a dash, '-', it means use the standard output,  instead of an actual file. In the example, the archive will be pass to  the next command in the pipe: gzip.

Hope it helps. Let us know if you have more questions.
Regards.


OK, so if I wanted to create an archive with a specific name, instead of typing:

```

find playground -name 'file-A' | tar cf - --files-from=- | gzip > playground.tgz
```

I could type:

```

find playground -name 'file-A' | tar cf playground.tar --files-from=-

```

which I could then compress using:

```

gzip playground.tar

```

which would give me:

```

playground.tar.gz

```

Is that correct?

---

### Post by papibe on 2017-04-29
That's correct.

However, there's a shortcut. Tar can gzip the archive for you using the option **'z'**:
```
find playground -name 'file-A' | tar c**z**f playground.tar.gz --files-from=-
```
Regards.

---

### Post by John_Patrick_Mason on 2017-04-29
> **papibe said:**
> That's correct.

However, there's a shortcut. Tar can gzip the archive for you using the option **'z'**:
```
find playground -name 'file-A' | tar c**z**f playground.tar.gz --files-from=-
```
Regards.

The book gives a similar example, but with the -T option.

```

find playground -name 'file-A' | tar czf playground.tgz -T -

```

What is the dash at the end supposed to mean? Is it just part of the weird syntax kinda like --files-from**=-**?

---

### Post by papibe on 2017-04-30
-T is the same as --files-from

so

-T - is the same as --files-from=-

:)

BTW, all this information is available on the man page:
```
man tar
```

---

