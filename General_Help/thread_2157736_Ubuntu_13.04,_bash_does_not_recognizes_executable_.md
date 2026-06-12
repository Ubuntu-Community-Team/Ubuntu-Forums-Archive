---
title: "Ubuntu 13.04, bash does not recognizes executable files"
date: 2013-06-26
forum: General Help
---

### Post by Dirich on 2013-06-26
Hello,
I just installed a 12.10 and updated it, then upgraded to 13.04.
I tried to install a certain program, which required me to run an executable file, thus I wrote:

```
./FILENAME -OPTION
```

problem is, bash says that there is no file or directory named ./NAMEFILE

I tried to simply write FILENAME, and tabbing does not recognize the file (it does not autocomplete the name), but it does if I type ./FILENAME. Also, ls shows that the file is in the directory (a bit useless check since the autocomplete does work on ./FILENAME).

What is wrong with my bash?

EDIT: for clarity, this is an issue I have with ALL executable files, even those I compiled myself from my self-written programs.

---

### Post by snowpine on 2013-06-26
What is the name of this mystery program?
Link to where you downloaded it??

---

### Post by Dirich on 2013-06-26
It is not THAT specific executable, bash does the same with ANY exectuable, even those of programs I have written and compiled myself.
Essentially the problem is not the file I am trying to execute: no exectuable files is found by my bash.

---

### Post by ajgreeny on 2013-06-26
Are you certain the files are really executable, ie have the executable permission set; what does **ls -l** say about the files?

Sorry to ask what may seem like a silly question if you are fully Linux able, but not everyone realises the permissions are needed, not simply naming as if executable, eg file.sh for a shell script.

---

### Post by efflandt on 2013-06-26
Besides the output of **ls -l**, the output if **id** (little i) would also be useful to tell if your user or group has execute permission for the file. And do you have x permission for every directory in the path (x directory permission is necessary to access or ls directoryes/files in the directory)? It seems like a permission problem somewhere (or typo) if bash filename completion does not work.

Also note that capitalization matters in Linux, so FILENAME, Filename, or filename would be separate files not recognized as each other. And any spaces in a filename or directory require either quotes around the string or escaping each space with a backslash (\ ), which bash filename completion does automatically if you only start typing the part before the space.

---

