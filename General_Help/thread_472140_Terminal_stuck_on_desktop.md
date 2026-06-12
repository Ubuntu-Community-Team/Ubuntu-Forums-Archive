---
title: "Terminal stuck on desktop"
date: 2007-06-12
forum: General Help
---

### Post by baseballer10p on 2007-06-12
I was trying to use the terminal to navigate to my music folder in Ubuntu, and I accidentally used cd to change to the desktop.  The terminal says:
nelson@nelson-desktop:~$ 

I just need to find a way to get it back to: 
nelson@nelson:~$

I've searched these forums and google to find a command to go backwards through directories, but I haven't been successful.  I've also tried logging off and logging on and restarting the computer, but nothing seems to work.  Can anyone help me with this problem?  Thanks.

---

### Post by tgoose on 2007-06-12
Are you sure it didn't say nelson-desktop before? That part should be the hostname, not the name of the directory. Mine says -laptop on the end by default, and I don't think changing directory should ever affect that.

If you type "ls" you can see what directory you are in by the files there, and "cd .." will go up a directory.

---

### Post by baseballer10p on 2007-06-12
Hmm.  I guess that it did say nelson-desktop before.  I thought I was having problems because I was trying to access the desktop but it kept saying that there was no such file or directory.  Thats why I thought I was already in the desktop.  Dumb mistake on my part.  Thanks.

---

### Post by RedSquirrel on 2007-06-12
The prompt will tell you where you are. In your prompt, the ~ means you are in your home directory, which for you would be /home/nelson. (~ is short for /home/nelson)

If you run the command 

```
pwd
```it will tell you where you are as well (pwd stands for "print working (i.e., _current_) directory").

I believe the deskop directory is named Desktop. Note that files and directories are case-sensitive, so desktop is not the same as Desktop. ;)

---

