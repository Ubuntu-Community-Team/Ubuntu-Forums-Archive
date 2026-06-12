---
title: "[SOLVED] Output to File: Why Doesn't this Work?"
date: 2007-08-11
forum: General Help
---

### Post by aaaantoine on 2007-08-11
I'm trying to run the following:
$ Xgl -help > output_file

But instead of doing what I'd think it would do, it prints the output to the terminal and creates output_file with 0 bytes.

Meanwhile...
$ echo "test" > test

Works.

Is there another way to do this?  The output text is too much for the terminal; I can't scroll up to read it all.

---

### Post by lloyd_b on 2007-08-11
One possibility: the "command > file" only redirects the "standard output" stream to the specified file.  But, there's also a "standard error" stream, which will also appear on the console.  So try this:
```
Xgl -help 1>output.file 2>error.file
```
which will still capture "standard out" to "output.file", but capture "standard error" to "error.file" as well.

Give the above command a try, and see if you've captured the info you want in "error.file".

Lloyd B.

---

### Post by aaaantoine on 2007-08-11
Ah, that worked.  I guess the app treats it as error output (even though the -help command is on the list...).

Thanks!

---

