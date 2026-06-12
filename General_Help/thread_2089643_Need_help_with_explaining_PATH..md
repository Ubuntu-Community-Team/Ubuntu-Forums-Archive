---
title: "Need help with explaining PATH."
date: 2012-11-29
forum: General Help
---

### Post by AsherSevyn on 2012-11-29
Linux $PATH question: (because google is not being helpful) Why is the order important in your path? I get it that the path makes commands find their directories so they can run regardless of where you are but of what importance is the order of those individual directories in your path?

For example here is my echo $PATH

/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/myusername/bin

What does the order matter?

---

### Post by Vaphell on 2012-11-29
i guess it affects the search order?
afaik if you have some_program in both /usr/local/bin and /bin, the one in /usr/local/bin will be executed

---

### Post by AsherSevyn on 2012-11-29
I suspect that may be true but is there anyone else in here that can confirm that? Is that the only importance for the order of your PATH?

---

### Post by wojox on 2012-11-29
> **Vaphell said:**
> i guess it affects the search order?
afaik if you have some_program in both /usr/local/bin and /bin, the one in /usr/local/bin will be executed

[QUOTE=AsherSevyn;12380353]I suspect that may be true but is there anyone else in here that can confirm that? Is that the only importance for the order of your PATH?

[/QUOTE]

I concur :P

---

### Post by AsherSevyn on 2012-11-29
So going off of Vaphell's statement "if you have some_program in both /usr/local/bin and /bin, the one in /usr/local/bin will be executed" Does that mean that if there is another version of that application in a separate directory and that is in your path also but after the the initial location the second program will not run? I would hope not!

---

### Post by Vaphell on 2012-11-29
well, you can test it
put some dummy scripts in dirs listed in PATH, with the same name but echoing different text. Call the name, see which one responds.

---

### Post by AsherSevyn on 2012-11-29
Good, idea. I will try that. Thanks guys!

---

### Post by JKyleOKC on 2012-11-29
> **AsherSevyn said:**
> So going off of Vaphell's statement "if you have some_program in both /usr/local/bin and /bin, the one in /usr/local/bin will be executed" Does that mean that if there is another version of that application in a separate directory and that is in your path also but after the the initial location the second program will not run? I would hope not!That is **exactly** what it means. The command interpreter looks first at the first directory listed in $PATH, and if it finds the program there, loads and executes it without looking any deeper. If not, it tries the next one listed. The process continues until it finds the command, and if it runs off the end of $PATH without finding the program, gives you the error message.

If you want to run the later version per your question, all you have to do is give the full path to that later version, and it will run without the command interpreter ever even looking at $PATH.

Unlike Windows, where the shell looks in the current working directory before looking in the path, Linux uses only $PATH. That's why you have to use the "./" prefix to run a file in a directory that's not listed in $PATH.

---

### Post by wojox on 2012-11-30
> **AsherSevyn said:**
> Does that mean that if there is another version of that application in a separate directory and that is in your path also but after the the initial location the second program will not run? I would hope not!

You can trigger the second application using the absolute path.

---

