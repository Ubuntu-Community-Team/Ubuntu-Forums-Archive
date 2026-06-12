---
title: "How do I install a .bin file?"
date: 2007-03-15
forum: General Help
---

### Post by jincast90 on 2007-03-15
Hello. I have downloaded the netbeans IDE. The install file is a .bin file and I don't know how to install a .bin file. Any help?

---

### Post by wieman01 on 2007-03-15
Command line:
> cd /your/folder
> sudo ./your_file.bin
They are executables.

---

### Post by jincast90 on 2007-03-15
> **wieman01 said:**
> Command line:


They are executables.

That won't do it. I went to my Desktop (That's where the file is located) and did a:

sudo ./netbeans-5_5-linux.bin 

The terminal just said: command not found

---

### Post by wieman01 on 2007-03-15
> **jincast90 said:**
> That won't do it. I went to my Desktop (That's where the file is located) and did a:

sudo ./netbeans-5_5-linux.bin 

The terminal just said: command not found
Oops, please try again with the "/."...
> sudo netbeans-5_5-linux.bin

---

### Post by jincast90 on 2007-03-15
> **wieman01 said:**
> Oops, please try again with the "/."...

I appriciate you tried to help. I found out the solution by myself. First I did a chmod 777, and then I did a sudo bash ./netbeans.. and now it is installing!

---

### Post by wieman01 on 2007-03-15
> **jincast90 said:**
> I appriciate you tried to help. I found out the solution by myself. First I did a chmod 777, and then I did a sudo bash ./netbeans.. and now it is installing!
Yeah... Have not thought of it. You need to make it executable first. Hard to give advice if you are sitting in front of a d@§"! Windows machine. ;-)

---

### Post by Jackfrost123 on 2008-05-25
Hi I ve been reading this thread due to an issue similar to the one I am having and I have the following queries.

why does putting a ./ in front of the command make all this much difference, and what is a ./, because without it I too got "command not found". Also I didn't do it with sudo, super user do, but it still worked, why?

And isnt it so, that linux does not have extentions to their filenames? Then how come .bin? And is .bin executable installer, or just executable???

Thanks!!!

---

### Post by robertchahine on 2008-05-25
> **Jackfrost123 said:**
> Hi I ve been reading this thread due to an issue similar to the one I am having and I have the following queries.

why does putting a ./ in front of the command make all this much difference, and what is a ./, because without it I too got "command not found". Also I didn't do it with sudo, super user do, but it still worked, why?

And isnt it so, that linux does not have extentions to their filenames? Then how come .bin? And is .bin executable installer, or just executable???

Thanks!!!

.bin are usually installer.
and don't forget that netbeans is made by SUN microsystem (that means java) which works well on all the platforms

---

### Post by lswest on 2008-05-25
> **Jackfrost123 said:**
> Hi I ve been reading this thread due to an issue similar to the one I am having and I have the following queries.

why does putting a ./ in front of the command make all this much difference, and what is a ./, because without it I too got "command not found". Also I didn't do it with sudo, super user do, but it still worked, why?

And isnt it so, that linux does not have extentions to their filenames? Then how come .bin? And is .bin executable installer, or just executable???

Thanks!!!

"./" means it is in the current directory, it may be that without it it's searched for in the $PATH (variable contains all the list of paths to exectuables, and their commands), and logically that excludes the directory you saved the .bin to, as it was not installed or downloaded by apt-get or synaptics (or even a root user).

---

### Post by Jackfrost123 on 2008-05-25
IsWest,

thanks buddy for the reply first off, That is kinda dumb though in terms of the operating system to not look in the current folder when I type a filename, or am I missing out something? Shouldn't it have been the current directory by default AND whatever is in the $path variable? It does make sense however the way you explained it.

Robert, I am still confused, what does usually installer mean? When isn't it installer? What do the other exec files have as ending in .something? Isn't linux supposed to NOT have .endings such as windows do?

---

### Post by lswest on 2008-05-25
haha, first off, my name is "lswest" (that's an L) and all lowercase, but no worries ;) About it not looking for the filename, it usually does for me, but sometimes there is the case where it simply does not, no idea why it doesn't.  Also, it depends on how the bin file is written, if it has a path to the default interpreter (e.g. what it's meant to be run with) it should work without having to add "bash" or anything beforehand, othertimes that line is missing, and you need to specify the interpreter with a command before it (such as "bash"), so that it knows how to run it.

---

### Post by Jackfrost123 on 2008-05-25
ok, great, ls, that clears things up. A bit.

Btw, just noticed your avatar, and and L it is indeed!!

---

### Post by lswest on 2008-06-14
> **Jackfrost123 said:**
> ok, great, ls, that clears things up. A bit.

Btw, just noticed your avatar, and and L it is indeed!!

haha that was my motivation for making the avatar ;) but thanks for noticing :)

---

