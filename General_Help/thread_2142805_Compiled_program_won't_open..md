---
title: "Compiled program won't open."
date: 2013-05-06
forum: General Help
---

### Post by Bresser on 2013-05-06
This didn't fit quite under the specialized support category because It has to do with an executable not opening not a problem in writing or compiling the code.

So I made a program with Netbeans and then also tested it in CODE:BLOCKS. I took the executable for the default folder that the executable goes to after compiling. But when I tried to run the executable nothing happened.

---

### Post by Impavidus on 2013-05-06
Does that program run in a terminal or does it open a window of its own? How do you try to start it?

---

### Post by Bresser on 2013-05-06
I doubleclick it. and i think it runs in terminal.

---

### Post by RJARRRPCGP on 2013-05-06
It means "dependency hell" or a permission problem.

---

### Post by Bresser on 2013-05-06
ok how do I fix it then?

---

### Post by steeldriver on 2013-05-06
You could open a terminal, navigate to the directory where you put the executable, and try to invoke it directly by name from there - that will allow you to capture any error messages about missing libs or whatever

```

$ cd /path/to/yourexecutable
$ ./yourexecutable

```

---

