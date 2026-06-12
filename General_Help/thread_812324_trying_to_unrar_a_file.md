---
title: "trying to unrar a file"
date: 2008-05-29
forum: General Help
---

### Post by Vigh on 2008-05-29
hi trying to unrar a file, following a guide to setting up rar, need to copy rar and unrar to the bin directory, when i go to copy the files, it says permession denied, how can I put the files into the bin directory, thanks Anthony

---

### Post by em3raldxiii on 2008-05-29
Use the sudo command for adding files to the /bin directory. :D

---

### Post by latna on 2008-05-29
Unrar is in the repos.

```
sudo apt-get unrar
```

---

### Post by Vigh on 2008-05-29
how do i use the sudo command to add files to the bin directory? I noob

---

### Post by tommytrying2linux on 2008-05-29
i think its

> sudo unrar e filename

---

### Post by latna on 2008-05-29
You can also install programs with synaptic. Open synaptic and search for a program called unrar. You can install it from there.

Here's the documentation for installing software in ubuntu: [https://help.ubuntu.com/8.04/add-applications/C/index.html]("https://help.ubuntu.com/8.04/add-applications/C/index.html")

Installing software is pretty easy but there are a few things you need to know first. There are several ways to do it too. Pick the one you like the best.

And for future reference, when you see something like this:

```
sudo apt-get install unrar
```

That means you need to open a program called terminal and type (or paste) the text into it.

HTH

---

### Post by Vigh on 2008-05-29
i need to add the files to the bin directory first don't i? how do i do that

---

### Post by latna on 2008-05-29
> **Vigh said:**
> i need to add the files to the bin directory first don't i? how do i do that

No you don't need to do that. Well, you can if you want, but there's an easier way. Just let the package manager take care of the details. See my other posts. Install unrar and then you can unrar files by clicking on them.

---

### Post by TVC15 on 2008-06-21
Hi all,


Why make things difficult if there is a simple solution integrated in the GUI?
By default, Ubuntu installs the Archive Manager (look in Applications -> Accessories.
The Archive Manager handles .rar files easily if you have unrar installed.

So first do sudo apt-get install unrar
Then you can use Archive manager in the GUI instead of having to use the command line.
The way I use it is to right-click on a .rar file and choose "Open with Archive manager".
As simple as that!

Have fun

---

