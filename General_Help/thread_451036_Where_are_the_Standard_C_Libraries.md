---
title: "Where are the Standard C Libraries?"
date: 2007-05-21
forum: General Help
---

### Post by timdoc1 on 2007-05-21
I tried to gcc my program and they weren't recognized.
Can you tell me where they should reside and if they are not there, then how to get them?

(BTW I am new to Linux and just installed ubuntu today)

Thanks from all,
Tim:(

---

### Post by AndrewGene on 2007-05-21
I think all you need to do is in the terminal type "sudo apt-get install gcc*"
w/out the quotations
the asterik will do what's called "redex" and will install everything in your system from the repositories that starts with "gcc"

I'm new to linux as well but I hope that helps

---

### Post by challengerlks on 2007-05-22
If your gcc is already in your system, U can try to add "/usr/bin/" in your PATH variable which can be set in .bashrc of your home diretory

setting PATH variable:

add the following line in .bashrc file

export PATH ="/bin:$PATH"

then type the follwoing command in your terminal to make your changes effect

source .basrhc 

Then , you should use make your gcc program working

And,

the Standard C Libraries were located at "/usr/include"

Hope it can help U ;)

---

### Post by WW on 2007-05-22
Be sure that you have installed the standard libraries and headers; they are not included by default.  You can install the C and C++ compilers and libraries by installing the package **build-essential**.  You can use Synaptic, or give the command
```

sudo apt-get install build-essential

```

EDIT: timdoc1, I just made a comment about build-essential in your other thread.  Sorry for repeating myself--I just now noticed that both threads were yours.

---

