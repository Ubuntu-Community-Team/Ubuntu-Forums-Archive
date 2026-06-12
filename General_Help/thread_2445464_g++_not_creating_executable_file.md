---
title: "g++ not creating executable file"
date: 2020-06-14
forum: General Help
---

### Post by jmbrown2 on 2020-06-14
Hello, 

g++ has been working fine on my computer for a long time and now, suddenly, it won't make executable files.  It's possible there was an auto update at some point, but other than that, I haven't changed a thing. The compiler runs through the program and gives errors if there are any, but then it just...does nothing.  It acts like it's finished, but then there is no executable file.  I've tried uninstalling and reinstalling g++ but that didn't change anything.  Any ideas? 

Thanks! 

Jill

---

### Post by norobro on 2020-06-14
I have no idea without more information. What are you compiling? Are you using a makefile? Does the simple program below generate an executable?
```
$ cat main.cpp 
#include <iostream>

int main() {
    std::cout << "Hello Jill\n";
}

$ g++ main.cpp

$ ./a.out
Hello Jill
```

---

