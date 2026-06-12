---
title: "C compiler help"
date: 2008-05-01
forum: General Help
---

### Post by itix on 2008-05-01
I don't know how many times I've had this (but i'ts too many) and I'm sure now that it isn't me doing anything wrong.

I'm slightly scared of command line and I'm so worried that I'd mess anything up, so I've always installed pre-compiled things with GUI interfaces rather than using the terminal to compile them.

This time I wanted to install FUSE which didn't come with a pre-compiled package, so thanks to the detailed installing instructions, I was able to get to the point where the C compiler were supposed to compile everything and I get this:
```

itix@acer:~/Downloads/fuse-2.7.3$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

This is definitely not the first time I've fought with the C compiler. I myself program C++ and downloaded this wonderful graphical SDK called Irrlicht and tried to use it with eclipse CDT but it was the same thing there. Eclipse couldn't use the C compiler...

Help plx!

---

### Post by Virtual_Ron on 2008-05-01
do you have permissions to create files in that directory?

---

### Post by DrMega on 2008-05-01
I'm no expert, but have fumbled my way through various source compiles with some success, and have seen the kind of problems you describe.

What I tend to do is look in Synaptic for anything with a name similar to what the text output said it couldn't find, install it, then try the compile again.

Like I said, I'm no expert so maybe someone with more knowledge than me will give you a more decisive answer.

---

### Post by Fixman on 2008-05-01
Have you tried

```
 sudo aptitude install build-essential 
```

---

### Post by Virtual_Ron on 2008-05-01
his output reads:  **configure: error: C compiler cannot create executables**

sure looks like a permissions issue to me.

---

### Post by itix on 2008-05-01
> do you have permissions to create files in that directory?
In */home/itix/Downloads*??
Uuhhh, yeah!
I tried sudo ./configur as well but it just resulted in the the same thing.

> look in Synaptic for anything with a name similar to what the text output said it couldn't find

Yeah, that was my first thought as well but I can't find anything missing in the output text above...

---

### Post by itix on 2008-05-01
According to synaptic pkg mgr, build-essential is for building deb packages...
How will that help me?

---

### Post by Fixman on 2008-05-01
> **itix said:**
> According to synaptic pkg mgr, build-essential is for building deb packages...
How will that help me?

Yes, it also has some libraries that bundle with gcc.

---

### Post by howlingmadhowie on 2008-05-01
have a look at the permissions of $HOME/Downloads/fuse-2.7.3 and make sure it's set to at least 755. you'll have to install build-essential as well in any case.

---

### Post by itix on 2008-05-01
Gaaah!
I seriously hope this step isn't nessecary on my Eee. 31 MBs is a bit large just to install a package considering the tiny SSD it has. I can of course remove the software afterwards...

ok, done... lets see; YEAH!
Thanx, it worked. djmount need fuse for my meda server to work.
Thought I'd experiment with my not so sensitive laptop before actually installing it on the Eee.
Thanx once again. Lets just hope it solved my eclipse problems too.

EDIT: This is soooo utterly useless. Why can't you mark threads as solved anymore?

---

