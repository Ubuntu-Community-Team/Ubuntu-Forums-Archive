---
title: "Fail to compile leveldb on Ubuntu 12.04 using c++"
date: 2013-03-17
forum: General Help
---

### Post by sveinn on 2013-03-17
Hello, 

I wish to try out leveldb on Ubuntu 12.04, 64bit. Found this example here

[http://www.pedrotanaka.com/1/post/2012/07/1-getting-started-with-leveldb.html](http://www.pedrotanaka.com/1/post/2012/07/1-getting-started-with-leveldb.html)

but compiling gives me error "undefined reference" to leveldb methods:

g++ -Wall  -I ./leveldb/include/ -pthread  ./leveldb/libleveldb.a test.cpp -o test
/tmp/ccYETi7C.o: In function `main':
test.cpp:(.text+0x1b): undefined reference to `leveldb::Options::Options()'
test.cpp:(.text+0x67): undefined reference to `leveldb::DB::Open(leveldb::Options const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, leveldb::DB**)'
collect2: ld returned 1 exit status

To anyone who has deployed leveldb on Ubuntu, are there any generic compile instructions out there? 

Thanks! 

Sveinn

---

### Post by TheFu on 2013-03-17
What is your level of expertise with C++?  
Do you have the dependent libraries loaded and included in the Makefile?  
Did you build the library before trying to build the test program?

Does **nm** show those methods inside the ./leveldb/libleveldb.a file?

---

### Post by sveinn on 2013-03-17
The Fu, 

I've only used C++ for about a year, but C much longer. I'll follow your suggestions post back once I have a working solution to this test.cpp. 

thanks, 

Sveinn

---

### Post by TheFu on 2013-03-17
Ok, so build the library, then try to build the test app.
**nm** will look inside the library for all functions/classes/methods, so you can KNOW what you need is there.
Lastly, did you install the std:: template libraries on your machine? Seems they are using those - like good C++ people should.

---

### Post by steeldriver on 2013-03-17
is it possibly just a link order issue? have you tried swapping the order of the library and the top level cpp file? i.e.

```
g++ -Wall  -I ./leveldb/include/ -pthread  **test.cpp ./leveldb/libleveldb.a** -o test
```

---

### Post by sveinn on 2013-03-18
Steeldriver, 

If I use

g++ -Wall  -I ./leveldb/include/ -pthread  test.cpp ./leveldb/libleveldb.a -o test

I get 382 lines of errors starting with 

/usr/bin/ld: i386 architecture of input file `./leveldb/libleveldb.a(db_impl.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `./leveldb/libleveldb.a(db_iter.o)' is incompatible with i386:x86-64 output

Wonder if that's where the error lies, libleveldb.a is compiled for 32bit not 64bit. 

Sveinn

---

