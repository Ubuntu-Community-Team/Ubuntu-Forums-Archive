---
title: "Learning c++ need help with compiling and outputting"
date: 2008-05-22
forum: General Help
---

### Post by two00lbwaster on 2008-05-22
I'm looking to start learning C++, from a book of all things, but I need to know how to compile the code and then output it to see the result.

So let's take the following code:

```

#include <iostream>

int main()
{
   std::cout << "Hello World!\n";
   return 0;
}

```

Might also need to be:

```

#include <iostream>
int main();
int main()
{
   std::cout << "Hello World!\n";
   return 0;
}

```

Oh, my platform is 8.04 32bit edition

---

### Post by geirha on 2008-05-22
You'll need a compiler. Installing [build-essential](apt://build-essential) will install gcc for you.

Then, assuming your code above is stored in a file called hello.cpp, compile and link with:
```

g++ hello.cpp

```

and run with
```
./a.out
```

When you don't specify what the output-file should be called, it defaults to a.out. You might want to do this instead
```
g++ -o hello hello.cpp
./hello

```

And btw, it's "Hello, World!\n" ;P

---

### Post by jakeofspades on 2008-05-22
Yea - hope this isn't patronizing or anything - but you will need to change the terminal directory to the folder where you are saving your c++ source code first so you can just state the .cpp file name without its location address.

eg.
```
cd ~/My-C++/
```

Also when you run the c++ executables ie. a.out or helloworld.out etc. in the terminal: you can always quit the program with ctrl - c.

This might not be particularly important now - but if you accidentally but some infinite loop of "Hello, World!" in; you can ctr-c to halt (which saves forcing the terminal to quit and then starting everything back up again etc. etc.)

Also - what are you using to edit your c++? I suggest Anjuta as a nice, beginners editor because it throws you straight out into actually writing code instead of bogging you down into 'project management.'

To get a nice environment: open Anjuta and go to edit/preferences -> Plugins tab -> and mark "Terminal." The effect of this is pretty self explanatory. Then, to get syntax highlighting which makes programming about 1000x easier: go to view -> editors -> highlight mode -> cpp.

---

### Post by two00lbwaster on 2008-05-22
> **geirha said:**
> You'll need a compiler. Installing [build-essential](apt://build-essential) will install gcc for you.

Then, assuming your code above is stored in a file called hello.cpp, compile and link with:
```

g++ hello.cpp

```

and run with
```
./a.out
```

When you don't specify what the output-file should be called, it defaults to a.out. You might want to do this instead
```
g++ -o hello hello.cpp
./hello

```

And btw, it's "Hello, World!\n" ;P

Cool, I'll try that later.

And I just copied the code out of the book, which didn't have a comma in it ;-D

---

### Post by two00lbwaster on 2008-05-22
> **jakeofspades said:**
> Yea - hope this isn't patronizing or anything - but you will need to change the terminal directory to the folder where you are saving your c++ source code first so you can just state the .cpp file name without its location address.

eg.
```
cd ~/My-C++/
```

Also when you run the c++ executables ie. a.out or helloworld.out etc. in the terminal: you can always quit the program with ctrl - c.

This might not be particularly important now - but if you accidentally but some infinite loop of "Hello, World!" in; you can ctr-c to halt (which saves forcing the terminal to quit and then starting everything back up again etc. etc.)

Also - what are you using to edit your c++? I suggest Anjuta as a nice, beginners editor because it throws you straight out into actually writing code instead of bogging you down into 'project management.'

To get a nice environment: open Anjuta and go to edit/preferences -> Plugins tab -> and mark "Terminal." The effect of this is pretty self explanatory. Then, to get syntax highlighting which makes programming about 1000x easier: go to view -> editors -> highlight mode -> cpp.

Hi there, not patronising at all.  Just good advice, though I would have known to change the directory.  

I didn't know about the ctrl + c although I should have made the link between the ctrl + c command when I'm folding with general termination of a program running in a terminal.

I was planning on using Notepad++ as this is what I use for modifying my xhtml/css with and I know the program fairly well now and I'm fairly certain that it supports c++ too.

I think that I may look at Anjuta too though as it sounds interesting.

---

