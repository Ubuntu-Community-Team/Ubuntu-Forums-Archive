---
title: "Permission denied/ command not found"
date: 2013-05-25
forum: General Help
---

### Post by plantton on 2013-05-25
Hey guys,
I get in this trouble for several times. 

When I try to install a newly downloaded software with command line, I get stuck with an information like "Permission denied" or "command not found". Even I use "sudo ./mduml", I cannot get over this problem. Would please help me to solve this problem?

---

### Post by socialismo on 2013-05-25
That file you are trying to run is allowed to be executed?

```
$ chmod +x [COLOR=#000000]mduml[/COLOR]
```

---

### Post by ibjsb4 on 2013-05-25
The command is

```
sudo apt-get install <name-of-package>
```

Is that what your using?

---

### Post by 3rdalbum on 2013-05-25
If you are new, stick to Ubuntu Software Center (or apt-get) until you have more experience.

When you try to run a program in the terminal and it gives "Permission Denied" you need to give the file execute permission.

To reduce "file not found" typing mistakes, try dragging the file into the terminal instead of typing its name or path.

---

### Post by HiImTye on 2013-05-25
it would help if you gave us the commands you're using, as we can only give vague answers to vague questions

---

### Post by plantton on 2013-05-27
later on, guys. Thanks for your explanation. I'll try to figure out what happened 2-3 days later....Still busy with my exams.

---

