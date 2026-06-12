---
title: "Adding -lpthread to Complex Makefile"
date: 2012-12-04
forum: General Help
---

### Post by darkprince117 on 2012-12-04
First off, my environment is Ubuntu 12.10 and I've installed all the base packages for C++ programming.
I am working on a project that requires a makefile to compile a lot of.cc and .h files in a certain order. It apparently works fine in Cygwin, but when I try compiling it in Ubuntu, it gives me this error:

```
g++ -g -o server server.cc connection.o encoding.o feedback.o negotiate.o scheduler.o socket.o unicast.o utility.o
utility.o: In function `Thread::start()':
/home/aaditya/meng/code/utility.cc:184: undefined reference to `pthread_create'
utility.o: In function `Thread::join()':
/home/aaditya/meng/code/utility.cc:208: undefined reference to `pthread_join'
collect2: error: ld returned 1 exit status
make: *** [server] Error 1
```

I have looked up a lot of threads about this error and they all point to adding a -pthread option to the linker, and I've tried adding -pthread everywhere I could think on the makefile, to no avail. Here is the makefile:

```
SHELL:=/bin/bash
CC:=g++ -g

OBJFILES:=$(patsubst %.cc, %.o, $(filter-out server.cc client.cc ClientSchedulerListener.cc, $(wildcard *.cc)))

.PHONY: all clean force zip

all:	server client ClientSchedulerListener

force:	clean all

# Default rule for making an object file.  For example, utility.o is made this way.
%.o:	%.cc %.hh
	$(CC) -c -o $@ $*.cc

socket.o:	socket.cc socket.hh utility.hh
	$(CC) -c -o $@ $*.cc

negotiate.o:	negotiate.hh negotiate.cc socket.hh connection.hh encoding.hh
	$(CC) -c -o $@ $*.cc

encoding.o:	encoding.hh encoding.cc socket.hh connection.hh
	$(CC) -c -o $@ $*.cc

connection.o:	connection.hh connection.cc socket.hh
	$(CC) -c -o $@ $*.cc

server:	server.cc	$(OBJFILES)
	$(CC) -o $@ $^

client:	client.cc	$(OBJFILES)
	$(CC) -o $@ $^

ClientSchedulerListener: ClientSchedulerListener.cc 	$(OBJFILES)
	$(CC) -o $@ $^
	
zip:	multicast.zip

%.zip:	$(wildcard *.cc) $(wildcard *.hh) makefile runclients wed7.mp4
	zip $@ $^

clean:	;
	-rm client server ClientSchedulerListener *.o

```

I also tried changing the CC variable to ```
g++ -g -pthread
``` also to no avail.

I've also tried to ensure that the libpthread library is installed, and it is installed. I found it in my /lib directory of my Linux system.

Thank you for your help!

---

### Post by darkprince117 on 2012-12-04
I solved it.

I just changed the variable ```
CC:= g++ -g -pthread
``` It seems to work now, for some reason.

---

### Post by rnerwein on 2012-12-04
> **darkprince117 said:**
> I solved it.

I just changed the variable ```
CC:= g++ -g -pthread
``` It seems to work now, for some reason.
i think it's more transparent using on the beginning of the makefile:
CC = g++
MY_LIBS = -lbla -lblu .......
CFLAGS = -xy -yx ...

and so on for varibles.

your_target: $(MY_OBJ) $(MY_INCLUDE) my_prog.c
 $(CC) -o $@ $(CFLAGS)  $@.c $(MY_OBJ) $(MY_LIBS)

---

### Post by kjohri on 2012-12-06
Put the libraries where you are linking the object files.

```
server:	server.cc	$(OBJFILES)
	$(CC) -o $@ $^ -lpthreads

client:	client.cc	$(OBJFILES)
	$(CC) -o $@ $^  -lpthreads
```

---

