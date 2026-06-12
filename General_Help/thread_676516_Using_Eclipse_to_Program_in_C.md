---
title: "Using Eclipse to Program in C"
date: 2008-01-23
forum: General Help
---

### Post by djrobthaman on 2008-01-23
Hi verybody.

I have so far installed the eclipse and eclipse-cdt packages via synaptic.  Am having hell actually running anything I'm trying to write in C though.  Any suggestions on what  should do?

Thanks a million

---

### Post by djrobthaman on 2008-01-23
By the way,  whenever I tell it to build the project I get the following ouput in the console
```

make -k all 
make: *** No rule to make target `all'.

```

---

### Post by djrobthaman on 2008-01-23
I just read [this post]("http://ubuntuforums.org/showthread.php?t=148626").  It looks like this guy may have had teh same problem and I notice them suggest that it could be because the program can't find the make file.  Now, I'm going to reveal my complete lack of knowledge here and just ask:

What is a make file?
Should I already have one?
If not, how do I make one?
And, if I have to make one, do I have to do so for each C project I create?

Also, is there a special method of making eclipse detect it?

Thanks again

---

### Post by LaRoza on 2008-01-23
> **djrobthaman said:**
> I just read [this post]("http://ubuntuforums.org/showthread.php?t=148626").  It looks like this guy may have had teh same problem and I notice them suggest that it could be because the program can't find the make file.  Now, I'm going to reveal my lack of knowledge here and just ask:

What is a make file?
Should I already have one?
If not, how do I make one?
And, if I have to make one, do I have to do so for each C project I create?

Also, is there a special method of making eclipse detect it?

Thanks again

A make files tells Make how to compile the code and what it needs. [http://en.wikipedia.org/wiki/Make_(software](http://en.wikipedia.org/wiki/Make_(software))

You don't always need one, I don't use them. (My C programs are usually small)

Search for "makefile tutorial"

You don't need them.

See my Programming in Ubuntu wiki for how to compile and run C programs. Link in my Learn to Program link.

---

### Post by djrobthaman on 2008-01-23
Tried just saving the following:

```

#include <stdio.h>
 
int main(int argc,char ** argv)
{
    printf("Hello world!\n");
    return 0;
}

```

and got the following output when I tried to do it the old command line way

```

douglas@douglas-desktop:~/workspace/Project$ gcc hw.c -o game
gcc: hw.c: No such file or directory
gcc: no input files
douglas@douglas-desktop:~/workspace/Project$ gcc game.c -o game
game.c:1:19: error: stdio.h: No such file or directory
game.c: In function ‘main’:
game.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
game.c:7:2: warning: no newline at end of file
douglas@douglas-desktop:~/workspace/Project$ gcc game.c -o game
game.c:1:19: error: stdio.h: No such file or directory
game.c: In function ‘main’:
game.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
game.c:7:2: warning: no newline at end of file
douglas@douglas-desktop:~/workspace/Project$ 

```

Did I not install the C libraries or something?

---

### Post by raul_ on 2008-01-23
Install the build-essential package. You should give a look @ Laroza's tutorials. It's good for beginners

---

### Post by djrobthaman on 2008-01-23
I guess I'm blind.  Missed that section.  Thanks Raul.  So, I can get the gcc to compile the program through command line, but do you know how I can fix the problem for eclipse (still trying to get the whole gui going)

---

### Post by raul_ on 2008-01-24
If it complains about the makefile, you have to create a makefile. You should have an option that doesn't use "make", like compile or build. I don't really use eclipse...

Since you're starting, I highly recommend not using a IDE (or gui, as you prefer). If you use Eclipse, you'll learn how to use eclipse, and not how to program :)

---

### Post by djrobthaman on 2008-01-24
Okay,  I'll try and figure out based on the links how to make the file.  Thanks for your help.

---

