---
title: "[SOLVED] How to install application from CDROM"
date: 2006-10-11
forum: General Help
---

### Post by fyz on 2006-10-11
Dear all,

I have an installation CD which contains the application. There is a file called "install" in CD, I think it is kind of excutable file (shell script) as in Windows. I am beginner of linux, not quite sure how to install the appliation. 

I open a Terminal, go to the cdrom directory, and type following (as written in the installation guide also contained in the CD):
install &

But the error message is:
install: missing file operant
Try 'install --help for more information

Then I tried this:
/cdrom/install &

The error message is:
bash: /cdrom/install: /bin/sh: bad interpreter: Permission denied

Anybody can help? What do I need to do to install that application? Thanks a lot!

---

### Post by yman on 2006-10-11
is seems you should type in the command line the following text:
install --help
and get help there.
question: what is the extension of the file? if it is install.bin then it is a binary, which is somewhat similar to the .exe files in windows. you can double-click it, but I don't recommend. you should open the terminal and navigate to the folder in which the 'install' files is and type ./install.bin and the installation should start. don't do it if it isn't a .bin file. I don't want to get you into trouble.
try this site for some help: [http://linuxcommand.org/](http://linuxcommand.org/). I don't know how good it is, because I just stumbled uppon it in the forums.

ow, I didn't notice you wrote the path for the cd rom.
in order to change the folder your viewing type:
cd <and here goes the folder path. if it has spaces then surround it with qoutation marks>

as far as I know, the command cd stands for "change directory"

so you should type:
cd /cdrom/

and to install (if its a .bin file):
./install.bin

---

### Post by fyz on 2006-10-11
Dear all,

(Sorry for repeating post. I hope more peope here.)

I have an installation CD which contains the application. There is a file called "install" in CD, I think it is kind of excutable file (shell script) as in Windows. I am beginner of linux, not quite sure how to install the appliation. 

I open a Terminal, go to the cdrom directory, and type following (as written in the installation guide also contained in the CD):
install &

But the error message is:
install: missing file operant
Try 'install --help for more information

Then I tried this:
/cdrom/install &

The error message is:
bash: /cdrom/install: /bin/sh: bad interpreter: Permission denied

Anybody can help? What do I need to do to install that application? Thanks a lot!

---

### Post by meng on 2006-10-11
Try
cd /media/cdrom
./install

and don't double post! You clearly realize you shouldn't do it, so why do you do it?

---

### Post by aysiu on 2006-10-11
What's the application? There may be an easier way to install it.

That said, if it's a shell script, you can try this: ```
cd /to/directory/where/installer/is
sudo ./installername
``` > **meng said:**
> 
and don't double post! You clearly realize you shouldn't do it, so why do you do it? I've merged the two threads. In the future, you can click the *report post* button to mark duplicate threads.

---

### Post by CapitalT on 2006-10-11
In linux, when you want to run a program in the current directory you use:
./program_name not program_name

Because when you try the second one it will call the program in your PATH

---

### Post by fyz on 2006-10-11
> **aysiu said:**
> What's the application? There may be an easier way to install it.

That said, if it's a shell script, you can try this: ```
cd /to/directory/where/installer/is
sudo ./installername
```  I've merged the two threads. In the future, you can click the *report post* button to mark duplicate threads.

Sorry for repeated post! Won't do it again.

And thanks for the help! I will try now.

---

### Post by aysiu on 2006-10-11
What's the application you're trying to install?

---

### Post by fyz on 2006-10-11
Unfortunatly, still not working.
I typed this in terminal (log in as root user and in the directory where install file is):

sudo ./install

But still got this error:
sudo: unable to execute ./install: Permission denied

As yman said, this install may not be excutable. It has not extension like .bin. I open it with gedit. it looks like a set of shell scrip commands. 

It is an image editing application.

---

### Post by aysiu on 2006-10-11
You don't log in as root and then use *sudo*. *sudo* itself temporarily gives you root privileges. I don't know why you would get permission denied, though. Maybe the file isn't set to be executable?

Can you try this? ```
sudo chmod +x install
sudo ./install
```

By the way, there are plenty of image editing applications that you can install more easily than the one off this CD-ROM. Have you already tried GIMP and Kolourpaint?

---

### Post by CapitalT on 2006-10-11
If the installer is a shell script (text file) then you could execute it without chmod'ing it:
```
sudo sh install
```

IIRC

---

### Post by aysiu on 2006-10-11
I didn't know that. Is there any reason is particular that shell scripts don't need to be executable to... execute?

---

### Post by ayoli on 2006-10-11
if you invoke the script with sh or bash (ie: sh myscript.sh) you don't need to have +x permission on it

---

### Post by aysiu on 2006-10-11
> **ayoli said:**
> if you invoke the script with sh or bash (ie: sh myscript.sh) you don't need to have +x permission on it
Thanks for explaining. I didn't know that.

---

### Post by ayoli on 2006-10-11
> **aysiu said:**
> Thanks for explaining. I didn't know that.

you're welcome :)

---

### Post by fyz on 2006-10-11
It works!!! The installer starts!!!
Thanks all of you!!! CapitalT, aysiu, meng and yman!

1. Need to change the permission of the install file as aysiu suggested.(It seems this is not necessary, after reading CapitalT's later post.)
2. Need to change the permission of the destination directory!
3. **Have to** start it in this way as CapitalT suggested:
sudo sh install
It doesn't like this: ./install

All these three need to be satisfied (at least I did all of them). As I said I am totally beginner for linux. After whole evening, with all your helps, eventully it installer starts.

Thanks!

---

### Post by yman on 2006-10-11
> **meng said:**
> Try
cd /media/cdrom
./install


so I shouldn't write the extention?

---

### Post by meng on 2006-10-11
> **yman said:**
> so I shouldn't write the extention?
My understanding is that
./install
should work _if_ the file itself begins with the line
#!/bin/bash
and is executable. But otherwise you need to
sh install

---

### Post by yman on 2006-10-13
I just remembered this usefull link: [How to install ANYTHING in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")

---

