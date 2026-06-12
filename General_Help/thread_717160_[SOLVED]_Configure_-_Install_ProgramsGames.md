---
title: "[SOLVED] Configure - Install Programs/Games"
date: 2008-03-06
forum: General Help
---

### Post by Rytron on 2008-03-06
Hi,
I follow the install.txt instructions file with programs-
I open the terminal and put in:
cd 'the folder of the file'
./configure
then I get this message:
bash: ./configure: No such file or directory

Anyone know why?

---

### Post by taurus on 2008-03-06
Were you in the source directory when you ran that command?  What's the output of this command from a terminal?

```
ls -la 
```

---

### Post by soldats on 2008-03-06
is the file there, or is it a make file ie "make install" or maybe "make && ./configure". i think you need to sudo it as well. id suggest looking for a README.

---

### Post by taurus on 2008-03-06
> **soldats said:**
> is the file there, or is it a make file ie "make install" or maybe "make && ./configure". i think you need to sudo it as well. id suggest looking for a README.

It's always ./configure before make.  I've never seen make first and then ./configure after.

---

### Post by soldats on 2008-03-06
> **taurus said:**
> It's always ./configure before make.  I've never seen make first and then ./configure after.

ahh my bad, i havnet compiled something in a long while. ill make a note of that.

---

### Post by Rytron on 2008-03-06
I follow the read me files and the install.txt files but end up with errors.

How do I know if I am in the source directory?

I use ```
./configure
```

usually it does not work.
when it does work...
I use the make
I get this:
```
make: *** No targets specified and no makefile found.  Stop.
```

I also tried sudo make - same result.

---

### Post by trippinnik on 2008-03-06
I'd have to say you might be in the wrong directory.  Check the output of ```
ls
```

---

### Post by Rytron on 2008-03-07
Thanks for the help everyone.

I have since come across the program in question in the Synaptic manager.

There does seem to be a lot of trouble in installing non .deb files.

The add/remove and Synaptic features are so much easier to use.

Cheers.

---

