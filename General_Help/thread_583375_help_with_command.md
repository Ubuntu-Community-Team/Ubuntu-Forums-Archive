---
title: "help with command"
date: 2007-10-20
forum: General Help
---

### Post by gm__ on 2007-10-20
Could anybody help me to explain what that command means!? 
It was in a "make" file.

@echo -e "\ntype \"./sploit\" to see if it works :)"

./sploit will execute the program, but what is "ntype" and why the slashes?

Does it make any sense to anybody? 

Thanks for any help!

---

### Post by Old *ix Geek on 2007-10-20
> Could anybody help me to explain what that command means!?
It was in a "make" file.

@echo -e "\ntype \"./sploit\" to see if it works "
It's just an instruction to the user, being **echo**ed to (shown on) their screen.
> ./sploit will execute the program, but what is "ntype" and why the slashes?It's not **ntype**, it's **\n** followed by the word **type**. The **\n** represents a newline, so when this piece of code is run, there will be a blank line immediately before the instruction.  The other backslashes are there to escape the quotes (make them print) around *./sploit*.  The actual output would look like this:

**type "./sploit" to see if it works :)**

---

### Post by gm__ on 2007-10-22
Makes perfect sense! :)

Thanks a million Mister, very nice from you for explaining it all.

---

### Post by Old *ix Geek on 2007-10-22
> **gm__ said:**
> Makes perfect sense! :)

Thanks a million Mister, very nice from you for explaining it all.You're very welcome.  One correction, though: It's Ms. not Mr. :D

---

