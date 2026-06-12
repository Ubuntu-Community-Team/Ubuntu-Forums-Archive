---
title: "Bash Profile"
date: 2008-05-16
forum: General Help
---

### Post by frito on 2008-05-16
downloaded a program called dcm2nii and you're supposed to be able to run it on the command line.
But apparently you need to change your .bash_profile to allow it to run

Anyone have any idea what to do?

---

### Post by pointone on 2008-05-16
They're asking you to edit "~/.profile" or "~/.bashrc".

Please post a link to the guide/instructions you're trying to follow. Your description is very vague.

---

### Post by kellemes on 2008-05-16
> **frito said:**
> downloaded a program called dcm2nii and you're supposed to be able to run it on the command line.
But apparently you need to change your .bash_profile to allow it to run

Anyone have any idea what to do?

The [instructions]("http://www.sph.sc.edu/comd/rorden/mricron/dcm2nii.html") don't speak of .bash_profile, or at least I don't see it.
You can't run it?

---

### Post by frito on 2008-05-16
those instructions dont talk about running it through console, it only uses the drag and drop / GUI (still a good find though)

the issue is all i know is that by modifying the bashprofile i can use it. 

I'll be happy with anything I can get. I barely know what a bash profile is :P

---

### Post by Ayuthia on 2008-05-16
I think I understand what you are saying.  Normally if you want to run a program from your home directory you have to be in your home directory and do:
```
./<application>
```
If you are not in your home directory, you have to type:
```
/home/<user>/<application>
```
or
```
~/<application>
```
or
```
$HOME/<application>
```

From what I understood from the instructions, the application is installed in your home directory.  If you want to just be able to just type <application> instead of entering the full path of the file, you have to modify your .bashrc so that your home directory is included.  To do this, you have to add this to .bashrc:
```
PATH=$PATH:/home/<user>;export PATH
```

You have to be careful when you do this though.  Any commands that you try to execute will always search through your home directory if it is not found in the other directories in $PATH.

In case you have not figured this out, <application> should be replaced with the application name that you want to run and <user> is to be replaced with your username.

This is a little long winded, but hopefully it makes sense.

---

