---
title: "Tarantella Native Client"
date: 2008-05-23
forum: General Help
---

### Post by devilears on 2008-05-23
Has anyone had a problem with getting this client to run on Ubuntu 8.04? It (tnci3li.tar), installs just fine (as user or root), but when one tries to run it as a user or as root, this happens:

/opt/tarantella/bin/ttwebtop
Aborted

/home/devillj/bin/ttwebtop
Aborted

---

### Post by ramprax on 2008-05-23
I too am facing the same problem.
The same issue has been reported by some people here:
[http://forum.java.sun.com/thread.jspa?threadID=5292495&tstart=0](http://forum.java.sun.com/thread.jspa?threadID=5292495&tstart=0)

---

### Post by podex_at on 2008-05-28
Hi!

I've been using tarantella native client 4.20.983 since Ubuntu 7.04. I had a problem starting it, but I can't remember the exact error message. I got a workaround by setting the environment variable XKEYSYMDB first:

export XKEYSYMDB=/usr/share/X11/XKeysymDB 
ttwebtop

(file XKeysymDB is owned by package libx11-data)

Since upgrading to 8.04, tarantella is not working correctly any more. It is starting, but it gives the error messages:

System cannot set locale
X does not support locale
Cannot set input modifiers
Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default

And as a result I can only use US keyboard layout, to whom I am not familiar with. 

Any ideas?

grx,
Ch.

---

### Post by ramprax on 2008-05-30
When I run ttwebtop it just says 'Aborted' and quits. I have no clue as to what is happening. I am attaching the output of 'strace ttwebtop'. Hope this helps in identifying the problem.

---

### Post by ramprax on 2008-05-30
I have put the output of 'strace ttwebtop' & 'ltrace ttwebtop' here:
strace - [http://ramprax.googlepages.com/tttrace.txt](http://ramprax.googlepages.com/tttrace.txt)
ltrace - [http://ramprax.googlepages.com/ttltrace.txt](http://ramprax.googlepages.com/ttltrace.txt)

---

### Post by almos.dinnyes on 2008-06-07
Hi,

I've the same problem, but my web based tarantella access doesn't work either. If I know well it uses only the port 443, but the error message says:
[I]Error - TCC helper
Cannot connect the Tarantella Client Component on port 43 269[/I] 

The port Nr. is not always the same. From the same machine, it works from Windows, this is why I think it's not because of the router.

Do you have any ideas?

Thanks in advance,
Álmos

---

### Post by rwbtta on 2008-06-11
> **almos.dinnyes said:**
> Hi,

I've the same problem, but my web based tarantella access doesn't work either. If I know well it uses only the port 443, but the error message says:
[I]Error - TCC helper
Cannot connect the Tarantella Client Component on port 43 269[/I] 

The port Nr. is not always the same. From the same machine, it works from Windows, this is why I think it's not because of the router.

Do you have any ideas?

Thanks in advance,
Álmos

Using Compiz / "Advanced Desktop Effects" can cause this error.  Try disabling to be sure.

---

### Post by Ricardo Qualtieri on 2008-11-17
Hello, ho do you do?

Maybe it too late, but I found the solution the problem...

It is simples.

Reading the install code, I saw a small error: the variable BINARY_FILE in the code is write ttwebtop and the its Ttwebtop, the sed in a some moment at the source code of install not find the file.

change the variable BINARY_FILE on the install. Is not ttwebtop is Ttwebop.

sorry for my english.

---

### Post by almos.dinnyes on 2009-04-26
Sorry for the very late answer. :) 
It worked, and this bug still exists in 9.04 :(

I also have an other question: something changed and now the keyboard layout in tarantella is wrong. I have Hungarian kayboard, and it works find within the ubuntu envirnment, but not in tarantella. e.g. instead of ö I have é etc. 

Do you have any idea, why?

---

### Post by ahbart on 2010-02-08
> **almos.dinnyes said:**
> Sorry for the very late answer. :) 
It worked, and this bug still exists in 9.04 :(

I also have an other question: something changed and now the keyboard layout in tarantella is wrong. I have Hungarian kayboard, and it works find within the ubuntu envirnment, but not in tarantella. e.g. instead of ö I have é etc. 
Do you have any idea, why?

Hi, Sorry for opening this old post, but I do have Ubuntu 9.10 now and have almost exactly ;-) the same problem with the keyboard layout. The normal keyboard layout in Ubuntu is US-international without deadkeys, but in Sun Secure Global desktop/tarantella it is german (I think) The Z is switched with Y for example and the symbols are all on other keys).
Does anyone know what could be a solution for this problem?

---

