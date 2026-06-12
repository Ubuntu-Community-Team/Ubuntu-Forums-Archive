---
title: "I'm new at this stuff. Keeps getting sudo error."
date: 2017-10-30
forum: General Help
---

### Post by jm999f on 2017-10-30
Everytime I try to install programs trough sudo-comands in the terminal, I get the same error

> jesper@jesper-AOD255:~$ sudo apt-get install anymeal
[sudo] password for jesper: 
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/mono-official.list
E: The list of sources could not be read.
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/mono-official.list
E: The list of sources could not be read.
jesper@jesper-AOD255:~$ 

How do I fix this?

---

### Post by deadflowr on 2017-10-30
Your mono-official source file is broken it seems.
Post what you see from
```
cat /etc/apt/sources.list.d/mono-official.list
```
(I hope I speeled that write)

I'm suspecting when you created that file, you did it wrong and added sudo to the entry.

---

### Post by jm999f on 2017-10-30
This is what I get :

> jesper@jesper-AOD255:~$ cat /etc/apt/sources.list.d/mono-official.list
sudo apt-get update


sudo apt-get install mono-devel
jesper@jesper-AOD255:~$ 


---

### Post by deadflowr on 2017-10-30
Yep, all wrong.
Best to delete that file and start over.
How did you first try adding that file?

---

