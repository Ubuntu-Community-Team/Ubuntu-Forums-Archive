---
title: "installing gcc"
date: 2008-06-16
forum: General Help
---

### Post by Isomorphismus on 2008-06-16
hello,
I am absolutely new to ubuntu and I want to install the gnu c compiler gcc on my system.. 
i installed the package "gcc" and I do have the command "gcc" in my /usr/bin directory, but when I try to run a simple "hello world"- program, I get a lot of errors like 

/tmp/ccXmEWIO.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
hello.cpp:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'

and many more. it seems that the gcc does not find any libraries! what can I do about that, do I have to install another package or specify a path variable or... ??

thx for any help,
Iso

---

### Post by chewearn on 2008-06-16
Install build-essential will give you everything:
```
sudo apt-get install build-essential
```

.

---

### Post by Isomorphismus on 2008-06-17
it still does not work ...

I have already installed the build-essential, so running your command, it says that build-essential is already the latest version. but trying to run my helloworld-programm, I get all these errors I wrote about above.

---

### Post by chewearn on 2008-06-17
Can you post the exact text in the terminal?  Also, if you don't mind, your program source codes as well.

p.s. Use [code] tags to make you post more readable, thanks.

.

---

### Post by pedro_orange on 2008-06-17
Post your code and your gcc command to compile it.

---

