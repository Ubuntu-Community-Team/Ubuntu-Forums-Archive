---
title: "exec to local file then command not work any more?"
date: 2017-12-07
forum: General Help
---

### Post by photonxp on 2017-12-07
In ubuntu's default terminal, I tried the following command:

```

exec >./test
ls

```

Then no any command worked any more under the same tab. 
But if I switched to other tab of the same terminal, commands worked well. 

Does the same happen to you? What could be wrong? Explanations?

---

### Post by Impavidus on 2017-12-07
What doesn't work?

That command is supposed to redirect standard output of the current shell to the file ./test. There should be no more output in the terminal (but still error messages), but the terminal should still show a prompt and accept input.

---

### Post by vasa1 on 2017-12-07
What are you wanting to do? If you want to capture all the terminal output to a file, see *man script*.

---

### Post by photonxp on 2017-12-07
> **Impavidus said:**
> 
That command is supposed to redirect standard output of the current  shell to the file ./test. There should be no more output in the terminal  (but still error messages), but the terminal should still show a prompt  and accept input.

That is really weird. What's the point of accepting input if the input doesn't work at all? I mean, the input could neither be executed nor be redirected to the ./test file. Even a **Ctrl + C** couldn't bring back the function of other commands such as ls.

By the way, this doesn't look like that **exec** is waiting for any input, at least to me, and probably to others as well:
> $ exec > ./test
$ 
$ ls
$ 
$ ^C
$ ls
$ 


---

### Post by Impavidus on 2017-12-08
Have you checked the contents of the file ./test?

exec is a shell buildin. For its instructions, try```
help exec
```
In your command, the input still works normally. Standard output is redirected to a file. So you don't see any standard output in the terminal, but all commands still work and store output in your file ./test. Error messages, which are a different kind of output, should still show up in the terminal. If you can't redirect output to the file where you want it to, you'll get an error message.
```
$ exec >/foo
bash: /foo: Permission denied
$ exec >test.txt
$ ls /foo
ls: unable to access '/foo': No such file or directory
# Error messages are still printed in terminal
$ echo hello world
# No output
$ exit
# Shell closes

# Different shell
$ cat test.txt
hello world
# Output of echo command was redirected to file

```

---

