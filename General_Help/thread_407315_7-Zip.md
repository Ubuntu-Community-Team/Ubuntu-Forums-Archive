---
title: "7-Zip"
date: 2007-04-12
forum: General Help
---

### Post by Madmoose on 2007-04-12
Hello, 

I have a large file that I need to open in the 7-Zip format. I didn't even know about this format until I got the file, does anyone know how to open it in Ubuntu?

Thanks, 

Moose

---

### Post by FuturePilot on 2007-04-12
```
sudo apt-get install p7zip p7zip-full
```
That should do it:) Then you can right click on it and use the Extract Here option or open it with Archive Manager and extract individual files.

---

### Post by Madmoose on 2007-04-12
Sweet. 

Thanks you. 

Moose.

---

### Post by kruppe on 2007-04-18
Thanks alot.

---

### Post by pligganease on 2007-09-17
Hi guys...

I supposedly downloaded and installed 7-Zip on my xubuntu system.  It shows up in my list of installed programs, but I can't find it anywhere and can't seem to use it.  I have hit Alt-F2 and tried that, but nothing.  What's the deal?  Am I missing something?  Any help would be greatly appreciated.

---

### Post by misfitpierce on 2007-09-17
Note: Can check in Add/Remove programs for useful programs that are pre-laid out for you. Just useful :)

7 zip and more found in there

---

### Post by hessiess on 2007-09-17
> **pligganease said:**
> Hi guys...

I supposedly downloaded and installed 7-Zip on my xubuntu system.  It shows up in my list of installed programs, but I can't find it anywhere and can't seem to use it.  I have hit Alt-F2 and tried that, but nothing.  What's the deal?  Am I missing something?  Any help would be greatly appreciated.

its a command line aplication, with it installed arcive manager will work with 7 zip format:)

---

### Post by pligganease on 2007-09-17
If only it were that simple.  Maybe it is, and I'm too "Microsoffed" to do it...  I get this error:

> Failed to execute child process "rar" (No such file or directory)

when I try to extract RAR files.  I have 7-Zip installed, which is supposed to extract RAR files.  I don't know what to do...  I've been having to put the files on a portable hard drive and stick them on my Vista notebook.  I want to get rid of all Microsoft, but I just can't get everything to work right!:(

---

### Post by aJayRoo on 2007-09-17
For unpacking rar files you will need to install the package 'unrar-free' or 'unrar-nonfree'. I noticed that the package description for 'p7zip-full' says that it supports rar files however the manual page makes no mention of this, If you want full support for opening rar archives I suggest installing 'unrar-nonfree' using synaptic. You will then be able to open rar archives by right clicking on them and selecting extract here.

---

### Post by pligganease on 2007-09-19
> **aJayRoo said:**
> For unpacking rar files you will need to install the package 'unrar-free' or 'unrar-nonfree'. I noticed that the package description for 'p7zip-full' says that it supports rar files however the manual page makes no mention of this, If you want full support for opening rar archives I suggest installing 'unrar-nonfree' using synaptic. You will then be able to open rar archives by right clicking on them and selecting extract here.

That worked like a charm.  Thanks.  I'm new to Linux and still learning, so thanks everyone for the advice!:redface::redface::redface:

---

