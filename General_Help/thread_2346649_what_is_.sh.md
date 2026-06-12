---
title: "what is .sh ?"
date: 2016-12-17
forum: General Help
---

### Post by 1ritesh on 2016-12-17
Hello,
when i extract the software .tar it has .sh what isthis mean?

---

### Post by QIII on 2016-12-17
Hello!

It might do you and everyone else on the forums some good for you to start first by trying to answer your own questions with resources available to you rather than immediately asking here as soon as a question occurs to you.

For instance, googling for 

```
what is an .sh file
```

gave me [this]("http://stackoverflow.com/questions/13805295/whats-a-sh-file") as a first hit.

---

### Post by 1ritesh on 2016-12-20
please teach more about it what it do?

---

### Post by lucavassos on 2016-12-20
.sh is an ececutable unix file. To execute it, you can open a shell, go to the folder where the file is and write "./namefile.sh" . if you need to run it as a root, write "sudo ./namefile.sh " and use your password.

---

### Post by speartip on 2016-12-20
Tell us what the .sh file is that you are trying to run. That may help.

---

### Post by Impavidus on 2016-12-20
File name extensions don't have a lot of meaning in Linux so it can be anything, but there are certain conventions. A .sh file is usually a shell script. Specifically, it tends to be a shell script for the [Bourne shell]("https://en.wikipedia.org/wiki/Bourne_shell"), which should be present on all Unix-family systems as the program /bin/sh. Nowadays /bin/sh is usually a symbolic link to another shell, which has to be compatible with the original Bourne shell in the sense that any script written for the Bourne shell will run the same way in the more modern alternative. On Ubuntu, /bin/sh is a symbolic link to /bin/dash, whereas most people run /bin/bash in their terminal.

But all of that shouldn't really matter to you. You got a .tar archive with software somewhere, unpacked it and found a shell script in it. The idea is probably that you have to run the script to install the software. You may have to run it with root permissions, you may have to configure some things first or answer some questions. I can't tell you exactly. It depends on how your software was packaged. Maybe there is an INSTALL file or a README with further instructions.

Of course, only run the script if you trust it.

---

### Post by 1ritesh on 2016-12-20
what is the importance of .sh file?

---

### Post by nothingspecial on 2016-12-20
If you posted the contents of the file (in code tags), perhaps someone could help. It could be anything??

---

### Post by 1ritesh on 2016-12-21
i am new to ubuntu linux never seen .sh extension.

---

### Post by speartip on 2016-12-21
As mentioned in #6, .sh files are just script files, that can be created by the user to run certain programs, or sometimes or can be packaged like that by the creator of the program.
For example I use Areca to backup my documents. Downloaded it comes as a .tar.gz compressed file. After extracting & entering the folder there is a .sh file. A terminal has to be opened in the folder that contains the .sh file. Then to run the program I have to run "./areca.sh" in the terminal to run the program. They all usually run by preceding the name of the .sh file with "./"
But as has been mentioned make sure you trust the source of the file before running.

---

