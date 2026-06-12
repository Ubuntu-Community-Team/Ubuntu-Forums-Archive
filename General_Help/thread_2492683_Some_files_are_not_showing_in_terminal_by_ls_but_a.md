---
title: "Some files are not showing in terminal by ls but are showing up in gui - solved"
date: 2023-11-20
forum: General Help
---

### Post by fysmat on 2023-11-20
Hello

I have pretty weird problem with files in terminal view. It appeared today, I have some files on disk that I can't browse using terminal, no matter what commands I use. 

And first: the files are not hidden files that use dot at the beginning of the filename. They are regular files ending like .py or .txt.

Any ideas what should I do? Cheked thus far:

- ls -la doesn't show them.
- thunar shows them.
- permissions are like any other file I can see by ls.
- drive is definitely mounted as the files are on the same drive as root filesystem.
- I can open the files via thunar, edit and save them.
- used different terminal emulator - problem persists
- disabled my .bashrc - problem persists
- sudo su -
  ls -lah path/to/directory
 doesn't show them.
- ls missing/file gives: ls: cannot access 'filename': No such file or directory
- sudo -i
ls -lah <path/to>
doesn't show them.

Using Xubuntu 22.04.

Is my drive failing or what is happening here? Am I missing some setting in terminal?

**Solution**: Better glasses and more careful working!

---

### Post by MAFoElffen on 2023-11-20
Do this
```

sudo su -
ls -lah <path_to>

```
As a security kind of thing, Ubuntu has changed the permissions of some files to 600, which would mean that you could only r/w it if you are root, but not be able to read, write, etc if not actually 'root'. That means not even by being in the 'sudo' group. This change was made recently.

---

### Post by fysmat on 2023-11-20
> **MAFoElffen said:**
> Do this
```

sudo su -
ls -lah <path_to>

```
As a security kind of thing, Ubuntu has changed the permissions of some files to 600, which would mean that you could only r/w it if you are root, but not be able to read, write, etc if not actually 'root'. That means not even by being in the 'sudo' group. This change was made recently.

Thank you for your answer. Unfortunately the problem still persists.

---

### Post by ajgreeny on 2023-11-20
I'm not on a Linux machine at the moment so can't check this in any way but if you use 
```
sudo -i
ls -lah <path/to>
```does that make any difference to what you are shown.

I know there is a difference between **sudo su- **and **sudo -i **but can't remember the precise difference.

---

### Post by fysmat on 2023-11-20
> **ajgreeny said:**
> I'm not on a Linux machine at the moment so can't check this in any way but if you use 
```
sudo -i
ls -lah <path/to>
```does that make any difference to what you are shown.

I know there is a difference between **sudo su- **and **sudo -i **but can't remember the precise difference.

Thank you for your reply. Unfortunately nothing changed and the problem persists.

---

### Post by fysmat on 2023-11-20
Okay. Problem solved with the most simple solution: I have - somehow at some point - done a copy of the file system to different location, and I was trying to look into different directory. Thank you all! I was worrying I couldn't trust command line tools, but that wasn't the case!

---

### Post by ajgreeny on 2023-11-20
Great news!
Please use the Thread Tools menu uptop to mark this as SOLVED.
It is a great help to other users searching the forum.

---

