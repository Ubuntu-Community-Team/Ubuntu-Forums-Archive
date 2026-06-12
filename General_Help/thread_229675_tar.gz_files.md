---
title: "tar.gz files"
date: 2006-08-04
forum: General Help
---

### Post by Cure777 on 2006-08-04
How do you extract, then install tar.gz files? I'm having a lot of trouble installing these.

---

### Post by 23meg on 2006-08-04
[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

---

### Post by Cure777 on 2006-08-04
I downloaded the build-essential package, and the "make" command still doesn't work:

> george@george-laptop:~/Desktop/tilp2-0.13$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by Ramses de Norre on 2006-08-04
Did you do ```
./configure
``` first?
Check the output for errors! If this still doesn't work you should read the READ_ME and INSTALL files in the archive, they should contain all info about how to install the program.

---

### Post by Cure777 on 2006-08-08
Yes, I did ./configure, and no mat what I try or any tar.gz file, it tells me no target for make or something like that.

---

### Post by Dodzey on 2006-08-08
have you checked to make sure there is a makefile in the folder you extracted the tar.gz archive to?

---

### Post by Cure777 on 2006-08-08
Hmm. What do you do if there isn't a makefile?

---

### Post by Dodzey on 2006-08-08
well...therees not much you can do....are you positive you have extracted every file from the tar.gz? What software are you trying to compile?

---

### Post by Cure777 on 2006-08-08
Several things, but one without a makefile is StepMania 3.9, (binary from the site). But it came in a tar.gz file.

---

### Post by Dodzey on 2006-08-08
If its a binary it wont need compiling, just give the binary execute permissions and run it

---

### Post by Cure777 on 2006-08-08
Ok, I got stepmania to run by switching to the directory and typing

./stepmania

thanks for the help

---

### Post by Ramses de Norre on 2006-08-08
./configure is used to configure the makefile, so if you're able to run ./configure and it works you should also have a makefile.

Did you manage to get the other ones working?

---

